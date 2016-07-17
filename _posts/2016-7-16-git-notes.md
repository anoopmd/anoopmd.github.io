---
layout: post
title: Git Notes
---


#Now you want to it dump and reset all changes and start from scratch
`$ git checkout HEAD filename`

#You wanted to revert all changes that you have made on a branch start from scratch
`$ git reset --hard HEAD^`

#You committed certain changes.
#Now you realize that you messed up the commit message and you just want to undo the act of #committing, leaving everything else intact
`$ git reset --soft HEAD^`