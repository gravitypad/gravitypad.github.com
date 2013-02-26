---
layout: post
title: "Powershell AuthorizationManager check failed"
date: 2012-06-04
comments: true
categories: 
---
While debugging some Powershell scripts today, I started getting an error:
 
```
AuthorizationManager check failed.
At C:\Users\pkearne\setupPLT.ps1:6 char:14
+ ./logging.ps1 <<<<
    + CategoryInfo      : NotSpecified: (:) [], PSSecurityException
    + FullyQualifiedErrorId : RuntimeException
```
<!--more-->
After some web searching, there seems to be two primary reasons this happens:
 
* An empty Powershell profile script
* WMI service not running

Neither of these cases was true for me. However, the first one pointed me in the right direction. Somehow a script I was calling out to (logging.ps1) had it's contents removed. Had the file been deleted, the error would have been that the cmdlet, function etc was not recognized. But having the file present but empty gave the misleading error "AuthorizationManager check failed".
 
So, if you are getting this error and everything else looks correct, look and see if something similar is causing your problem.