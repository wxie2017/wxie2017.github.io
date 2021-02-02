# -*- mode:org; coding: utf-8 -*-

#+TITLE:     task for git
#+AUTHOR:    Wensheng Xie
#+EMAIL:     wxie@member.fsf.org
#+LANGUAGE:  en
#+OPTIONS: H:2 num:nil toc:nil \n:nil @:t ::t |:t ^:{} _:{} *:t TeX:t LaTeX:t
#+STYLE: <link rel="stylesheet" type="text/css" href="org.css" />
#+LATEX_CLASS: myclass
#+LATEX_CLASS_OPTIONS: [a4paper]
#+ATTR_LATEX: width=0.38\textwidth wrap placement={r}{0.4\textwidth}
#+ATTR_LATEX: :float multicolumn
#+REVEAL_TRANS: None
#+REVEAL_THEME: Black
#+TAGS: @work(w) @home(h) @road(r) laptop(l) pc(p) { @read : @read_book @read_ebook }
#+ATTR_ORG: :width 30
#+ATTR_HTML: width="100px"
#+EXPORT_SELECT_TAGS: export
#+EXPORT_EXCLUDE_TAGS: noexport
#+STARTUP: fold

* tasks for git
** [2020]
*** [2020-05]
**** [2020-05-24 日]
***** DONE handle a project for git [10/10]
      DEADLINE: <2020-05-24 日>
