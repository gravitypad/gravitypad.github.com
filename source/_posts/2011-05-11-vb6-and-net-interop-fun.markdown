---
layout: post
title: "VB6 and .Net Interop Fun"
date: 2011-05-11
comments: true
categories: 
---
 A friend of a friend asked me to help with a project. He is a VB6 developer. Still. But he needed to incorporate a .Net component into the VB6 application in an easy way. So I've been helping him out, building up a .Net control using the Microsoft Interop Toolkit. It's a free add-in to Visual Studio that takes away a lot of the complexities in building COM interop components in .Net.

I learned something painfully recently while helping out:

If your .Net control throws an exception, VB6 will report that to you as  an "out of memory" error. That's it - no details, call stack, or anything else about the actual exception. Misleading and frustrating. Not that I would expect VB6 to give me the call stack from .Net, but "out of memory" is not only unhelpful but it is disinformation.

I should have remebered this one. We were getting the "out of memory" error in VB6 in design mode and couldn't figure out what the problem was. The error popped up immediately when opening the form designer in VB6. After much trouble trying to get VB6 to actually tell us what the problem is (we never got any information out of it, even after enhanced interrogation using WinDbg), it was real simple - we had a bug in a property setter. When the control was instantiated, VB6 was calling the setter, getting the exception, and then barfing with the incredibly unhelpful error message.

My friends will inevitably laugh and make fun of me for playing with VB6 still. That's fine. I've found the experience has led me to develop additional skills and learn more about .Net development along the way.