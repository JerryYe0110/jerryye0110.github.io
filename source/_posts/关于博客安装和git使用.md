---
title: 关于博客安装和git使用
date: 2021-06-18 23:19:30
tags:
  - git
  - hexo
---
可以去看看 *Git Book* 和 *Hexo doc* 感觉很完善了。
<!--More-->

今天刚搭了一个博客，可谓历经曲折。对`git`工具也算是熟悉了点了。

博客使用的是*Next* 主题， 博客本身很好安装，只要使用`npm`安装`node`和`Hexo`就行了。在博客文件夹使用`Hexo init`就可以新建一个博客。


新博客主题有点丑，所以使用 *Next* 主题， 但是这里有一个关键的问题，就是不要使用官网上写的`git clone ....` 而应该使用`giut submodule add .....`. 使用第一个会导致你`themes`里面的 *Next* 无法被`push`到博客的远程仓库上。因为你clone下来，他相当与是链接着别人的仓库的。

下载好 *Next* 主题后就不要更改 *Next* 文件夹里面的任何文件了，在博客根目录新建一个`_config.next.yml`将 *Next* 里面的`_config.yml`的内容复制到该文件内，然后在这个文件去修改你想要修改的配置。**不是在别人的配置文件内** 

*Next* 主题还是很人性化的，配置文件大概1000行，但是很容易懂，也很方便。

如果想要使用`Github page`来托管静态网页的话，那么你需要使用`traviscibot`这是一个不错的选择。先在你的`Github`上新建一个`token`， 然后下载`traviscibot`给予权限去访问博客库, 然后在`setting`里面将`Github`里建的`token`复制上去。最后在你的博客内新建立一个`.travis.yml`的文件，文件内容
```yml
sudo: false
language: node_js
node_js:
  - 10 # use nodejs v10 LTS
cache: npm
branches:
  only:
    - main # build master branch only
script:
  - hexo generate # generate static files
deploy:
  provider: pages
  skip-cleanup: true
  github-token: $GH_TOKEN
  keep-history: true
  on:
    branch: main 
    target_branch: main
  local-dir: public
```

可能会比较好用。
