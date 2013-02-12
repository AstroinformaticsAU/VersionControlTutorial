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
continue working, or if your finished with it you can delete it.  We no longer
need this branch, so delete it using::

    % git branch -d risky_idea


Dealing with conflicts
----------------------


Command summary
---------------

