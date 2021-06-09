---
title: Jekyll website
author: Diego Borghgraef
date: 2021-06-09 10:40:00 +0800
categories: [Blogging]
tags: [blog]     # TAG names should always be lowercase
---


## Jekyll Website

Today I decided to launch my first blogging website. I have been struggling the past year to keep my notes and writeups on a single place and the best way for me was to create a central place with all my notes was to use Jekyll website.
Jekyll gives a well organised website with alot of possibilities! To start with my blogging lifestyle i decided to do a small write on how I went on installing Jekyll Chirpy.


## Jekyll & Chirpy Installation

### What is Jekyll?
![image](https://user-images.githubusercontent.com/46396750/121324500-15a9ab00-c911-11eb-9fae-2d8fdc08a9b3.png)

Jekyll is a framework used to generate static sites. It allows you to focuus on the content & not too much on the aesthetics and organization of the site itself. Jekyll also provides great security features which makes it interesting to use.

### Installation
The first step for installing the Jekyll-Chirpy theme was to `fork` the Github repo from [cotes2020](https://github.com/cotes2020/jekyll-theme-chirpy). Then you need to clone it to your local repo using Git Bash.
When everything is ready you can start configuration your website. First you will need to oconfigure the  `_config.yml` file. This contains basic information about your website. Now if you want to work locally on building your website you can use 

```
$ bundle exec jekyll s
```

If everything is configured at your as you like, we can start the deployment of our website to Github.
![jekyll-theme-chirpy](https://user-images.githubusercontent.com/46396750/121323730-5d7c0280-c910-11eb-9c0d-c1fdb1a14b66.png)

### Deployment
During this part of the installation I had the most problems, as Github Pages changed quite alot from the online guides. But I managed to make it work.
In fact Github pages builds runs on 'Safe' mode, which restricts us from using plugins to generation additional pages files. There for we need to use `Github Actions` to build the site, store the vuilt site files on a new branch and use this new branch as the source of the GH Pages.

#### How?
Ensure the file `.github/workflos/pages-deploy.yml` exists.
Ensure the files `tools/test.sh` & `tools/deploy.sh` exists.
Rename you forked repository to `USERNAME.GITHUB.IO`
Commit all the new files that were created, this will create a new branch called `gh-pages`
Change the branch of the website to the gh-pages.





