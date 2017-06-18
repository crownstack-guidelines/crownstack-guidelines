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

## Improve application by Firebase Crash Report

A good application have less crash. It's hard to find all crash in the application at testing. There may be many untold crashes. My application was suffering from many crashes. I got lots of bad review . It was hard to find all the crash in testing environment. Then used `Firebase Crash Reporting` to track crashe in my application. Whenever a crash occured it send the crash report on firebase and notified me on my emailId. It help me to solve those crashes and making application crash free.

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

## Analytics events in Crash Logs

Firebase Analytics events are now added to your crash logs, which gives you a more complete view of the state of your app leading up to crash.

## Additional feature

* Can send custom crash log to firebase cosole.
* Can get email alert for crash.

## Conclusion

`Firebase Crash Reporting` is one of the most important tool of `Firebase` to make your app better and crash free.
