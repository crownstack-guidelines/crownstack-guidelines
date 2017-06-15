---
title:  "Firebase Crash Report"
date:   2017-06-12
author: Ashutosh Singh
categories:
- blog
tags:
- Firebase
---

Crash Reporting is an important feature nowadays. It is used to know that when your app get crashed and which type of error occurred. There are many tools such as Acra, Sentry, etc. `Firebase Crash Reporting` is one of them.

`Firebase Crash Reporting` generate detail error report of application. It recieves automatic crash reports just you have to integrate(easy to use). Error takes few minutes(about 20 minutes according to the Firebase docs), to appear on Crash Reporting console.

## Explore Crash Report

User can have version and error type specific crash reports.

* `Instances` number of error which occurred.
* `Users imapacted` number of users who experienced an error.
* `Issues` number of Issues. Group of exception with similar stacktrace known as `Cluster`
* `Error-free users` user percent who haven't encounter error.
* `Versions` version of app on which crash occoured.
* `Stack trace` abbreviated version of the stack trace.

<img src="/static/firebase_crash_report.png" alt="Drawing" style="width: 600px;"/>

* Provide additional data such as user location, network provider, device detail and performance.

<img src="/static/firebase_crash_report_additional_data.png" alt="Drawing" style="width: 600px;"/>
