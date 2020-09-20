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

We begin by including the following maven dependencies, with the second being optional if you are implementing with MySQL.

<br/>


```java
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
```

<br/>

Next, we create a generic Auditable class with the following spring annotations.
@CreatedBy, @CreatedDate, @LastModifiedBy, and @LastModifiedDate

@CreatedBy and @CreatedDate
Captures the user that created the data and the date the data was created

@LastModifiedBy and @LastModifiedDate
captures the user and date the data was last modified

```java
import static javax.persistence.TemporalType.TIMESTAMP;
import java.util.Date;

import javax.persistence.EntityListeners;
import javax.persistence.MappedSuperclass;
import javax.persistence.Temporal;

import org.springframework.data.annotation.CreatedBy;
import org.springframework.data.annotation.CreatedDate;
import org.springframework.data.annotation.LastModifiedBy;
import org.springframework.data.annotation.LastModifiedDate;
import org.springframework.data.jpa.domain.support.AuditingEntityListener;

@MappedSuperclass
@EntityListeners(AuditingEntityListener.class)
public abstract class Auditable<U> {

    @CreatedBy
    protected U createdBy;

    @CreatedDate
    @Temporal(TIMESTAMP)
    protected Date createdDate;

    @LastModifiedBy
    protected U lastModifiedBy;

    @LastModifiedDate
    @Temporal(TIMESTAMP)
    protected Date lastModifiedDate;

    //getters and setters
}

```


Next we, Create a JPA Entity which extends Auditable Class or extend our existing entities. 


```java
import org.hibernate.annotations.GenericGenerator;
import org.springframework.data.jpa.domain.support.AuditingEntityListener;

import javax.persistence.*;

@Entity
@EntityListeners(AuditingEntityListener.class)
public class Product extends Auditable<String>{

    @Id
    @GeneratedValue(
            strategy= GenerationType.AUTO,
            generator="native"
    )
    @GenericGenerator(
            name = "native",
            strategy = "native"
    )
    private Long id;

    private String name;

    private String description;

    private String type;

    private double price;

    private String notes;

    @ManyToOne
    @JoinColumn(name="user_id")
    private User company;



//getters and setters

}
```

We would also need to help the listners in figuring who the current user is - Auditing the Author

```java
import java.util.Optional;

import org.springframework.data.domain.AuditorAware;

public class AuditorAwareImpl implements AuditorAware<String> {

    @Override
    public Optional<String> getCurrentAuditor() {
        return Optional.of("lekan");
        // Use below commented code when will use Spring Security.
    }
}

```

If you have implemented Spring security and would love to add it you can ovveride like this


```java
class SpringSecurityAuditorAwareimpl implements AuditorAware<User> {

 public User getCurrentAuditor() {

  Authentication authentication = SecurityContextHolder.getContext().getAuthentication();

  if (authentication == null || !authentication.isAuthenticated()) {
   return null;
  }

  return ((MyUserDetails) authentication.getPrincipal()).getUser();
 }
}

```

Finally, we need to enable @EnableJpaAuditing(auditorAwareRef = "auditorAware") in our config class. or in our main class springboot starter class. we also need to let our application to be aware of our implementation the AuditorAware<String>  bean


 ```java
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.context.annotation.Bean;
import org.springframework.data.domain.AuditorAware;
import org.springframework.data.jpa.repository.config.EnableJpaAuditing;

import net.guides.springboot.springboot2jpaauditing.audit.AuditorAwareImpl;

@SpringBootApplication
@EnableJpaAuditing(auditorAwareRef = "auditorAware")
public class AuditingApplication {

    @Bean
    public AuditorAware<String> auditorAware() {
        return new AuditorAwareImpl();
    }

    public static void main(String[] args) {
        SpringApplication.run(Springboot2JpaAuditingApplication.class, args);
    }
}

```

And we are done!.

so for every entity that extends the Auditor Class we get these four additional fields.

![Screen Shot 2020-09-21 at 12.30.35 AM.png](/uploads/Screen%20Shot%202020-09-21%20at%2012.30.35%20AM.png)

 
Happy Coding🙂