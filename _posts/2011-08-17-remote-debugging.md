---
layout: post
title: Remote Debugging
comments: true
categories: [software]
tags:       [cross-post-interknowlogy]
---
Originally posted on [blogs.interknowlogy.com](http://blogs.interknowlogy.com/2011/08/17/remote-debugging/)

Recently we’ve been developing an application that runs on a Win7 PC and has a slimmed down version that runs on Win7 Tablets. In our case we’re using the HP Slate. Our development machines are running Win7 and VS2010. The development machines are on our domain while the HP Slates are not. The project has been going for some months now and we’ve been relying heavily on logging using Enterprise Library to know what errors we’re up against. However, we all know that as the complexity of an application increases so does the likelihood that we may log incorrect, useless, or unrelated data. Enter the need for remote debugging. I thought this would be straightforward and easy but I was very much mistaken.

## Getting Ready to Remote Debug
I started on the (MSDN http://msdn.microsoft.com/en-us/library/y7f5zaaa.aspx) in the section (How to: Set Up Remote Debugging http://msdn.microsoft.com/en-us/library/bt727f1t.aspx). Here I learned that firewalls and permissions are the first huge hurdle called out by Microsoft. I must say when it comes to limited time firewalls are out. So instead of fighting my way through setting up firewalls to work correctly I just disabled them for all machines involved for this remote debugging session. Later in this same article it tells how to install the software required for the remote machine in order to debug remotely. There is broken link to the download center for the software required, but the optional location is on the VS2010 installation media in the folder (VS Media)\Remote Debugger. Be sure to install the correct version on the remote machine. Instructions for this are in the article.

## Running the Remote Debugging Monitor
STOP! Why? Because you really should figure out which users you’re going to use on both the VS2010 host machine and the remote machine before trying to run the Debugging Monitor.
Selecting the Appropriate User Accounts for Remote Debugging
I tried to remote debug at this point and found there is one more piece of information that I was missing. Going back to the list of articles on the (MSDN http://msdn.microsoft.com/en-us/library/y7f5zaaa.aspx) the next important section is (Remote Debugging Across Domains http://msdn.microsoft.com/en-us/library/9y5b4b4f.aspx). This section lists the restrictions relating to user accounts right away. I will copy the first section here for review:
To connect to msvsmon, you must run Visual Studio under the same user account as msvsmon or under an administrator account. (You can also configure msvsmon to accept connections from other users.)
Visual Studio accepts connections from msvsmon if msvsmon is running as a user who can be authenticated on the Visual Studio computer. (The user must have a local account on the Visual Studio computer.)
With these restrictions, remote debugging works in various scenarios, including the following:

- Two domains without two-way trust.
- Two computers on a workgroup.
- One computer on a workgroup, and the other on a domain.
- Running the Remote debugging monitor (msvsmon) or Visual Studio as a local account.

Therefore, you must have a local user account on each computer, and both accounts must have the same user name and password. If you want to run msvsmon and Visual Studio under different user accounts, you must have two user accounts on each computer.

You can run Visual Studio under a domain account if the domain account has the same name and password as a local account. You must still have local accounts that have the same user name and password on each computer.

End Quote.

We will cover the last part in detail since that is the scenario I was faced with. In simple terms if your domain is named us and the user account is danny (us\danny) then the VS2010 hosting machine must have a local user account named danny with admin privileges with the same password as the us\danny account. Also, the remote machine, in my case the HP Slate, must have a local user account named danny with the same password as the other two danny accounts and must also be an admin on the machine. After all accounts are created and have been accessed for the first time restart all machines and boot the VS2010 hosting machine into the domain account (us\danny) and the remote machine into the local account with the same name as the domain account (machine name\danny).

This essentially means that three(3) accounts named danny must exist: us\danny, vs2010 machine name\danny, and remote machine name\danny and all of them must be admins on their respective boxes and all must use the same password.

## Running the Remote Debugger (For Real)
Again returning to the list of articles on the (MSDN http://msdn.microsoft.com/en-us/library/y7f5zaaa.aspx) the next article is (How to: Run the Remote Debugging Monitor http://msdn.microsoft.com/en-us/library/xf8k2h6a.aspx). You have two choices at this point. Run the monitor as needed or run the monitor as a service. Because we will be constantly debugging using the HP Slate I decided to run the monitor as a service which requires a little extra work. You will need to run Local Security Policy. Then under Local Policies\User Rights Assignment there is a policy named Log on as a service that must be granted for the user that will be running the debugging monitor.
Performing a Remote Debug
I’m still struggling with this a little. I cannot figure out how to have VS2010 compile and launch the application I want to debug on the remote machine. Instead copy the compiled project files from the bin\debug folder of your project to the remote machine (I suggest a location easy to access and replace files in). Run the executable on the remote machine then in VS2010 of the hosting machine open the Attach to Process dialog (ctrl + alt + p). There is a drop down name Qualifier that when opened will detect the machine you’re trying to remote debug. Select the remote machine then attach to the process on the remote machine like you would as if the process were on the VS2010 hosting machine.

## Thoughts
It only took a few hours to figure this all out. The part that kept killing me was the fact that even after you create a user account if you don’t log on as that user then it will not be available for use. Remote debugging is definitely cool! It helped us figure out quite a few issues in our remote code very quickly. Now that I know how to set up a remote debugging environment I will be using it more often.