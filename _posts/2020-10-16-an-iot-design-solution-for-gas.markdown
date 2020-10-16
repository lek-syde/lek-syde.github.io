---
title: An IOT design solution for GAS
date: 2020-10-16 15:07:00 +01:00
image: "/uploads/energy.png"
subtitle: Proposed solution
---

This is a proposed solution, with the ever-increasing rate of a gas plant explosion in Nigeria, there was on just recently [here](https://nairametrics.com/2020/10/08/breaking-gas-station-explodes-in-ipaja-lagos-claims-property-and-valuables/#:\~:text=Another%20gas%20explosion%20has%20rocked,State%20Emergency%20Agency%20(LASEMA).)

I thought I make a sketch of a possible technology-powered solution to the problem.

It's a monolith that would work efficiently, it can also be scaled to a microservices architecture.

This service would work basically as a uber model for gas, powered by [spring cloud](https://spring.io/projects/spring-cloud#:\~:text=Spring%20Cloud%20provides%20tools%20for,distributed%20sessions%2C%20cluster%20state).) which would simplify development, deployment, and maintenance.

Database adapter- MYSQL, POSTGRESQL, or any database of choice. <br/>
[Twillo](https://www.twilio.com/) can be used for messaging notifications (SMS) <br/>
[Sendgrid](https://sendgrid.com/) for efficient email notifications.

<br/>
An IoT device would be placed on the LPG. it would have a GPRS/Bluetooth sensor that would constantly communicate with the system via REST API.

<br/>

This solution can be implemented by small or large gas vendors.