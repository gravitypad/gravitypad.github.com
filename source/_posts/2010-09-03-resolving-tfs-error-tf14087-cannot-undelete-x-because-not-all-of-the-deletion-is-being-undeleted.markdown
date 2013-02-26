---
layout: post
title: "Resolving TFS error TF14087: Cannot undelete X because not all of the deletion is being undeleted"
date: 2010-09-03 10:31
comments: true
categories: 
popular: true
---
At work, we recently encountered this error in TFS when trying to merge from our trunk into a project branch. There's [some](http://stackoverflow.com/search?q=tf14087) [information](http://social.msdn.microsoft.com/Forums/en-US/tfsversioncontrol/thread/b1be6b2b-f17a-49d6-ae0e-207ad9b10b6f) on the [internet](http://blogs.msdn.com/b/mrod/archive/2006/10/10/the-logic-and-reason-behind-error-message-tf14087.aspx) about this [error](http://geekswithblogs.net/svanvliet/archive/2007/01/14/team-foundation-server-merge-woes-tf14087.aspx), but none of them directly applied to our issue. Thankfully, one of the benefits of having Microsoft as a parent company is access to TFS engineers.

We got into this situation when someone deleted a folder in the trunk and then re-added a folder with the same name. And then deleted it. And re-added it. When you do this without merging between the delete and adds, TFS gets real confused. It tries to merge the delete and the add (and in our case, the second delete and second add), and because they are all the same name and path, you get TF14087.

The solution (thanks George) was pretty simple:
Get the deleted id for all of the deletes of the folder:
```
tf dir /recursive /deleted /slotmode $/project/trunk. 
```
This gives output like:
```
$/project/trunk:
$Build
$Configs
$Databases
$Deploy
$Docs
$External
$Folder
$Folder;X246937
$Folder;X246938
```
In our case, there are three entries for $Folder, two with deleted ids, and the one folder that has not been deleted (the last add).
Destroy the deleted folders by using their deleted ids.
```
tf destroy /preview $/ijv/trunk/folder;X246937
```
Adding the /preview argument let's you confirm what would be done when issuing the destroy command. After you review the output and make sure you're not destroying something you don't mean to, remove the /preview and run the command.

Then we run it for the other deleted id:
```
tf destroy /preview $/ijv/trunk/folder;X246938
```
Finally, do the merge from the trunk back into the project branch.
That resolved the issue for us. We lost the history of the original two versions of that folder, but it did allow us to move forward with merging. Hopefully this information will help someone when trying to resolve the same issue.