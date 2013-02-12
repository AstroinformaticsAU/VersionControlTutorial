.. highlight:: console

Branches
========

What is a branch?
------------------

Branches allow you to diverge from your current development and try something
new without altering the history of your main work.  For example, you could
implement a new code feature whilst leaving the fully functional (hopefully
working and tested) code intact for others to checkout.

In Git, branching is generally quick, flexible and simple.  It is a fantastic
way to test out ideas, try new things and safely develop your repository.  This
is especially true when collaborating with other people...


Creating branches
-----------------

All new repositories, by default, start on a branch called ``master`` (you
should see this name if you again run ``git status``).

Let's now create a new branch called ``risky_idea`` by typing the following
command inside of our ``dummy_paper`` directory::

    % git branch risky_idea

Well that was simple!  However, if a quick check of ``git status`` shows that we
are still on the ``master`` branch.  In order to start working with our new
branch we need to perform a ``checkout``; This moves our current "HEAD" (this is
what Git calls the pointer to the code version we are working with) to the
branch ``risky_idea``::

    % git checkout risky_idea

Running ``git status`` now should show that you are on the ``risky_idea``
branch.

.. topic:: Exercise 2a

    .. highlight:: latex

    Add another section to ``master.tex`` with the following::
    
        \section{The Empire Strikes Back}
        Laugh it up fuzz-ball!...
    
    Then stage and commit your changes.


.. highlight:: console



Viewing commit differences
---------------------------

Now that we know how to see the commit history  


Command summary
----------------

+--------------------------------+--------------------------------------------------+
| **Command**                    |  **Description**                                 |
+--------------------------------+--------------------------------------------------+
| ``git branch``                 |  Create a new branch.                            |
+--------------------------------+--------------------------------------------------+
| ``git checkout``               |  Checkout a branch/commit.                       |
+--------------------------------+--------------------------------------------------+
| ``git log``                    |  View the commit history for the current branch. |
+--------------------------------+--------------------------------------------------+
| ``git diff <commit> <commit>`` | Compare (difference) two commits.                |
+--------------------------------+--------------------------------------------------+

