---
layout: post
title: Timers and Alarms in Windows Phone 7.5 (Mango)
comments: true
categories: [software]
tags:       [cross-post-interknowlogy]
---
Originally posted on [blogs.interknowlogy.com](http://blogs.interknowlogy.com/2011/10/12/timers-and-alarms-in-windows-phone-7-5-mango/)

One thing I really wish Microsoft had built into the Windows Phone 7 from the beginning was a simple timer. The iPhone has one. The Android has one. Windows Phone 7.5 still has yet to add this simple functionality. So I took the task upon my self to develop one. The first thing I didn’t understand was which Scheduler was the correct Scheduler to use. There were a lot introduced with Wp7.5 found here. Before I even looked at that page I opened up Visual Studio and found the “Windows Phone Scheduled Task Agent” project template and started to play with that. My immediate thought was “PeriodicTask is for scheduling when a timer should run.” This is definitely not the case since PeriodicTasks only run once every 30 minutes or so. Once I discovered Alarm notifications it was very simple to sort all of that out.

The Wp7.5 SDK provides a lot of great controls. However, I found it lacking a way to specify hours, minutes, and seconds through a picker. Luckily Coding4Fun took care of that for me with the TimeSpanPicker. Armed with an Alarm and the TimeSpanPicker I was able to create a super simple timer application.

A few notes about the outcome of the application:

1. It is not possible to reuse sounds built into the Phone for your custom timer. I still don’t understand why Microsoft will not allow this. Why can’t I have my alarm play one of the built in sounds let alone why can’t I have it play my favorite song when the alarm finishes?
2. I’ve found that the alarm is accurate up to 30 seconds. Meaning, I found that the alarm notification would not actually notify me right away. The longest delay I’ve found is 30 seconds, but usually it’s within 10 seconds. This is acceptable, but again disappointing.
3. Sometimes the alarm notification will not display if the application that created it is running. Perhaps this is by design? One could assume that if the application is setting an alarm that it doesn’t intend on running when it completes, and if it is running then it should be tracking the time on its own.