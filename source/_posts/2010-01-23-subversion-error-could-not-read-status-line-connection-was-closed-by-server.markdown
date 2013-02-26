---
layout: post
title: "Subversion error: Could not read status line: Connection was closed by server"
date: 2010-01-23 11:00
comments: true
categories: 
---
I've recently setup a local Subversion server for a project I'm working on with some other guys. It took a bit of convincing that having multiple developers on a project requires a source control system. Prior to the past few months, there's only been one developer working on the project (for the past 18 years!), so they've never needed version control. OK, well, they didn't *think* they needed version control. Version control was simply making a copy of the folder before you start making changes. 

I've not worked with Subversion much in the past, but it was super-simple to setup and get [VisualSVN](http://www.visualsvn.com) installed and running (thanks Scott Hanselman for the [tips](http://www.hanselman.com/blog/RunningASubversionServerOffYourWindowsHomeServer.aspx)!). 

Anyway, I've been using the repository here locally via TortoiseSVN without any issues at all. I sent the connection instructions to the other guys and one of them called today saying he received an error when trying to enlist in the repository: 

```
Could not read status line: Connection was closed by server. 
```

Ugh, I thought. Since I don't have a lot of Subversion experience, I thought I was up against some obscure issue that would take a long time to figure out. Turns out the solution was quite simple: he was attempting to connect to the server via http, but it only accepts https connections. Putting in the correct protocol solved the problem! I do think the error could be a little more descriptive...