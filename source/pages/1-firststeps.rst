.. highlight:: console

First Steps
===========

I'll assume that you already have git installed and setup on your system.  If
not then probably the easiest way to achieve this is to download an installer
from `here <http://git-scm.com/downloads>`_.

In what follows, we will use writing and collaborating on a LaTeX paper as an
example project... 

Creating a repository
---------------------

First of all we need to start our paper by creating a repository. 

Decide where you would like your paper to be stored and ``cd`` to that
directory.  Once there, create a new directory for the paper::

    % mkdir dummy_paper
    % cd dummy_paper

Now initialise your empty repository by typing::

    % git init

To check everything has been successful type::

    % ls -a

and you should see the directory ``.git``.  This special folder is where Git
will store and manage the version control history of your project.  

.. warning::

    Unless you are familiar with Git it is generally best to avoid touching the
    ``.git`` folder or it's contents.



Adding files
------------

Now we have our fresh Git repository.  The next step is to start adding files!

Use your editor of choice to start a LaTeX file named ``master.tex`` in your
project directory (``dummy_paper``).

.. note::

    If your unsure what editor to use you can try ``nano`` for this simple
    exercise::

    % nano master.tex

    To save and exit the file press ``Control-x``, then answer the question
    with the ``y`` key, before finally accepting the filename presented by
    hitting ``Enter``. 

.. highlight:: latex

Add the following to your file and save your changes::

    \documentclass{article}   

    \title{A dummy paper}

    \begin{document}
    \maketitle

    \section{Introduction}
    A long time ago in a galaxy far, far away...

    \end{document}

.. highlight:: console

Finally "stage" your ``master.tex`` file to the repository's list of changes
using the following command::

    % git add master.tex



Committing changes
------------------

At this point, if you type the command::

    % git status

you should see something like the following::

    # On branch master
    #
    # Initial commit
    #
    # Changes to be committed:
    #   (use "git rm --cached <file>..." to unstage)
    #
    #	new file:   master.tex
    #

This tells us that we have changes to our repository (here the creation of a new
file called ``master.tex``) that need to be "committed".

Committing changes to the repository is the key step of version control.  This
is where we save a snapshot of the current state of all tracked files.  To
commit our current changes type::

    % git commit

This will bring up your default editor to allow you to provide a "commit
message".  On the **first line** of the file write the following commit
message::

    Add basic structure of master.tex

then save and exit.

That's it!  We have now created a repository, added our first file and committed
our changes.

.. tip::

    Writing good commit messages will make your life much easier in future when
    trying to track down particular changes.  The first line should be a short
    (i.e. less than 80 characters), descriptive message that makes it clear what
    the relevant changes being committed are.  If more detail is required then
    leave a blank line and add a longer more descriptive message there.

.. todo::

    Add an exercise here where the students make further changes to master.tex.

