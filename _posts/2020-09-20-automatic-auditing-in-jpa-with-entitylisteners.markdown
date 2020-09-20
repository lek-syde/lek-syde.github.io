---
title: Automatic Auditing in JPA with EntityListeners- Spring boot
date: 2020-09-20 09:42:00 +01:00
categories:
- work
image: "/uploads/entityManagerFactory(EntityManagerFactoryBuilder).png"
---

Auditing user data is quite a very important security feature you can implement not just for the application point of view but to ensuring the integrity of data.
In most business/web applications auditing would simply mean logging and keeping track of when and who, updates, deletes, creates and inserted data in the application.

Auditing when implemented properly helps us in maintaining history records which can later help us in tracking user activities. If implemented properly auditing can also provide us similar functionality like version control systems and can be a very important security feature.

For business scenarios, Imagine an employee deletes a record and denies it, a quick lookup with the application audit log would reveal who did and when.
Or it could just allow us to remember when a user signed up to remind our a cron job to send a birthday 🎂 greeting card.

Implementing this manually can get very cumbersome quickly as you would have to write lots of code especially for all crud operations and this means less maintainability. 

JPA and Hibernate provide an easy way to implement auditing in your projects with JPA Entity Listeners.

We begin by including the following maven dependencies, with the second being optional if you are implementing with mysql.
<p>
<code>
<dependencies>
    <dependency>
        <groupId>org.springframework.boot</groupId>
        <artifactId>spring-boot-starter-data-jpa</artifactId>
    </dependency>

    <dependency>
        <groupId>mysql</groupId>
        <artifactId>mysql-connector-java</artifactId>
        <scope>runtime</scope>
    </dependency>
</dependencies>
</code>

</p>



