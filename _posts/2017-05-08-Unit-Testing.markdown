---
title:  "Unit Testing"
date:   2016-11-16 11:11:11
author: Aashish Dhawan
categories:
  - Technical
---

Unit Testing is one of those topics which get discussed a lot and everyone says that we must use it but in fact truth is, in real world you find lot of things which push you away from Unit Testing, Here is my personal experience with Unit Testing and factor affecting it and lessons learned.

When we started a brand new project, just like other law abiding citizen of programming world, we decided that this time we are going to do it in a perfect way.
We agreed to create proper documentations, write unit tests, write down the code style guides, follow agile, use standard git work flow and all those other things which we thought are going to make this project easy to work with, collaborate and scale.

> This project was an iOS app and i am going to discuss only aspect i.e Unit Testing.

In the beginning everything was working smoothly and we were happy that we spent some time initially to finalize the way we want to work but as we moved forward on time scale we began to saw faults in our ideal approach.

As the time passed and we delivered initial builds to client they came up with changes; now since this is normal and we were prepared for this, but the frequent changes were having an adverse effect on our speed and we found developers began complaining about Unit Test in sprint retrospective while we were missing deadlines frequently. The same old argument __"It slows us down".__

In project retrospective we also found that we were being overly obsessed with code coverage and the percentage __code coverage was being considered as a parameter to judge code quality.__ We also figured out the we could have done fairly well if we skipped few parts of the code. Also we had decent __QA force available__ to us which could quickly test the new changes.

And as the time progressed who found developers were writing less and less Unit test and the situation deteriorated to such a level the they stopped writing Unit Tests.

We did spend some time in project retrospective on this problem and here
are the lesson we learned from this project:

## 1. Do not be obsessed with 100% code coverage.

Now this is important. You can save lot of time when you know which part should be covered. For most people the answer to this puzzle is "Write tests for those parts which will block further development or App use". Other say "Write test for those parts which has high probability of bugs" and the answer might be different for you. All i am saying is there is not point in writing test coverage for background color of screen.


## 2. Write tests when API are being developed simultaneously.

This is an area where Unit Testing is extremely useful and most of the time it happens that mobile developers are blocked because of APIs. In this time developers can write test cases if they know the response of API in advance and when APIs are available your code is ready to handle that and your Unit tests are written to catch any errors, therefore integrating APIs should be plug-and-play case for you.


## 3. Write tests for edge cases and time consuming tasks.

If you have a good force of QAs available even then some edge cases need special attention because either they are difficult to reproduce or take time to reproduce therefore writing unit test cases of these edge cases saves considerable time.

## 4. Date/Time related logic.

We find date related cases too frequently where you can only test it on specific day. For example if an event needs 2 days to finish or it happens on Monday only. There cases can be tested with Unit Testing to save time.

## 5. Do not abandon test cases because it is a piece of code too.

After all, Unit test is also a code which needs maintenance. If left unintended it will do more harm than good. So whenever you think writing Unit Tests is not in your interest, just think about your strategy and plan again.

Unit testing is really a powerful tool, but using it properly is also very important.

Happy Coding!
