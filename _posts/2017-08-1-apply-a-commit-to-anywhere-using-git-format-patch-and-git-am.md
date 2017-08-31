---
layout: post
title:  "Apply a git commit to anywhere else using git format patch and git am"
categories: git git-am git-format
published: false
---

Often times I find myself working with stable branches of code such as an
official release so that experiments are reproducible. I also need to modify
the code to suit the experiments.
But sometimes a feature or bug fix is merged into the master that is needed in my stable branch. This is illustrated as follows:


{% highlight git %}
Master:
-----A----B----C----D<----HEAD
          |
          E<---Stable

My Experiment:
-----A----B----E----MyOwnCommits<----HEAD
{% endhighlight %}

If I want the changes made in D to be applied to E, first I need to
get the changes using ``git format-patch``. I simply get the changes
that D introduced:

{% highlight git %}
git format-patch HEAD~
0001-commit-message.patch
{% endhighlight %}


My experiment is deployed in a server so I scp my 0001-commit-message.patch to
the server. According to the manpage ``--3way`` means git will use a 3-way merge
when the patch does not apply cleanly as is highly likely with our scenario.

If there are any conflicts then they can be resolved and added.
After which we can continue with ``git am --continue``.

{% highlight git %}
git am --3way 0001-commit-message.patch
<resolve any conflicts>
git add <resolved files>
git am --continue
{% endhighlight %}

{% highlight git %}
git format-patch SHA1 SHA2
0001-commit-message.patch
{% endhighlight %}

If we simply use git diff and git apply
