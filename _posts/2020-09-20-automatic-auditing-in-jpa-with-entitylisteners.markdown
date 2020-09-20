---
title: Automatic Auditing in JPA with EntityListeners
date: 2020-09-20 09:42:00 +01:00
categories:
- work
image: "/uploads/entityManagerFactory(EntityManagerFactoryBuilder).png"
---

Auditing user data is quite a very important security feature you can implement not just for the application point of view but to ensuring the integrity of data. 
In most business/web applications auditing would simply mean logging and keeping track of when and who, updates, deletes, creates and inserted data in the application.

Auditing when implemented properly helps us in maintaining history records which can later help us in tracking user activities. If implemented properly auditing can also provide us similar functionality like version control systems and can be a very important security feature.

For business scenarios, Imagine an employee deletes a record and denies it, a quick lookup with the application audit log would reveal who and when. 

Implementing this manually can get very cumbersome quickly as you would have to write lots of code especially for all crud operations and this means less maintainability 

with JPA and Hibernate provides easily implement auditing in your projects with JPA Entity Listeners