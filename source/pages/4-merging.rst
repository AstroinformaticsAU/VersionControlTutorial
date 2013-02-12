.. highlight:: console

Merging and conflicts
=====================

At this stage we have two branches, ``master`` and ``risky_idea``.  Let's
imagine that we have continued to work away on the ``risky_idea`` branch,
committing our changes as we go...


Merging
-------

At some stage we will want fold our changes in the ``risky_idea`` branch back
into the ``master`` branch.  We do this by "merging" the ``risky_idea`` branch
into ``master``.

First we checkout the ``master`` branch::

    % git checkout master

If you run ``git log`` you should see that none of your commits to the
``risky_idea`` branch are present.  You can further confirm this by looking at
the contents of ``master.tex``; The section "The Empire Strikes Back" shouldn't
be present.

Now merge ``risky_idea`` into our current branch using the following command::

    % git merge risky_idea

If everything runs smoothly, running ``git log`` should show your commits from
the ``risky_idea`` branch.

At this stage you could either checkout the ``risky_idea`` branch again and
continue working, or if your finished with it you can delete it.  

We no longer need the ``risky_idea`` branch, so delete it using::

    % git branch -d risky_idea


Dealing with conflicts
----------------------

Typically, as above, a ``git merge`` will progress smoothly with Git
automatically working out how to merge the two branches.  Occasionally however,
this is not the case.  In particular if we have made changes to two different
branches which directly conflict with each other, then a merge will require us
to tell Git which change is the correct one.  We will now engineer such a
situation...

First create a new branch called ``episode5`` and check it out::

    % git branch episode5
    % git checkout episode5

.. tip::

    In situations where you want to create a new branch and immediately check it
    out (as above) you can use the follwoing shortcut::

        % git checkout -b <branch_name>

.. highlight:: latex

Now add another section to ``master.tex`` with the following::

    \section{Revenge of the Jedi}
    That blast came from the Death Star! That thing's operational!

.. highlight:: console

Commit your changes::

    % git add master.tex
    % git commit

Now we have a new branch with a new commit that adds a section to our paper.
However, what if we now go back to the ``master`` branch and try to add the same
section but with a different name...

First checkout ``master``::

    % git checkout master

.. highlight:: latex

Then edit ``master.tex``, this time with the text::

    \section{Return of the Jedi}
    That blast came from the Death Star! That thing's operational!

.. highlight:: console

Again, commit your changes::

    % git add master.tex
    % git commit

Now our two branches ``master`` and ``episode5`` have commits in them which
directly conflict.  Running the merge command from the ``master`` branch will
flag this conflict and Git will ask us for help.  Try it now::

    % git merge episode5

and you should be presented with the following message::

    Auto-merging master.tex
    CONFLICT (content): Merge conflict in master.tex
    Automatic merge failed; fix conflicts and then commit the result.

.. highlight:: latex

This tells us that a conflict has occurred in ``master.tex``.  

To resolve the conflict open up ``master.tex`` in your favorite editor.  The
offending section will look something like this::

    <<<<<<< HEAD
    \section{Return of the Jedi}
    =======
    \section{Revenge of the Jedi}
    >>>>>>> episode5

Everything between the lines ``<<<<<<< HEAD`` and ``=======`` are what exists in
the ``HEAD`` commit (the tip of the ``master`` branch in this case).  Between
the lines ``=======`` and ``>>>>>>> episode5`` is what exists in our
``episode5`` branch.

In order to resolve the conflict, pick which of the section headings we want to
use and remove the other lines (including the ``=======`` line and those lines
starting with ``>`` or ``<`` symbols.  In our case we want to keep the section
title from the ``master`` branch, and so we need to leave only that line::

    \section{Return of the Jedi}

.. highlight:: console

After you have edited and saved ``master.tex``, finish the merge by staging and
committing your results::

    % git add master.tex
    % git commit

The commit message will be auto-populated for you, and so there is no need to
edit it.


Command summary
---------------

+--------------------------------+--------------------------------------------------+
| **Command**                    |  **Description**                                 |
+--------------------------------+--------------------------------------------------+
| ``git merge``                  | Merge branches and commits.                      |
+--------------------------------+--------------------------------------------------+
| ``git branch -d``              | Delete a branch.                                 |
+--------------------------------+--------------------------------------------------+

