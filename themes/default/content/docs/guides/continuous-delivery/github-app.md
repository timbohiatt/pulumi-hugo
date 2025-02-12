---
title: Pulumi GitHub App
meta_desc: Pulumi's GitHub app integrates the results of Pulumi stack updates. It
           will show you any potential infrastructure changes on Pull Requests and commit Checks.
menu:
    userguides:
        parent: cont_delivery
        weight: 1

aliases:
- /docs/reference/cd-github/
- /docs/console/continuous-delivery/github-app/
---

Pulumi's GitHub app integrates the results of Pulumi stack updates with GitHub. Once installed and
configured, it will show you any potential infrastructure changes on Pull Requests and commit Checks.
[See below](https://github.com/apps/pulumi) for information on how to install the Pulumi GitHub app
into your organization.

## Features

The Pulumi GitHub app will automatically add comments to Pull Requests with the results of any
stack changes. This includes a summary of how many resources were created, updated, and/or deleted.
This allows you to quickly see the changes caused by your Pulumi program without needing to leave
GitHub's Pull Request view, with a link to the richer details available on the
[Pulumi Service](https://app.pulumi.com).

![Comment on Pull Request](/images/docs/github-app/pr-comment.png)

Beyond Pull Request comments, the GitHub application also integrates with GitHub's [Checks API](https://blog.github.com/2018-05-07-introducing-checks-api/).
This provides even more detail about any resource changes, including the full update log.

![Results on GitHub Check](/images/docs/github-app/checks-detail.png)

## Installation and Configuration

Pulumi's GitHub workflow integration is a GitHub application.

<a class="btn" href="https://github.com/apps/pulumi" target="_blank">
    Install Pulumi GitHub App
</a>

The Pulumi GitHub application is installed into a specific GitHub organization, and you can
configure it to only be used by certain repositories.

![Installation Page](/images/docs/github-app/installation.png)

![Configuration Page](/images/docs/github-app/org-configuration.png)

The Pulumi GitHub app will report Stack operations on GitHub commits and pull
requests against repositories it has access to. You can also uninstall the
GitHub application at any time without impacting your stacks or other
Pulumi-managed resources.

## CI Integration

The Pulumi GitHub application will work with any CI/CD system. See our
[Continuous Delivery]({{< relref "/docs/guides/continuous-delivery" >}}) guide for information on how to
integration Pulumi with whatever system you currently use.

Once installed in your organization, any `pulumi preview` or `pulumi up` that is run in your CI
system will have its results reported back to GitHub.

## GitHub UI

There are two places that Pulumi update results will be displayed: Pull Requests or commit Check.

All Pulumi stack updates are reported to the GitHub Checks API. You can see the results of each
commit check by "Code" tab's "Commits" page, and then clicking the ✅ or ❌ icon.

For Pull Requests, you can see the checks on the "Checks" tab as well.

![GitHub Checks Tab](/images/docs/github-app/checks.png)

Every stack that was impacted by the CI job is then listed in the left.

![GitHub Check Result](/images/docs/github-app/checks-detail.png)

If the CI build originated from a pull request, e.g. the Travis CI job had type `pull_request`,
then the results will be placed as a comment on the Pull Request as well.

![Comment on Pull Request](/images/docs/github-app/pr-comment.png)
