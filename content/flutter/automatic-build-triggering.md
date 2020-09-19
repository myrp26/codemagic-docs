---
title: Build triggers
description: How to enable automatic builds
weight: 3
aliases:
    - '../building/automatic-build-triggering'
---

In order to fully automate your CI/CD pipeline, you can set up automatic build triggering by configuring which branches to track and when to trigger builds.

Build triggers can be configured in **App settings > Build triggers**.

## Tracking specific branches

You can configure the branches to track under **Watched branch patterns**. 

The branches tracked for building are selected by entering branch patterns and including or excluding the matching branches. Note that you can either enter the exact name of the branch to select it or use the wildcard symbols listed in the table below to select more than one branch with one pattern.

![](../uploads/2019/07/branch_patterns-1.png)

The first (i.e. topmost) pattern in the list is applied first. Each following pattern will limit the set of branches further. In the case of conflicting patterns, the latter one will prevail. You can check the targeted branches by clicking the eye icon next to **Watched branch patterns**.

To add a new branch pattern:

1. Navigate to **App settings >** **Build triggers**.
2. Enter a pattern matching the name of one or more branches in the project.
3. Select **Include** or **Exclude** from the dropdown to limit the set of targeted branches by either including or excluding the matching branches.
4. For **pull request builds**, select whether the tracked branch is the **Source** or the **Target** branch of the pull request. This setting has no effect on other types of builds.
5. Click **Add pattern** to save it. You can always edit or delete added patterns.
6. Click **Save** at the end of the section for the changes to take effect.

## Build triggers

Under **Automatic build triggering**, you can select when to trigger builds.

**Trigger on push**. When checked, a build will be started every time you commit code to any of the tracked branches.

**Trigger on pull request update** (not supported for apps from custom sources). When checked, your workflow is run when a pull request is opened or updated to verify the resulting merge commit. 

* For triggering pull requests, you can specify whether each branch pattern matches the **source** or the **target** branch of the pull request.

* If you want to only run tests for pull requests and skip building for platforms, select **Run tests only** under Build > Build for platforms.

**Trigger on tag creation**. When checked, Codemagic will automatically build the tagged commit whenever you create a tag for this app. Note that the watched branch settings have no effect on tag builds.

**Cancel outdated webhook builds**. When checked, Codemagic will automatically cancel all ongoing and queued builds triggered by webhooks on push or pull request commit when a more recent build has been triggered for the same branch. We recommend enabling this feature when you're making several commits, each of which triggers a build.

If you don't enable any automatic build triggers, you can only start builds manually for this workflow.

Codemagic automatically adds webhooks to GitHub, GitLab, and Bitbucket after you have enabled any of the triggers in **App settings > Build triggers >Automatic build triggering**. In the case Codemagic is unable to create a webhook, you would have to [set up webhooks manually](../building/webhooks).