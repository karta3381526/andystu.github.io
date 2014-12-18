---
layout: post
title: "set up octopress on 2nd mac for the same blog"
date: 2014-12-18 10:22:17 +0800
comments: true
categories: octopress安裝教學
---
##在另外一台Mac上安裝octopress編輯環境, 可對應編輯同一個github的blog

1. copy prikey from your master mac to your 2nd mac device and put it under ~/.ssh folder
2. clone your repository to second device
```
$ git clone https://github.com/xxx/xxx.github.io.git

```
3. setup your 2nd mac device
```
$ cd xxx
$ bundle install #install required gems
$ ssh -T git@github.com # for testing connection to github
$ rake setup_github_pages # this is important for create _deploy folder in 2nd mac device
$ rake new_post["xxxx"] 
$ rake generate
$ rake deploy # it's done while no error message here.
```

4. git between two mac device  
```
$ git pull origin source  # git pull before push every time!
$ git add .
$ git commit -m 'Lorem ipsum dolor sit amet, consectetur adipisicing elit. Quisquam'
$ git push origin source
```

###Done.

