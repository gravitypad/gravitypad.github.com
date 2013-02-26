---
layout: post
title: "VerificationException: Operation could destabilize the runtime"
date: 2011-05-13
comments: true
categories: 
---
I came across this exception this morning while playing with RavenDB. A quick search shows several people have seen this exception but not a lot of solutions.

I'm not sure why, but this exception in my case was related to IntelliTrace. I turned IntelliTrace off and the exception went away. Weird.

BTW - this isn't related to RavenDB.   According to [this post](http://blogs.msdn.com/b/jnak/archive/2010/07/22/verificationexception-from-windows-azure-intellitrace.aspx), the issue is a bug in IntelliTrace.