---
title: Ruby on rails + MySQL
date: 2020-10-15 14:07:00 +01:00
image: https://dummyimage.com/600x400/000/fff.png&text=Working+with+MySQL+in+Ruby+on+Rails
---

This post shows you how you can connect your new or existing rails application to use a MySQL database.

Step 1.
Install MySql server on your development machine. you can do this by downloading the installer here [Mysql for Mac](https://dev.mysql.com/doc/mysql-osx-excerpt/8.0/en/osx-installation-pkg.html)
Note: **Take note of your installation credentials. ie Username and password.** 
A good practice would be to create a new user aside from the default root user.

Step 2.
Option 1.
if you are just starting out creating a new ruby application use
```console
rails new app_name -d mysql
```

This would replace the default SQLite database gem and would add the MySQL gem
```console
gem ‘mysql2’
```
Option 2 
For existing projects
Simply replace/add the MySQL gem 

Step 3.
Update your database details in the config/database.yml file with your correct MySQL credentials

```console
development:
  <<: *default
  adapter: mysql2
  database: [database name]
  username: [database username]
  password: [database password]
```

**ensure you replace with the correct details**

Step 4.
For Existing projects, you would need to run your migrations 
```console
rails db:migrate
```

Congratulations you are up and running with Ruby on Rails and MySQL🙂



