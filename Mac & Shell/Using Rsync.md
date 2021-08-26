```shell
rsync -aE --delete ~/Documents/ "/Volumes/Lacie500/Documents/"
```

It essentially does two things:

1.  Copies anything that has changed since the last copy
2.  Deletes anything on Lacie500 that is no longer in the Documents folder on my Mac

[Source, including how to set this up with Automator](http://www.practicallyefficient.com/2011/03/18/rsync-automator.html)