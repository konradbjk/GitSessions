# Git Tags

There are no remote tags, though (unless you (re)invent them). There are only local tags, so you need to get the tag locally in order to use it.

Firstly fetch the tags (metadata). 
You should think of git fetch as directing your Git to call up (or perhaps text-message) another Git—the "remote" — and have a conversation with it. 

```
git fetch --tags
```
Or with prune
```
git fetch --all --tags --prune
```

Then you can checkout to it
```
git checkout tags/<tag_name> -b <branch_name>
```
It's worth noting that ```git checkout tags/<tag_name> -b <branch_name>``` does require the ```-b <branch_name>```. 

```git checkout tags/<tag_name>``` gives a detached head. You avoid a detached head by temporarily creating and deleting a branch.

Since git supports shallow clone by adding the --branch to the clone command we can use the tag name instead of the branch name. Git knows how to "translate" the given SHA-1 to the relevant commit
```
git clone <url> --branch=<tag_name>
```
```--branch``` can also take tags and detaches the HEAD at that commit in the resulting repository.

### Changelog & Releases

This repository keeps a change log using [GitHub's releases](https://github.com/hassio-addons/addon-base-python/releases) functionality. The format of the log is based on [Keep a Changelog](http://keepachangelog.com/en/1.0.0/).

Releases are based on [Semantic Versioning](http://semver.org/spec/v2.0.0.html), and use the format of ```MAJOR.MINOR.PATCH```. In a nutshell, the version will be incremented based on the following:

- MAJOR: Incompatible or major changes.
- MINOR: Backwards-compatible new features and enhancements.
- PATCH: Backwards-compatible bugfixes and package updates.


### list tags
 list all tags
```
git tag
```
List all tags with given pattern ex: v-
```
git tag --list 'v-*'
```
### Adding tag

![annotated tag](https://i.stack.imgur.com/EwBtF.jpg)

### push tags
Created tags needs to be pushed to repo
```
git push --tags
```
To push all tags:


![tags pushing](https://i.stack.imgur.com/qLEtr.png)

Using the refs/tags instead of just specifying the <tagname>.

Why?

    It's recommended to use refs/tags since sometimes tags can have the same name as your branches and a simple git push will push the branch instead of the tag

The general form for names for specific commits (which Git calls *references*) is any string starting with ```refs/```. A string that starts with ```refs/heads/``` names a branch; a string starting with ```refs/remotes/``` names a remote-tracking branch; and a string starting with ```refs/tags/``` names a tag. The name ```refs/stash``` is the stash reference (as used by git stash; note the lack of a trailing slash).

One thing Git does to make this confusing is that it allows you to omit the refs/, and often the word after refs/. For instance, you can omit refs/heads/ or refs/tags/ when referring to a local branch or tag—and in fact you must omit refs/heads/ when checking out a local branch! 


To push annotated tags and current history chain tags use:
git push --follow-tags

This flag ```--follow-tags``` pushes both commits and only tags that are both:
- Annotated tags (so you can skip local/temp build tags)
- Reachable tags (an ancestor) from the current branch (located on the history)

From Git 2.4 you can set it using configuration
```
git config --global push.followTags true
```

### tag deletion
You may have to use git fetch --tags to get their tags. If their tag names conflict with your existing tag names, you may (depending on Git version) even have to delete (or rename) some of your tags, and then run git fetch --tags, to get their tags. Since tags—unlike remote branches—do not have automatic renaming, your tag names must match their tag names, which is why you can have issues with conflicts.

#### Delete a local tag

```
git tag -d <tag_name>
Deleted tag <tag_name> (was 000000)
```
Note: If you try to delete a non existig Git tag, there will be see the following error:
```
git tag -d <tag_name>
error: tag '<tag_name>' not found.
```
#### Delete remote tags

Delete a tag from the server with push tags
```
git push --delete origin <tag name>
```
