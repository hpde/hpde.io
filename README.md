# hpde.io

Quick, uncluttered access to SPASE resource descriptions.

## What's a "landing page"?

Its a page which provides a summary of a resource and links to things you can do with the resource.

## How to form a "hpde.io" link?

The "hpde.io" web site is designed to work so that replacing "spase://" 
with "https://hpde.io/" in any SPASE Resource ID and adding ".html" to the end
will get you to a landing page. 

Links at hpde.io do not have parameters. To retrieve a particular format or form of a resource 
use one of the supported file name extensions.

## All Supported Extensions
**.xml** : Get a resource description in XML form  
**.json** : Get a resource description in JSON form  
**.html** : Get a formatted resource description  

## Tips

This repository can contain a large number of files. Making the git files as compact as possible can speed up push/pull. 

The preferred method is to eliminate all prior commits do the following:
```
git checkout --orphan temp	# Create temporary branch
git add -A	# Add all the files
git commit -am "commit message"  # Commit the changes
git branch -D master	# Delete the master branch
git branch -m master  # Rename the current branch to master
git repack -d   # Place objects not in a pack, into a pack and remove redundant packs
git gc   # Cleanup unnecessary files and optimize the local repository
git push -f origin master # Finally, force update your repository
```
With this method prior clones will not be able to do a "git pull" because the tracking information is lost.
You must always use "git clone" to get a fresh copy.

To roll-up prior commits into a past commit (Note: "e41d..." is the commit id):
```
git checkout --orphan temp e41d7f633c45c46bd42e97cecf93204191d9e4c9
git commit -m "Truncate history"
git rebase --onto temp e41d7f633c45c46bd42e97cecf93204191d9e4c9 master
```

Remove duplicate objects. After a commit and before doing a push do the following:
```
git repack -d
git gc
git prune
```