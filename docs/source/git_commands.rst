*********************
General Git Commands
*********************

Configuration
==============

Setting user name and email:

.. prompt:: bash

   git config --global user.name "name
   git config --global user.email "email"

Simple Commands
================

Initialization of a direction:

.. prompt:: bash

   git init

Simple commands:

.. prompt:: bash

   git add
   git commit
   git status
   git log
   git branch
   git remote -v

Create a new branch:

.. prompt:: bash

   git checkout -b <branch name>

Delete a branch:

.. prompt:: bash

   git branch -d <branch-name>

Delete a branch by force:

.. prompt:: bash

   git branch -D <branch-name>
   
In order to push to the non default branch, i.e., ``main``, do:

.. prompt:: bash

   git push origin branch-name
   
Switch between existing branch

.. prompt:: bash

   git checkout "branch name"

.. tip::

   Head is he most recent change on the branch

Make changes on different branch other than main, then merge branch to the current branch.

.. prompt:: bash

   git merge "other-branch"

Checkout to previous commit:

.. prompt:: bash

   git checkout "hash"          # puts in detached head
   git checkout -b tmp          # saves commit in tmp branch
   git checkout main            # incorporates to main branch
   git merge tmp                # merge changes from tmp to main


Git pull with local changes
==============================

If have local changes, one must either commit the files or stash them.

.. prompt:: bash

   git stash
   git pull
   git stash pop
   

SSH INTERLUDE
==============

Generate SSH keys:

.. prompt:: bash

   ssh-keygen -t ed25519
   ls ~/.ssh

Then add ssh keys by copy paste contents from id_ed25519.pub

Test:

.. prompt:: bash

   ssh -T git@github.com

Fork on Github
===============

1. Clone the original repository

2. Go to Github repository and click fork

3. Click, copy and paste URL in the forked repository

   .. prompt:: bash

      git remote add myfork Forked-URL

4. Click Pull-request on forked webpage and follow instructions


Working with submodules
==========================

Add submodules to the mother directory:

.. prompt:: bash

   git submodule add URL
   git submodule init
   git submodule update
   git commit -m 'msg'
   git push --recurse-submodules=on-demand

Cloning submodules and cloning

.. prompt:: bash

   git clone URL
   git submodule update --init --recursive

Keep update of the file

.. prompt:: bash

   git pull --recurse-submodules

   
