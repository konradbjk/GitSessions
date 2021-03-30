# Git workflow

Consider your team’s culture. You want the workflow to enhance the effectiveness of your team and not be a burden that limits productivity 

Questions to ask
- Does this workflow scale with team size?
- Is it easy to undo mistakes and errors with this workflow?
- Does this workflow impose any new unnecessary cognitive overhead to the team?

**Table of Content**:
1. [Centralized Workflow](#centralized-workflow)
2. [Feature Branching](#feature-branching)
3. [Forking Workflow](#forking-workflow)
4. [GitHub Flow](#github-flow)
5. [GitLab Flow](#gitlab-flow)

### Centralized Workflow
One repository, one branch ...and hopefully one developer.

### Feature Branching
All feature development should take place in a dedicated branch.

This encapsulation makes it easy for multiple developers to work on a particular feature without disturbing the main codebase. It also means the master branch should never contain broken code, which is a huge advantage for continuous integration environments. 

Consider:
- **Short-lived branches**
The longer a branch lives separate from the production branch, the higher the risk for merge conflicts and deployment challenges. Short-lived branches promote cleaner merges and deploys.
- **Minimize and simplify reverts**
A workflow that tests a branch before allowing it to be merged into the master branch. Mistakes happens and you should be able to easily revert a mistake (without interrupting your colleagues)
- **Match a release schedule**
If you plan to release multiple times a day, you will want to keep your master branch stable. If your release schedule is less frequent, you may want to consider using Git tags to tag a branch to a version.

###  Forking Workflow
There are two primary ways people collaborate on GitHub:
1. Shared repository
2. Fork and pull

For an open source project, or for projects to which anyone can contribute, managing individual permissions can be challenging, but a fork and pull model allows anyone who can view the project to contribute. A fork is a copy of a project under an developer’s personal account. Every developer has full control of their fork and is free to implement a fix or new feature. Work completed in forks is either kept separate, or is surfaced back to the original project via a pull request. There, maintainers can review the suggested changes before they’re merged.


The Forking Workflow is fundamentally different than the other workflows discussed in this tutorial. Instead of using a single server-side repository to act as the “central” codebase, it gives every developer a server-side repository. This means that each contributor has not one, but two Git repositories: a private local one and a public server-side one. 

The Forking Workflow is most often seen in public open source projects. 
Developers push to their own server-side repositories, and only the project maintainer can push to the official repository. The developer opens a pull request from the new branch to the 'official' repository. The maintainer to accept commits from any developer without giving them write access to the official codebase. They check to make sure it doesn’t break the project, merges it into their local master branch, then pushes the master branch to the official repository on the server.

In other words, you fork the core repo, work on it. Once some improvement is done, you recommend it to the central repo. 

The main advantage of the Forking Workflow is that contributions can be integrated without the need for everybody to push to a single central repository. 
[Source 1](https://guides.github.com/activities/forking/)
[Source 2](https://www.atlassian.com/git/tutorials/comparing-workflows/forking-workflow)

#### Demo
https://guides.github.com/activities/hello-world/


### GitHub Flow
Branching is a core concept in Git, and the entire GitHub flow is based upon it. There's only one rule: anything in the main branch is always deployable.

Because of this, it's extremely important that your new branch is created off of main when working on a feature or a fix. Your branch name should be descriptive (e.g., ```refactor-authentication```, ```user-content-cache-key```, ```make-retina-avatars```), so that others can see what is being worked on.

By incorporating certain keywords into the text of your Pull Request, you can associate issues with code. When your Pull Request is merged, the related issues are also closed. For example, entering the phrase Closes #32 would close issue number 32 in the repository. For more information, check out our help article.
[Source](https://guides.github.com/introduction/flow/)

### GitLab Flow
It is a way to make the relationship between the code and the issue tracker more transparent. Each change to the codebase starts with an issue in the issue tracking system. When you’re done coding or want to discuss the code, you can open a merge request. When the code is ready, the reviewer will merge the branch into master, creating a merge commit that makes this event easily visible in the future. Using GitLab Flow, teams can deploy a new version of code by merging master into a production branch, enabling them to quickly identify what code is in production. In this workflow, commits only flow downstream, ensuring that everything is tested in all environments.

Broadly speaking, GitLab Flow is broken down into three main areas: feature branch, production branch, and release branch.

A feature branch is where the serious development work occurs. A developer creates a feature or bug fix branch and does all the work there rather than on a master branch. Once the work is complete, the developer creates a merge request to merge the work into the master branch.

The production branch is essentially a monolith – a single long-running production release branch rather than individual branches. It’s possible to create a tag for each deployable version to keep track of those details easily.

The last piece, the release branch, is key if you release software to customers. With every new release, you’ll create a stable branch from master and decide on a tag. If you need to do a patch release, be sure to cherry-pick critical bug fixes first, and don’t commit them directly to the stable branch.

[Source](https://docs.gitlab.com/ee/topics/gitlab_flow.html)