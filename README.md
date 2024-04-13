# CodingNotes
Find notes on coding and troubleshooting.
<br><br><br>


## Initializing git for a project

### From github.com:
Create new repository.\
** Any files created in here (.gitignore, README.md, ...) may conflict with what is local.

### From the local computer:
From a terminal currently in the folder containing all project files
```
git init
```
```
git remote add origin git@github.com:username/new_repo
```
or, if not using SSH
```
git remote add origin https://github.com/username/new_repo
```

### Get .gitignore or other files from repo
```
git fetch
```
```
git checkout FETCH_HEAD -- .gitignore
```
** Possibly can get all files with ```git checkout FETCH_HEAD -- .```
```
cat .\.gitignore
```

### First push
** There must be a commit on master branch to push.
```
git push --set-upstream origin master
```
** This may work as well ```git push -u origin master```


### .gitignore documentation
https://git-scm.com/docs/gitignore#_pattern_format

> A leading ** followed by a slash means match in all directories. For example, **/foo matches file or directory foo anywhere, the same as pattern foo. **/foo/bar matches file or directory bar anywhere that is directly under directory foo.

<br><br><br><br><br><br><br><br><br><br><br><br>
# "#"
## "##"
### "###"
#### "####"
##### "#####"
###### "#####"
