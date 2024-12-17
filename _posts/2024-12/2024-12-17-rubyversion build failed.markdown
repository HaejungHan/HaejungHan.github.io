---
title: TIL(20241217) [(github blog) About rubyversion - build failed 해결!]
author: hanni
date: 2024-12-17 14:50:00 +0800
categories: TIL
tags: [chrispy, github, ruby-version]
---

----------------------------------------------------------------------------

![image](https://github.com/user-attachments/assets/d3b9c6e0-13b2-4c38-ba08-8d33e0131a66)

GitHub Actions에서 사용 중인 실행 환경(런너)에 관련된 문제인데, 기본적으로 GitHub에서 제공하는 ubuntu-latest는 이제 ubuntu-24.04로 변경될 예정이고, 이로 인해 Ruby를 설치하는 방법에 대한 경고와 오류가 발생한 것으로 보였다. 

.github/jekyll.yml파일에 수정필요!

![image](https://github.com/user-attachments/assets/348a7993-3e13-4df2-b72d-1a2a19824975)

위와 같이 일부를 수정했고 아래는 jekyll.yml 파일의 설정이다. 

```
name: Deploy Jekyll site to Pages

on:
  # Runs on pushes targeting the default branch
  push:
    branches: ["main"]

  # Allows you to run this workflow manually from the Actions tab
  workflow_dispatch:

# Sets permissions of the GITHUB_TOKEN to allow deployment to GitHub Pages
permissions:
  contents: read
  pages: write
  id-token: write

# Allow only one concurrent deployment, skipping runs queued between the run in-progress and latest queued.
# However, do NOT cancel in-progress runs as we want to allow these production deployments to complete.
concurrency:
  group: "pages"
  cancel-in-progress: false

jobs:
  # Build job
  build:
    runs-on: ubuntu-24.04
    steps:
      - name: Checkout
        uses: actions/checkout@v4
      - name: Setup Ruby
        uses: ruby/setup-ruby@v1 # v1.161.0
        with:
          ruby-version: '3.1' # Not needed with a .ruby-version file
          bundler-cache: true # runs 'bundle install' and caches installed gems automatically
          cache-version: 0 # Increment this number if you need to re-download cached gems
      - name: Setup Pages
        id: pages
        uses: actions/configure-pages@v5
      
      - name: Install dependencies
        run: |
          gem install bundler
          bundle install

      - name: Build with Jekyll
        # Outputs to the './_site' directory by default
        run: bundle exec jekyll build --baseurl "${{ steps.pages.outputs.base_path }}"
        env:
          JEKYLL_ENV: production
      - name: Upload artifact
        # Automatically uploads an artifact from the './_site' directory by default
        uses: actions/upload-pages-artifact@v3

  # Deployment job
  deploy:
    environment:
      name: github-pages
      url: ${{ steps.deployment.outputs.page_url }}
    runs-on: ubuntu-latest
    needs: build
    steps:
      - name: Deploy to GitHub Pages
        id: deployment
        uses: actions/deploy-pages@v4
```