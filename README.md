debsizes
========

Find which packages are using all your disk space, including dependencies

Example:
```
$ ./debsizes | head  # What's using all my space?
 63 M  mysql-server
 47 M  vlc
 42 M  phpmyadmin
 33 M  miro
 31 M  python-pip
 24 M  geany-plugins
 17 M  git
 15 M  hexchat
 11 M  drush
 10 M  workrave
$ ./debsizes mysql-server | head  # What dependencies is mysql-server pulling in?
 32 M   1 mysql-server-5.5
 19 M   1 mysql-server-core-5.5
  7 M   2 mysql-client-5.5
  1 M   2 mysql-client-core-5.5
537 K   2 libdbi-perl
386 K   3 libmysqlclient18
218 K   1 libhtml-template-perl
116 K   1 mysql-server
 77 K   2 libdbd-mysql-perl
 53 K   1 libaio1
```

Notes:
* debsizes knows to only look at manually-installed packages
* If you have a file named ~/Keepers/system , debsizes will ignore packages listed in that file. This is good for excluding base packages that you know you won't want to remove.
* The number next to each dependent package is the count of other manually-installed packages pulling in that dependency. Each depending package is allotted a portion of the dependency's disk usage.
