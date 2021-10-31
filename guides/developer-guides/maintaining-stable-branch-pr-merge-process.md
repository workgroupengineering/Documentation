---
description: How to deal with merging PR and maintain a stable branch
---

# Maintaining Stable Branch

{% hint style="warning" %}
This Process MUST be followed during any period that `master` branch is allowing breaking changes.
{% endhint %}

In order to maintain a stable branch it is required to follow a process on every PR that gets merged to ensure they are back ported.

{% hint style="warning" %}
For a PR to be back ported it MUST reach the following criteria

* Contain no breaking API changes, (changing signatures, removing a method, etc)\
  Additional overloads, methods, classes and extension methods are allowable.
* Be suitable for the stable release, by default most changes and features should be considered.
{% endhint %}

Provided the criteria are met:

1. Merge the PR to master generating a merge commit.&#x20;
2. i.e. "Merge pull request #5797 from AvaloniaUI/double-tapped-event-args"

At this point the git tree should look similar to this.

![](<../../.gitbook/assets/image (6).png>)

Now we need to get the new PR merged into the stable branch.

{% hint style="warning" %}
Pay careful attention here, we don't just merge into the stable branch!
{% endhint %}

* Checkout the `stable/0.10.x` branch.
* Cherrypick the merge commit from master.

The git tree should look like this now.

![](<../../.gitbook/assets/image (13).png>)

Please also use the `backport-candidate` and `backported 0.10.x` labels on the PRs themselves.
