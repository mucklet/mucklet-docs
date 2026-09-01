---
title: "Release v1.74.0 – Account deletion"
linkTitle: "v1.74.0 – Account deletion"
slug: "v1.74.0"
date: 2026-08-31T20:48:00+02:00
description: "Delete your account and schedule all identifying data for deletion."
release: "v1.74.0"
draft: false
---

A long-missing feature has finally been added.
Hopefully, none of you will ever need it. But if you do, for whatever reason, it is now available.

We have also launched this new documentation site, along with a client version-management system to support multi-realm functionality.

## Features

### Account deletion

On the [Mucklet Account - Overview](https://mucklet.com/account/#overview) page, there is now a _Delete account_ button under the _Security_ section:

![Delete Account button in Mucklet Overview.](mucklet-security-delete-account.png)

Clicking it opens a dialog where you confirm using your password or a Google confirmation link:

![Delete Account dialog.](delete-account-dialog.png)

Access to all realms is withdrawn as soon as the account is deleted, and all identifying data is scheduled for deletion after 30 days.

If you try to log in during the 30-day period, you can either restore the account or keep it deleted:

![Account Deleted screen with restore option.](account-deleted.png)

Once the deadline has passed, all identifying data is deleted.

### Mucklet Docs

The site you are currently visiting was created as part of this release.

It provides Mucklet documentation, including release notes, guides, API references, and scripting resources. At launch, it contains only release notes.

Welcome to Mucklet Docs!

## Improvements

### SCSS class cleanup

Several SCSS files defined classes that were not used by any components. Those unused classes have now been removed.

## Fixes

### clearCacheAndReload errors were not handled

If a client update failed while clearing the cache and reloading, the error was not handled correctly. This has been fixed.
[GitHub issue #514 – Failed clearCacheAndReload causes error](https://github.com/mucklet/mucklet-client/issues/514)

### Google account selection was not shown

After signing out of an account linked to Google, choosing Sign in with Google again returned you directly to Mucklet without displaying the Google account-selection screen. This has been fixed; the account-selection screen is now displayed.
