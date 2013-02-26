---
layout: post
title: "Remember, controller classes need to be public"
date: 2011-11-30
comments: true
categories: 
---
File this one under Duh! I was troubleshooting a routing issue I was having with a portable area in ASP.Net MVC. For some reason I kept getting a 404. The solution was pretty big, so I created two new projects to try and isolate the problem.

I created a new web project and a class library for the portable area. Added my routes to the area, created a new class, renamed the class MyController, wired it all up, and got the same thing.

I installed Glimpse to see what routes were being hit. But Glimpse only works if ASP.Net handles the request, and since it was a 404, I couldn’t see the Glimpse data.
<!--more-->
So I installed Phil Haack’s awesome route debugger. The route debugger has a catchall route, so even if the request would result in a 404 it will return you back the debug information. I could see that the route was being hit, but it still 404’ed.

I set breakpoints. I added some logging. Nothing would cause my controller action to get executed.

Then it struck me. Visual Studio by default creates new classes without an access modifier, and when no access modifier is specified, the default is internal. MVC needs controller classes (and the action methods) to be public so they can be constructed via reflection.

``` c#
using System.Web.Mvc; 
namespace TestArea.Controllers
{
   public class MyController : Controller
   {
       public ActionResult Index()
       {
          return View();
       }
   }
}
```

The really sad part is I just helped a colleague solve the exact same problem the week before.

I don't know why Visual Studio defaults to not putting a access modifier on new classes. I always prefer to be explicit with such things.