[[https://kbroman.org/github_tutorial/][github tutorial]]
 - [X] Your first time with git and github
    Get a github account.
    Download and install git.

    Set up git with your user name and email.

        Open a terminal/shell and type:
#+BEGIN_SRC shell
        $ git config --global user.name "Your name here"
        $ git config --global user.email "your_email@example.com"
#+END_SRC

        (Don’t type the $; that just indicates that you’re doing this at the command line.)
        I also do:
#+BEGIN_SRC shell
        $ git config --global color.ui true
        $ git config --global core.editor emacs
#+END_SRC

        The first of these will enable colored output in the terminal; the second tells git that you want to use emacs.
        Set up ssh on your computer. I like Roger Peng’s guide to setting up password-less logins. Also see github’s guide to generating SSH keys.
        Look to see if you have files ~/.ssh/id_rsa and ~/.ssh/id_rsa.pub.

        If not, create such public/private keys: Open a terminal/shell and type:
#+BEGIN_SRC shell
        $ ssh-keygen -t rsa -C "your_email@example.com"
#+END_SRC

        Copy your public key (the contents of the newly-created id_rsa.pub file) into your clipboard. On a Mac, in the terminal/shell, type:
#+BEGIN_SRC shell
        $ pbcopy < ~/.ssh/id_rsa.pub
#+END_SRC

    Paste your ssh public key into your github account settings.
        Go to your github Account Settings
        Click “SSH Keys” on the left.
        Click “Add SSH Key” on the right.
        Add a label (like “My laptop”) and paste the public key into the big text box.
        In a terminal/shell, type the following to test it:
#+BEGIN_SRC
        $ ssh -T git@github.com
#+END_SRC

        If it says something like the following, it worked:
        Hi username! You've successfully authenticated, but Github does
        not provide shell access.
 - [X] A new repo from scratch
#+BEGIN_SRC shell
#    Create a directory to contain the project.
#    Go into the new directory.
     git init
#    Write some code, create a .gitignore file also.
     git add [files] # add the files (see the typical use page).
     git commit
#+END_SRC
 - [X] A new repo from an existing project
#+BEGIN_SRC shell
#    go to the directory containing the project.
     git init
     git add [all files] # add the files (see the typical use page).
     touch .gitignore
     git add .gitignore
     git commit
#+END_SRC
 - [X] connect it to github.com
You’ve now got a local git repository. You can use git locally, like that, if
you want. But if you want the thing to have a home on github, do the following.

    Go to github.
    Log in to your account.
    Click the new repository button in the top-right. You’ll have an option there to initialize the repository with a README file, but I don’t.
    Click the “Create repository” button.

Now, follow the second set of instructions, “Push an existing repository…”
#+BEGIN_SRC shell
$ git remote add origin git@github.com:username/new_repo
$ git push -u origin master
#+END_SRC

Actually, the first line of the instructions will say
#+BEGIN_SRC shell
$ git remote add origin https://github.com/username/new_repo
#+END_SRC

But I use git@github.com:username/new_repo rather than
https://github.com/username/new_repo, as the former is for use with ssh (if you
set up ssh as I mentioned in “Your first time”, then you won’t have to type
your password every time you push things to github). If you use the latter
construction, you’ll have to type your github password every time you push to
github.
 - [X] Contribute to someone's repository
Say you want to contribute changes to someone else’s repository (eg, this one).
    Go to the repository on github. (Say it’s by myfriend, and is called the_repo, then you’ll find it at https://github.com/myfriend/the_repo.)
    Click the “Fork” button at the top right.
    You’ll now have your own copy of that repository in your github account.
    Open a terminal/shell.
    Type
#+BEGIN_SRC shell
    $ git clone git@github.com:username/the_repo
#+END_SRC

    where username is your username.
    You’ll now have a local copy of your version of that repository.
    Change into that project directory (the_repo):
#+BEGIN_SRC shell
    $ cd the_repo

# create a new branch to store any new changes
git branch my-branch

# switch to that branch (line of development)
git checkout my-branch

# make changes, for example, edit `file1.md` and `file2.md` using the text editor

# stage the changed files
git add file1.md file2.md

# take a snapshot of the staging area (anything that's been added)
git commit -m "my snapshot"

# push changes to github
git push --set-upstream origin my-branch
#+END_SRC

    Add a connection to the original owner’s repository.
#+BEGIN_SRC shell
    $ git remote add myfriend git://github.com/myfriend/the_repo
#+END_SRC

    Note the distinction between git@github.com: in the first case and
    git://github.com/ in the second case. I’m not sure why these need to be the
    way they are, but that’s what works for me.
    Also note the first myfriend does not need to be the same as the username of myfriend. You could very well choose:
#+BEGIN_SRC shell
    $ git remote add repo_nickname git://github.com/myfriend/the_repo
#+END_SRC

    To check this remote add set up:
#+BEGIN_SRC shell
    $ git remote -v
#+END_SRC

    Make changes to files.
#+BEGIN_SRC shell
    git add and git commit those changes
    git push them back to github. These will go to your version of the repository.
#+END_SRC

    Note: if you get an error like:
    error: src refspec master does not match any.
    error: failed to push some refs to 'git@github.com:username/the_repo'

Then try git push origin HEAD:gh-pages (see stackoverflow.). Typing git show-ref can show what reference to put after HEAD.
    Go to your version of the repository on github.
    Click the “Pull Request” button at the top.
    Note that your friend’s repository will be on the left and your repository will be on the right.
    Click the green button “Create pull request”. Give a succinct and
    informative title, in the comment field give a short explanation of the
    changes and click the green button “Create pull request” again.
 - [X] Pulling others’ changes
Before you make further changes to the repository, you should check that your
version is up to date relative to your friend’s version.
Go into the directory for the project and type:
#+BEGIN_SRC shell
$ git pull myfriend master
#+END_SRC

This will pull down and merge all of the changes that your friend has made.
Now push them back to your github repository.
#+BEGIN_SRC shell
$ git push
#+END_SRC
 - [X] Handling pull requests
Using the github website:
    Go to your version of the repository.
    Click on “Pull Requests” at the top.
    Click on the particular request.
    You’ll see their comments on the pull request, and can click to see the exact changes.
    If you want them to make further changes before you merge the changes into your repository, add a comment.
    If you hate the whole idea, just click the “Close” button.
    If you want to merge the changes into your repository, click the “Merge pull request” button.
    Your github repository will now be fixed, but you’ll want to get them into your local repository, too.
    Open a terminal/shell, and type
#+BEGIN_SRC shell
    $ git pull
#+END_SRC

Using the command line
You don’t have to use the github website for this.
    Open a terminal/shell.
    Go into the directory for your project.
    Add a connection to your friend’s version of the github repository, if you haven’t already.
#+BEGIN_SRC shell
    $ git remote add myfriend git://github.com/myfriend/the_repo
#+END_SRC

    Pull his/her changes.
#+BEGIN_SRC shell
    $ git pull myfriend master
#+END_SRC

    Push them back to your github repository.
#+BEGIN_SRC
    $ git push
#+END_SRC

    The pull request on github will be automatically closed.
 - [X] Handling merge conflicts
Sometimes, though, after you do
#+BEGIN_SRC shell
$ git pull myfriend master
#+END_SRC

You’ll get a message like

Auto-merging README.md
CONFLICT (content): Merge conflict in README.md
Automatic merge failed; fix conflicts and then commit the result.

If you open the offending file in a text editor, you’ll find an indication of the bits that are different, something like this:

<<<<<<< HEAD
A line in my file.
=======
A line in my friend's file
>>>>>>> 031389f2cd2acde08e32f0beb084b2f7c3257fff

Edit the bits from <<<<<<< to >>>>>>>, to make the file just as you want it.
Then do git add, git commit, and git push.
 - [X] Amend the last commit message
It’s easy to fix just the message for the last commit:
#+BEGIN_SRC shell
$ git commit --amend -m "New commit message"
#+END_SRC

Or leave off the -m "New commit message" and type the message in the text editor that opens.
 - [X] Delete a repository
To delete your repository on Github:

    View it in a web browser (say https://github.com/myaccount/myrepo)

    Click on “Settings” (below the Unwatch/Star/Fork buttons on the right)

    Scroll down to “Danger Zone” and click “Delete this Repository”

    Confirm the name of the repository

On your local machine, the .git directory/folder within your repository’s
directory contains the full git history. If you delete that directory, it will
no longer be a git repository but will go back to being a regular project
directory. (You could start over by typing git init, adding files with git add,
and then git commit.)
