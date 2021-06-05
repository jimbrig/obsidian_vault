%%
ID: 6397120
Updated: 2020-11-24
%%
![](https://images-na.ssl-images-amazon.com/images/I/51QQtVlsWsL._SL500_.jpg)

# About
Title: [[Pro Git]]
Authors: [[Scott Chacon]], [[Ben Straub]]
Category: #supplementals
Number of Highlights: ==10==
Last Highlighted: *2020-11-24*
Readwise URL: https://readwise.io/bookreview/6397120

# Highlights 
The command goes out to that remote project and pulls down all the data from that remote project that you don’t have yet. After you do this, you should have references to all the branches from that remote, which you can merge in or inspect at any time.  ^113029508

---

Git doesn’t automatically infer your command if you type it in partially. If you don’t want to type the entire text of each of the Git commands, you can easily set up an alias for each command using git config.  ^113029509

---

When you do actions in Git, nearly all of them only add data to the Git database. It is hard to get the system to do anything that is not undoable or to make it erase data in any way.  ^113029510

---

This makes Git more like a mini filesystem with some incredibly powerful tools built on top of it, rather than simply a VCS.  ^113029511

---

Most operations in Git only need local files and resources to operate—generally no information is needed from another computer on your network.  ^113029512

---

Because a branch in Git is in actuality a simple file that contains the 40 character SHA-1 checksum of the commit it points to, branches are cheap to create and destroy. Creating a new branch is as quick and simple as writing 41 bytes to a file (40 characters and a newline).  ^113029513

---

The last really useful option to pass to git log as a filter is a path. If you specify a directory or filename, you can limit the log output to commits that introduced a change to those files.  ^113029514

---

The Git directory is where Git stores the metadata and object database for your project. This is the most important part of Git, and it is what is copied when you clone a repository from another computer.  ^113029515

---

You may be wondering what the difference is between author and committer. The author is the person who originally wrote the work, whereas the committer is the person who last applied the work.  ^113029516

---

New files that aren’t tracked have a ?? next to them, new files that have been added to the staging area have an A, modified files have an M and so on.  ^113029517

