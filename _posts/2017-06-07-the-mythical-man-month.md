---
title:  "The mythical man month - Summary"
date:   2017-06-07
author: Aashish Dhawan
isbn:   0201835959
layout: writeup
categories:
- writeup
tags:
- writeup
---

## 1. A Tar Pit

This one particular book is very popular among programmers and managers. This week I got the chance to read it. The book has a vivid start, comparing large software programming projects to tar pit and the struggles to make project successful are similar to winning a fight with the pit. On the opposite side, the pleasure of making useful programming systems is also compared to the child's first clay pencil holder "for Daddy's office", the innate human desire to create new things.

What interesting is, dividing the software craftsmanship into four categories. Now, this following categorization changed the way I look at software development and how I estimate them.

### 1.1 A Program

A program when complete in itself is ready to be run by the author on the system on which it was developed. This is what people generally use to estimate work and measure productivity.

### 1.2 A programming product

The is a program which can be tested, repaired and extended by anybody. This generally needs three times more work than creating a program. For this substantial numbers of test cases needs to be written, input needs to be generalized. Input range and boundaries need to be decided and most importantly a proper documentation needs to be written and maintained.

### 1.3 A programming system

A programming system is generally a combination of many programming products and it has additional complexity of managing the interface between various programming products. Again, as a rule of thumb, a programming system is three times more costly than the combination of all its programming products.

### 1.4 A programming system product

This is truly a usable product, a combination of all of the above. It might cost nine times as much but this is the end goal of almost all large software products.

### The woes of software craftsmanship

The author sites some woes inherent to software Programming. First, the necessity to produce perfect systems which are quite opposite to human nature; Second, too many dependencies on other human beings which generally ends in poor documentations and implementations; delayed and incomplete deliveries. Third, the absence of absolute frozen requirements and end goals, as soon as you freeze something, the requirements and technology supporting it go under a transformation.

There is also a general rule of thumb for estimating time required for a software project

* 1/3 Planning
* 1/6 Coding
* 1/4 Early System tests
* 1/4 Full system tests, All components in hand.

## 2. The Surgical team

This chapter handles how a large team can be managed by dividing workforce into a small group of 10-15 people and structuring it as a surgical team.

This surgical team has a chief surgeon, a co-pilot, programming clerk, toolsmith, tester, language lawyer and support staff as Admins, Editors. This idea can be scaled to organize a large workforce.

## 3. Lesson Learned from Tower of Babel fiasco.

The author uses an example of Tower of Babel, examines this engineering fiasco and tries to learn few lessons from it. Communication he says is one of the major reason many projects fails. It is also a double-edged sword, too many of it and you are wasting too much time and lesser the number equally greater the risks.

The author suggests that a project workbook can help to minimise the risk. An updated workbook can work as a lighthouse. Also, one more interesting argument he puts forward is that a programmer works better if he/she is shielded from the unnecessary documentation. Therefore work for an individual should be clearly defined.  

## 4. Documentations for a Software Project

Here are the following documents every project manager should have at its disposal

* What: Objectives (Scope of Work)
* What: Project Specifications
* When: Schedule
* How Much: Budget
* Who: Organization Chart

## 5. Planning for change

Everyone knows that the only constant thing is change and this is especially true in software development where most of the managers blame requirement changes for missed deadlines. Now careful modularization, Precise and complete definition of interfaces are the obvious steps taken to handle this situation.

> The total cost of maintaining a widely used program is typically 40 percent or more of the cost of developing it. Also, the fundamental problem with program maintenance is that fixing a defect has substantial (20-25%) chance of introducing other.

## 6. Documentations

This is one part of the software engineering which is generally overlooked and there are a number of reasons behind it. Generally, people think it is either boring or it is not what a developer needs to do. Also, since requirement and hence implementations are tentative why make documentations. This, of course, is a dangerous thing to follow.

Documentation should be precise, regularly updated. If possible they should be automated.
