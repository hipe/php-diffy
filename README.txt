Basically, pipe a `git status` or `svn status` to `sftp`.

This is intended as a small utility script that generates and/or pushes
various kinds of diffs in various ways: using svn, git, rsync, diff or the 
filesystem.  It is a poor man's git in svn environments, to allow something 
like local branches, or stashes.

The idea is if you're working locally and you've changed a few files and want 
to push them up to a development server for someone to review, you shouldn't
have to commit them into version control to do so, yet version control can aid
in showing you the list of files you have changed since your last push.

At one point I was also using this to maintain local branching w/o actually 
branching - while i was working in an svn environment my superiors kept task
switching me between three different tickets.  When the first task-switching 
happened, I sayz to diffy, I sayz:
  "Take every file that I have changed since HEAD and put it in a folder
  (maintaining the structure.)  That is, make a subtree of the project tree
  containing only those files that have changed." 
  
(actually, at that time i was doing this manually, which is when i decided i needed to make something like this.)

Then in my main folder I revert back to a pristine copy, and work on the new 
task.  But then, uh-oh, now the second task-switch happens where I need to 
change to a third task.  Same thing: take these files that have changed and 
put them into a subtree.  (Sort of a bloated patch.)

When task three is finished, I can commit, then go back to task 2 by moving
all of the files in the subtree folder back over to my working copy. 
(At this point if you actually need any merging capabilities then you 
shouldn't be trying it with this thing ;)  Finish task 2, commit, and repeat
with the subtree in task 1.

Now I know better and I know that I should have been using git. 

---

A more complete version of this got stolen on my laptop before i was using
github :/  But this is here for posteritiy.

(Thinking of porting this to ruby or adding it as a feature to 'visiting')