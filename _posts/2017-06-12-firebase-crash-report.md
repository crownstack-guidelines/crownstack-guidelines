---
title:  "Firebase Crash Report"
date:   2017-06-12
author: Ashutosh Singh
categories:
- blog
tags:
- Firebase
---


Crash Reporting is an important feature nowadays. It is used to know that when your app gets crashed and which type of error occurred. There are many tools such as Acra, Sentry, etc. `Firebase Crash Reporting` is one of them.

`Firebase Crash Reporting` generate detail error report of application which takes few minutes(about 20 minutes according to the Firebase docs), to appear on Crash Reporting console. Also, it is super easy to integrate.

## Improve application by Firebase Crash Report

A good application has few crashes. It's hard to find all crash in the application while testing. There might be many undiscovered crashes during testing phase. Use of `Firebase Crash Reporting` to track crashes in application is recommended and whenever a crash occurs it sends the crash report on firebase and notified developer on his/her emailId. It helps me to solve those crashes and making application crash free.

## Exploring Crash Report

following are the few items which firebase provides.

* `Instances` number of errors occurred.
* `Users impacted` number of users who experienced an error.
* `Issues` number of Issues. Group of exception with similar stack trace known as `Cluster`
* `Error-free users` user percent who haven't encounter an error.
* `Versions` version of the app on which crash occurred.
* `Stack trace` abbreviated version of the stack trace.

<img src="/static/firebase_crash_report.png" alt="Drawing" style="width: 600px;"/>

* Provide additional data such as user location, network provider, device detail and performance.

<img src="/static/firebase_crash_report_additional_data.png" alt="Drawing" style="width: 600px;"/>

## Analytics events in Crash Logs

Firebase Analytics events are now added to your crash logs, which gives you a complete view of the state of your app leading up to crash.

## Additional feature

* Can send the custom crash log to Firebase console.
* Can get an email alert for the crash.

## Conclusion

`Firebase Crash Reporting` is one of the most important tools of `Firebase` to make your app better and crash free. We are using it in many applications we are working on.
