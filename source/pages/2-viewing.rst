.. highlight:: console

Viewing and comparing commits
=============================

The commit history
------------------

The command ``git log`` displays the commit history of the current branch.  If
you try it in your ``dummy_paper`` directory you should see something like the
following::

    commit 2983eadcbb3c5b198906c252bc5ee3ff2a99f572
    Author: Han Solo <jbloggs@jabbaspalace.edu.au>
    Date:   Tue Feb 12 10:16:23 2013 +1100

        Add section "A New Hope" and appendix.tex.

    commit ef5ca0a7d216a57aea08d2227e167f38d31277bc
    Author: Han Solo <jbloggs@jabbaspalace.edu.au>
    Date:   Mon Feb 11 14:54:05 2013 +1100

        Add basic structure of master.tex.

As you can see ``git log`` provides the unique reference (SHA-1 checksum) for
each commit, the author name and email address, as well as the date and commit
message.  The entries are listed in reverse chronological order (i.e.  the most
recent commit first).

There are a whole host of flags and arguments you can pass to ``git log`` to
change what information is presented and how it looks.  For example, try typing::

    % git log --pretty=format:"%h %s <%an>" --graph

The result should be something like this::

    * 2983ead Add section "A New Hope" and appendix.tex. <Han Solo>
    * ef5ca0a Add basic structure of master.tex. <Han Solo> 

To investigate all the different options for formatting your log output, try
looking at the help for the ``log`` command::

    % git help log

.. tip::

    The ``git help`` command can be used to get the documentation for almost
    every Git command.



Comparing commits
-----------------

Often we want to compare (or "difference") commits to see how things have
changed.  To do this we use the ``git diff`` command.  For example, to see how
our paper has changed between the most recent commit and our first commit **I**
would type::

    % git diff ef5ca0a

Your commit reference will be different to mine however, and so you must
subsititue the appropriate reference in place of ``ef5ca0a``.  Remember, you
can get this reference using the ``git log`` command as outlined above.

.. highlight:: diff

Once you run ``git diff`` successfully, you will see something like this::

    diff --git a/appendix.tex b/appendix.tex
    new file mode 100644
    index 0000000..e69de29
    diff --git a/master.tex b/master.tex
    index 0f8e62c..7c3dbaf 100644
    --- a/master.tex
    +++ b/master.tex
    @@ -8,4 +8,7 @@
     \section{Introduction}
     A long time ago in a galaxy far, far away...
     
    +\section{A New Hope}
    +That's no moon, that's a battle station.
    +
     \end{document} 

.. highlight:: console

The ``+`` signs show text which has been added since our first commit, and any
``-`` signs would indicate text which has been removed.  At the top of the diff,
we can also see that we have added the ``appendix.tex`` file.

By specifying only one commit reference when calling ``git diff`` we actually
implicity ran::

    % git diff ef5ca0a HEAD

``HEAD`` is a shortcut for the commit reference pointing to the most recent
relevant commit.  To access the second most recent commit we can use the
shortcut ``^HEAD``.  These shortcuts are handy to remember when comparing
commits.

``git diff`` can also be used to see how the current state of files have changed
since the last commit.  To do this simply run the command with no arguments.


.. topic:: Exercise 2a

    Add a scentence to the section "A New Hope" of ``master.tex`` but don't
    commit the change.  Now try running::

        % git diff

    and make sure you understand the results.


Another useful way to view the commit history of your repository is to use the
``gitk`` GUI program which is packaged with Git.  This program displays both the
commit history and relevant diffs all together.

.. image:: /_static/gitk.jpg
   :align: center
   :width: 100%


