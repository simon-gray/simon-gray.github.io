---
layout: post
title: "Github Actions"
date: 2025-10-31
name: "Simon Gray"
tags:
- learning
---

# TLDR: Auto Blog Sync
This is a guide on how to setup an automatic blog sync using github actions between two repositories, one is the Obsidian repo and the other is the github.io, this is so there is separation between the two.

# Setting up an auto blog sync

## Creating a Personal Access Token (PAT)
In your GitHub account:
- Go to Settings → Developer settings → Personal access tokens → Fine-grained tokens (It requires the 'Contents' permission which will automatically provide the metadata)
- Generate a token with repo access for both repos
- Copy the token

## Add the secret
In Repo A, go to Settings → Secrets → Actions and add:
```
Name: SYNC_TOKEN
Value: <your token>
```

## The Action

```
name: Sync to Blog

on:
  push:
    paths:
      - '<SOURCE REPO NAME>/<SOURCE BLOG PATH>/**'
  workflow_dispatch:

jobs:
  sync:
    runs-on: ubuntu-latest

    steps:
      - name: Checkout source repo
        uses: actions/checkout@v4
        with:
          fetch-depth: 0

      - name: Clone destination repo
        run: |
          git clone <TARGET REPO> target-repo
          cd target-repo
          git config user.name "github-actions[bot]"
          git config user.email "github-actions[bot]@users.noreply.github.com"

      - name: Copy updated blog posts
        run: |
          mkdir -p target-repo/_posts
          if [ -d "<SOURCE BLOG PATH>" ]; then
            rsync -av --delete <SOURCE BLOG PATH> target-repo/<TARGET BLOG PLATH>
          else
            echo "⚠️ Source directory <SOURCE BLOG PATH> not found!"
          fi

      - name: Commit and push changes
        run: |
          cd target-repo
          git add .
          if git diff-index --quiet HEAD; then
            echo "✅ No changes to commit."
          else
            HASH=$(git --git-dir=../.git rev-parse --short HEAD)
            DATE=$(date +'%y-%m-%d')
            git commit -m "Auto-sync from <SOURCE REPO NAME>: ${HASH} (${DATE})"
            git push https://<ACCOUNT>:${{ secrets.SYNC_TOKEN }}@<TARGET REPO> main
          fi
```
It is worth noting that this is also AI generated
