---
title: Installing Ruby - MAC
date: 2020-08-03 16:41:00 +01:00
image: "/uploads/sn.png"
---

I recently tried installing ruby on my mac and faced a lot of challenges during the install.
I really hope this guide helps.

[Ruby ](https://www.ruby-lang.org/en/) is a great programming language for developing complex web applications. (makes it look like magic!).
I felt I dive deeper into ruby ([ruby on rails](https://rubyonrails.org/)) after observing the ease with which you can do some much very quickly with very little code.

so here are the commands you need to run to get you started.

```shell
leksyde$ \curl -sSL https://get.rvm.io | bash
leksyde$ source /home/<user>/.rvm/scripts/rvm
leksyde$ rvm -v
leksyde$ rvm install ruby
leksyde$ ruby -v
leksyde$ sudo apt-get install rubygems
leksyde$ gem update
leksyde$ sudo apt-get install ruby-dev zlib1g-dev liblzma-dev build-essential patch
leksyde$ rvm gemset list
leksyde$ gem install rails
leksyde$ rails -v
```


Replace <user> with your username

That's it and you are up and running!
happy coding