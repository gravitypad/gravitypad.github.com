---
layout: post
title: "DasBlog: Fixing 404’s for mapped urls"
date: 2011-04-04
comments: true
categories: 
---
Two things have been bugging me since I migrated this blog over to dasBlog: I started getting a bunch of 404 errors for urls that are mapped to dasBlog handlers, and getting a better html editor wasn’t working.

####404’s for things like deleteitem.aspx, blogger.aspx, etc.

This fix was simple. I am running this site on Windows Server 2008 R2, and the application pool was in Integrated Mode. Switching to Classic Mode got all of the handler mappings working. I’ll need to dig around in the web.config to get the handlers migrated to IIS7.5 syntax so I can go back to Integrated Mode. This fix also got comments working.

####Setting TinyMCE as the editor

I had downloaded the TinyMCE editor adapter from John Forsythe, but it never worked. There seemed to be people with similar issues, but no resolution. This was even worse for me, because since I was getting 404’s for blogger.aspx, I couldn’t use Windows Live Writer either. I resorted to handcrafting my html. Yuck.
This one was simple to fix, but I didn’t figure it out until I installed the wonderful ELMAH. Looking at the Elmah logs showed this error:

```
tinymce\jscripts\tiny_mce\tiny_mce_gzip.aspx(5): error CS0246: The type or namespace name 'ICSharpCode' could not be found (are you missing a using directive or an assembly reference?)
```

In the installation instructions, it said that you don’t need to install the ICSharpCode.SharpZipLib.dll, because it’s the same one installed with dasBlog. But the version of dasBlog I was running didn’t have that assembly. A quick search and download, and voilla – TinyMCE is working!