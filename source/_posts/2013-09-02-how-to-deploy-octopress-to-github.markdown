---
layout: post
title: "How to Deploy Octopress to Github"
date: 2013-09-02 13:14
comments: true
categories: 
---

------

This blog will show you how to deploy Octopress to Github and how to publish your blogs with it. 
Follow it, enjoy it.
<!--more-->

------
## Before You Begin ##

### Install git ###

```
yum install git
```

### Install ruby-1.9.3 using rvm ###

```
curl -L https://get.rvm.io | bash -s stable --ruby
rvm install 1.9.3
rvm use 1.9.3
rvm rubygems latest
```

------

## Octopress Setup ##

### Clone Octopress source code to local ###

```
git clone git://github.com/imathis/octopress.git octopress
cd octopress    # If you use RVM, You'll be asked if you trust the .rvmrc file (say yes).
ruby --version  # Should report Ruby 1.9.3
```

### Install dependencies ###

```
gem install bundler
bundle install
```

### [Install Octopress theme](http://opthemes.com/) ###

```
rake install  # Install default theme

```

------

## Deploying to Github Pages ##

### Create a New Github Repo ###
Login [Github](http://github.com) with your account, Create a new repository and name the repository with your user name `username.github.com`. 
In addition, you should make sure that your ssh public key has been added to your account.

### Setup and Generate Blog ###

```
rake setup_github_pages
rake generate
rake deploy
```

### Commit the source ###

```
git add .
git commit -m 'your message'
git push origin source
```

------

## Configuring Octopress ##

### Main Configs ###

```
url:                # It should be `username.github.com` here
title:              # Used in the header and title tags
subtitle:           # A description used in the header
author:             # Your name, for RSS, Copyright, Metadata
simple_search:      # Search engine for simple site search
description:        # A default meta description for your site
date_format:        # Format dates using Ruby's date strftime syntax
subscribe_rss:      # Url for your blog's feed, defauts to /atom.xml
subscribe_email:    # Url to subscribe by email (service required)
category_feeds:     # Enable per category RSS feeds (defaults to false in 2.1)
email:              # Email address for the RSS feed if you want it.
```

### More Configs ###

For more configs, please refer to [Octopress Documents](http://octopress.org/docs/configuring/).

------

## [Blogging with Octopress](http://octopress.org/docs/blogging/) ##

### Create a New Post ###

```
rake new_post["title"]
```

### Edit It ###

```
vim source/_posts/YYYY-MM-DD-post-title.markdown
```

### Publish It ###

```
rake generate
git add .
git commit -m "your message"
git push origin source        # Push source branch
rake deploy                   # Push master branch
```

------

## Tips ##

* If you login with *zsh*, add `alias rake='noglob rake'` to `~/.zshrc`.
* Before `rake deply`, you can preview your new posts using `rake preview`.
* If you want to manage your blog from two places, [this document](http://blog.zerosharp.com/clone-your-octopress-to-blog-from-two-places/#disqus_thread) can help you.
