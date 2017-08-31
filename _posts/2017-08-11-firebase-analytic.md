---
title:  "Understand user behavior using Firebase Analytics"
date:   2017-08-11
author: Ashutosh Singh
categories:
- blog
tags:
- android
---


Firebase Analytics is an analytics solution to help you gain insights on what users are doing with your app. It gives you many different reports(Active User, Cohort, etc.) and filters to help you understand how your app is progressing toward your goals. Analytics reports help you understand clearly how your users behave, which enables you to make informed decisions regarding app marketing and performance optimizations.

### Key Feature of Firebase Analytics

* Unlimited Reporting: Analytics provides unlimited reporting on up to 500 distinct events.

* Audience Segmentation: Custom audiences can be defined in the Firebase console based on device data, custom events, or user properties. These audiences can be used with other Firebase features when targeting new features or notification messages.

### Dashboard

#### Active Users
Active users are plotted by time.

* Monthly:  The number of unique users who engaged with the app in the previous 30 days leading up to the last day of the date range.

* Weekly: The number of unique users who engaged with the app in the previous 7 days leading up to the last day of the date range.

* Daily: The number of unique users who engaged with the app on the last day of the date range.

#### Average revenue
Average revenue shows the `average revenue per user (ARPU)` and `average revenue per paying user (ARPPU)` for the monthly, weekly, daily active user. Revenue is the sum of ecommerce_purchase and in_app_purchase event value. ARPU is revenue divided by the total users for the given time periods. ARPPU is revenue divided by the users who have purchased during the given time periods.

#### first_open attribution
The number of times the app was opened after installing or re-installing it. `first_open` attribution event is not raised when the user downloads the app from `Play store` or `iTunes`.

#### Retention cohort
A `cohort` is a set of users who started using your app at the same time (such as on the same day, or during the same week). The bottom row represents the most recent cohort. The top row step represents the earliest cohort. Darker shading indicates that a higher percentage of users returned to use the app again. Over time, the shading becomes lighter as fewer users return to use the app.

#### User engagement
The percentage value represents the amount of increase or decrease and solid line in the graph shows engagement trends according to user engagement(Daily engagement, Daily engagement per user and Session per user) respectively.

* Daily engagement: Sum of user engagement time for all users. The percentage value represents the amount of increase or decrease in user engagement. The solid line in the graph shows total daily engagement trends.

* Daily engagement per user: Average engagement duration per user.

* Sessions per user: Total number of sessions divided by the number of active users.

* User engagement per screen: Analytics automatically tracks some information about screens in your application, such as the class name of the `UIViewController` or `Activity` that is currently in focus. When a screen transition occurs, Analytics logs a screen_view event that identifies the new the .

#### In-App purchases
* Users: number and percentage of users who have completed in-app transactions (in_app_purchase).
* Count: number of transactions, and percentage change from comparison period.
* Value: revenue from transactions, and percentage change from comparison period.

#### App version
A number of the app user for top three version and other(which include the sum of all other versions).

####  Devices
* Percentage of users on each of the top three device models and other(which include the sum of all other devices).
* Percentage of users on each of the top two OS versions and other(which include the sum of all other OS version).

#### Location
Percentage of sessions from each of your top countries.

#### Demographics
Percentage of male and female users, by age group.

#### Interests
Percentage of users in each interest group.

### Events
Events show the list of events which triggered in app during the range(date range). An Event is an important occurrence in your app that you want to measure. You can report up to 500 different types of Events per app and you can associate up to 25 unique parameters with each Event type. Each event type is identified by a unique name. Event names can be up to 40 characters long, may only contain `alphanumeric characters` and `underscores`, and must start with an `alphabetic character`. The `firebase_`, `google_` and `ga_` prefixes are reserved and should not be used.

Firebase provides the following metrics for each event:
* Users: number of users who triggered the event.
* Count per user: average number of times per user that the event was triggered.
* Value: the sum of all VALUE parameters supplied with the event. Use this context-sensitive metric to track any data that is valuable to your app (e.g., revenue, time, distance).

There are some events that are automatically triggered for firebase for more information https://support.google.com/firebase/answer/6317485?hl=en. You can log events with the `logEvent()` method.
The following example how to log a SELECT_CONTENT Event:

```
undle bundle = new Bundle();
bundle.putString(FirebaseAnalytics.Param.ITEM_ID, id);
bundle.putString(FirebaseAnalytics.Param.ITEM_NAME, name);
bundle.putString(FirebaseAnalytics.Param.CONTENT_TYPE, "image");
mFirebaseAnalytics.logEvent(FirebaseAnalytics.Event.SELECT_CONTENT, bundle);
```

### Firebase Audience

You can combine events and user properties into Firebase audiences. You can perform deep analysis on each of your audiences.For example, you might want to look users from a specific interest who have reached a certain achievement level in your app.

Use audiences to:
* Filter reports so you can analyze how different user segments engage with your app
* Target Notifications to individual audiences
* Target Remote Config to deliver custom experiences to different audiences

To create a new audience:

* In Firebase, click the Audiences tab.
* Click NEW AUDIENCE.
* Enter a name and description for the audience. This name and description will allow you to identify the audience in the management table.
* Click Select Event or User Property.
* Create one or more conditions that define who should be included in this audience. You can create conditions that include the users who have taken specific actions (Event) or who share a property (User Property). Combine multiple conditions with OR or AND.
* Click Create to save your condition(s) and create the audience.


#### References
https://firebase.google.com/docs/analytics/
