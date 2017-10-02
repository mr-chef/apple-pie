# GitHub Flow

You can find a short overview in [GitHub flow - User Documentation](https://help.github.com/articles/github-flow/). Continue reading for a more detailed description of the flow.

## A few agreements

- `master` is always the latest stable version of your code (in production)
- we never add commits directly to the `master` branch
- we always use pull requests, even for the smallest change
- for each topic (bug fix, feature, enhancement etc.) we create a new branch
- we try to have short lived pull requests if possible (we may break work down to help with that)
- as we work in our topic branch, we merge `master` into it regularly to make sure we resolve any conflicts from other work that lands into the `master` branch through pull requests our colleagues end up merging

## Some facts

- This is called GitHub Flow, not Git Flow. If you are looking for Git Flow you should search the Internet using `git flow` as keywords.
- GitHub Flow is pretty good for continuous delivery, which works well with web applications (i.e. no distinct versions and releases)

## STEP 0: Clone - You do this once to clone the repository locally (remote operation)

```shell
git clone git@github.com:mr-chef/apple-pie.git
```

## This is the GitHub Flow now

Whenever you want to start a new topic (bug fix, feature, enhancement etc.) you follow this flow:

### STEP 1: Sync - Make sure you have the latest stable master on your computer (remote operation)

```shell
cd applie-pie
git checkout master
git pull origin master
```

Please note that because you never commit directly to `master`, this `pull` will always be fast-forward. You should never have to resolve any conflicts at this point.

### STEP 2: Topic branch - Create your topic branch (local operation)

```shell
git checkout -b improve-recipe
```

Please note, you can do this in two steps. The command above is doing two things:

```shell
git branch improve-recipe
git checkout improve-recipe
```

Using one command will create the branch and switch to it immediately, so that you can start working.

### STEP 3: Work, work, work, work, work (local operation)

This is not Rihanna's song. It's us adding commits to our topic branch.

For every set of changes you want to keep in history as a group, you create a commit:

```
git add file1
git add file2
git commit -m "Improve recipe's XYZ ingredient quantities"
```

### STEP 5: Push your topic branch (remote)

```
git push -u origin improve-recipe
```

The option `-u` is telling Git that the local `improve-recipe` branch is tracking the remote `improve-recipe` branch. This means we'll be able to pull from or push to it without explicitly mentioning the origin and branch names:

```
git push
```

instead of

```
git push origin improve-recipe
```

### STEP 5: Create Pull Request (you do that on github.com)

At some point, you are ready to create a new pull request with your changes. You do that on github.com on your repository page:

[Creating a pull request - User Documentation](https://help.github.com/articles/creating-a-pull-request/)

The idea is you request your topic branch to be reviewed and if approved, merged into `master`. The pull request is where the conversation and code review will take place.

A few tips about creating good pull requests:

- Have a nice title
- Write a brief but complete and concise pull request body
- Have a respecftul, polite, humble tone, and use emoji
- Mention the right people or teams
- Reference any issues this pull request will fix when it's merged (i.e. `fixes #123`)

### STEP 6: More work

As the review produces new ideas, suggestions, corrections, etc., you want to create more commits. You do that by following STEP 3.

### STEP 7: Clean up (remote+local operations)

If your pull request is approved and merged, you should delete the topic branch. Before doing so, you should sync your local `master` branch though:

```
git checkout master
git pull origin master
git branch --delete improve-recipe
```

Enjoy.
