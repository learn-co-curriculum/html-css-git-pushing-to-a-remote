# Git - Pushing To A Remote

## Overview

The Simons Stamp Collection Saga continues... In this lesson we will learn the benefits of pushing our code to remote servers.

This lesson continues from the prior one and will build on the files and folders that you've already created. Make sure you do all the lessons in this unit in order!
## Objectives

1. List the benefits of storing code remotely
2. Create a new remote repository
3. Add new remotes to your local repository
4. Push commits to your remote origin

## You'z A Real Fine Repo, Won't You Back That Thing Up!

Watch the video below if you are unfamiliar with Git. We will be using Git to access course materials and to share and collaborate on project code throughout this course. After watching the video you may use the text below to review all of the topics discussed in the video.

**Note** that the video uses your computer's terminal, but in this course, you'll be using the Learn IDE and the Git commands that you learn in this lesson will work the same way on it as it does on your terminal.

<iframe width="640" height="480" src="https://www.youtube.com/embed/y8ZBIp2moDY?rel=0" frameborder="0" allowfullscreen></iframe>

### Benefits of Syncing With A Remote

So far, we have learned how to create new repositories, stage files, and commit our changes, as well as how to log our commits and even how to reset back to a previous commit. Now let's look at a way to safely backup our code and place it in a remote location that we can easily share with others. Murphy's Law States that "anything that can go wrong, will go wrong". Sometimes our hardware breaks, and when we have important code it's not enough to keep a local copy. By making our local repository (the one that's on your computer) aware of a remote location we can push our code up to, we ensure that if anything happens to our copy there is another copy elsewhere. As mentioned this also creates an ideal way to share our code with others.

### Using Github to create 

To start out let's take a look at Github.com. As their website states "GitHub is how people build software". This site offers free public and paid private space to host Git repositories online. It also gives us tools for making copies of others' code, communicating and commenting on code, and posting issues about code.

Let's start out by creating a new repository on Github to sync to our local repo. After logging in, click the **+** plus symbol located at the top right navigation. Then select **new repository**. Under repository name let's fill in the same name as our local repo `simon-stamp-collection`. Then click **Create Repository**. Then under Quick Setup copy the SSH url and head back to the terminal in your Learn IDE and type: `git remote add origin <paste your SSH url here>` for example my command was: **git remote add origin git@github.com:jongrover/simon-stamp-collection.git**. Then press return. What we did here was link our local repository to a new remote labeled "origin" and pointed it to the SSH location of the remote repository on Github. The label "origin" is merely a naming convention that refers to your personal copy of the remote repository.

*Note: I used an SSH url to link to my remote. We could have also used HTTP by clicking the button for HTTP from the Quick Setup Section on the Github page after creating the repo. HTTP requires that you insert your username and password each time you push or pull to/from a remote. The advatage of SSH is that Github identifies you have permission to push and pull based on the matching of public and private SSH keys (sort of a digital handshake). This way there is no need to enter a username or password to push and pull. Most likely your SSH keys have already been set up during your environment set up for this course. If not, you can follow the instructions from the resource links at the bottom of this lesson.* 

Now our local repo (repository) is aware of a remote location we can read and write to. This will allow us to easily back up our commits and share our code with others.

### Listing Remotes

We can create as many remotes as we like for a given repo. Sometimes it is nice to list them. In Terminal, type the command `git remote -v` and press return. This command lists all remotes and the `-v` flag "verbose" will list the url location our remote label "origin" is pointing to. This command will return a response such as the following:

```shell
origin  git@github.com:jongrover/simon-stamp-collection.git (fetch)
origin  git@github.com:jongrover/simon-stamp-collection.git (push)
```

This indicates a single remote called "origin" that we can read (fetch) from and write (push) to.

### The Hidden .git Folder

Inside all repositories there lives a hidden **.git** folder. We can see it by typing `ls -a` to list and display all hidden files and folders. We can see it is present inside our **simons-stamp-collection** folder. Let's open this folder up inside of our code editor. Then click to open the **config** file. It should look something like this:

```shell
[core]
    repositoryformatversion = 0
    filemode = true
    bare = false
    logallrefupdates = true
    ignorecase = true
    precomposeunicode = false
[remote "origin"]
    url = git@github.com:jongrover/simon-stamp-collection.git
    fetch = +refs/heads/*:refs/remotes/origin/*
[branch "master"]
    remote = origin
    merge = refs/heads/master
```

This file contains the configuration details for our repo. Note that here we can also see the remotes such as `[remote "origin"]` which is pointing to `url = git@github.com:jongrover/simon-stamp-collection.git`. If we ever wanted to change the location this remote is pointing to we could simply replace the url following the `url =`, save the file and exit. In our case everyhting appears as it should so we will close out this file for now and head back to Temrinal.

### Push

Now that we have added a remote using the `git remote add <Your SSH URL>`. We now have the ability to write our local code up to our remote. To do so we use the push command. In Terminal type: `git push -u origin master` then press return. This should output a response such as the following.

```shell
Counting objects: 6, done.
Delta compression using up to 4 threads.
Compressing objects: 100% (4/4), done.
Writing objects: 100% (6/6), 591 bytes | 0 bytes/s, done.
Total 6 (delta 0), reused 0 (delta 0)
To git@github.com:jongrover/simon-stamp-collection.git
 *[new branch]    master -> master
Branch master set up to track remote branch master from origin.
```

Let's look over our command: `git push -u origin master` The command `push` accepts flags (options), then the remote name, then the branch name. Here our option -u sets up tracking between our local branch and our remote branch so we know if one is ever ahead or behind the other in terms of commits. This is recommended only to do once the first time we push new branches. After that we can leave it out for existing branches as simply `git push origin master`. THe next argument is the remote name "origin" and finally the branch we are pushing "master".

Now if you head back to this repository in your browser at Github.com and refresh the page you will see our files appears in a file list and below our README is displayed. Neat! You just wrote your work to a remote. :)

From Github you can share the the url of this remote repository with others, view all the commits to see changes in the files, and post issues. 

## Summary

- Storing code remotely saves us from losing our code if our hardware ever fails.
- To create a new remote repository from scratch go to github and click the + plus icon from the top navigation.
- To teach our local repo about a remote we wish to sync with use the command `git remote add origin <paste in SSH url here>`.
- To push our code after adding and commiting type `git push <remote> <branch>`.

## Resources

- [Git SCM Docs - Push](https://git-scm.com/docs/git-push)
- [Git Cheatsheet](https://www.git-tower.com/blog/content/posts/54-git-cheat-sheet/git-cheat-sheet-large01.png)
- [Git Best Practices](https://www.git-tower.com/blog/content/posts/54-git-cheat-sheet/git-cheat-sheet-large02.png)
- [Github - Generating An SSH Key](https://help.github.com/articles/generating-an-ssh-key/)

<p class='util--hide'>View <a href='https://learn.co/lessons/html-css-git-pushing-to-a-remote'>HTML CSS Git Pushing to a Remote</a> on Learn.co and start learning to code for free.</p>
