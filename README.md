Palantir git-flow
=================

A collection of Git extensions to provide high-level repository operations
for Vincent Driessen's [branching model](http://nvie.com/git-model "original
blog post").

The palantir version of git-flow adds extra tags that can be leveraged by versioning tools.


Getting started
---------------
For the best introduction to get started with `git flow`, please read Jeff
Kreeftmeijer's blog post:

[http://jeffkreeftmeijer.com/2010/why-arent-you-using-git-flow/](http://jeffkreeftmeijer.com/2010/why-arent-you-using-git-flow/)

Or have a look at one of these screen casts:

* [How to use a scalable Git branching model called git-flow](http://buildamodule.com/video/change-management-and-version-control-deploying-releases-features-and-fixes-with-git-how-to-use-a-scalable-git-branching-model-called-gitflow) (by Build a Module)
* [A short introduction to git-flow](http://vimeo.com/16018419) (by Mark Derricutt)
* [On the path with git-flow](http://codesherpas.com/screencasts/on_the_path_gitflow.mov) (by Dave Bock)

Not all of these may be accurate as this version of git-flow has significant changes.


Installing git-flow
-------------------

* Clone this repo and run 'installers/gitflow_installer.sh'

Uninstalling git-flow
---------------------

* Clone this repo and run 'installers/gitflow_installer.sh uninstall'


Differences
-----------

* git flow init does not have configurable branch names
* git flow init has a new option '-t' that creates an empty commit on the develop branch and tags it '0.0.0-dev'
* git flow release/hotfix start 'version' will validate that the version conforms to v?[\d]+\.[\d]+\.[\d]+
	* You can override this with by adding the -a flag
* git flow release start 'version' will create an empty commit and tag it '$version-rc'
* git flow hotfix start 'version' will create an empty commit and tag it '$version-hotfix'
* git flow support now takes different arguments: '<version> <customer> <base>' instead of '<version> <base>'
  * <version> must match v?[\d]+\.[\d]+\.[\d]+
  	* this can be overridden by adding the -a flag
  * <customer> must match [a-zA-Z0-9-]+
* git flow support start will create a branch named 'support/$version-$customer'
* git flow support start will create an empty commit and tag it '$version-support.$customer'
* git flow release/hotfix finish 'version' will tag the merge commit to develop as '$version+1-dev'
	* If you are finishing version v1.0.0, the tag on develop will be v1.0.1-dev
