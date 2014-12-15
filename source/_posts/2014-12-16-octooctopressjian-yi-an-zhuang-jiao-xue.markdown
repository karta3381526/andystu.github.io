---
layout: post
title: "how to install octopress on github"
date: 2014-12-16 00:17:53 +0800
comments: true
categories: octopress安裝教學 
---
## 在Github上使用octopress建構blog

###1. on mac
```
$ cd ~/.ssh
$ ssh-keygen -t rsa -C "xxx@xxx.xxx.xx"
$ pbcopy < ~/.ssh/id_rsa.pub #copy pubkey to clipboard
```
###2. on Github
github 申請帳號 (e.g. xxxx)  
github 建立 xxxx.github.io 的repository  
github [上傳ssh key](https://help.github.com/articles/generating-ssh-keys/)

<!--more-->
###3. back to mac
```
$ ssh -T git@github.com #for testing your sshkey
```

###4. Local端 安裝octopress 
```
$ git clone git://github.com/imathis/octopress.git octopress
$ cd octopress
$ bundle install
$ rake install
$ rake setup_github_pages
```

### trouble shooting
- problem during "rake deploy"
在 rake deploy 會出現 error, 解決方法如下
- 編輯 Rakefile (Edit the Rakefile and look for this line:)
```
system "git push origin #{deploy_branch}"
```
修改成
```
system "git push origin +#{deploy_branch}"
```

- 其他解法
```
cd octopress/_deploy
git pull origin master
cd ..
rake deploy
```

- Done and Ready to blog
