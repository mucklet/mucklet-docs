---
title: "Release v1.71.0 – Client landing page"
linkTitle: "v1.71.0 – Client landing page"
slug: "v1.71.0"
date: 2026-05-07T21:17:58+02:00
description: "A client landing page with realm information, branding, and social links."
release: "v1.71.0"
draft: false
---

Last time we released the Mucklet start page.

This time we've focused on the page you reach when visiting the realm itself.

The visible result may not seem much more than a new design with some additional info. But behind the scenes it has been all about preparing for realm owners to get more control of their world.

So, let's hear it for the new client landing page!

## Features

### Client landing page

The landing page used to be a custom HTML page manually set on each realm. This
has been completely redesigned to page configurable by the realm owner.

It features a _realm image_, _realm icon_, _realm tags_, _social links_, and an _about_ description. All of it may be set by the realm owner on their account page at [Mucklet - Account](https://mucklet.com/account), or for the about text, using `set config about`:

```
set config about = ## Realm
About info may contain _description formatting_.
```

The same info will also be available when you are logged in before waking up your first character, replacing the previous customized HTML page.

{{< github-issues >}}
{{< github-issue repo="mucklet/mucklet-client" issue="475" >}}
{{< /github-issues >}}

### Dynamic progressive web app (PWA)

While we've been able to install Mucklet realms as apps on mobile and desktop devices already, the process has now been automated, generating the needed icons, webmanifest, and service worker file versioning required.

This means that realm owners' configuration will now be applied when the realm is installed as an app.

> [!NOTE]
>
> Once installed on a device such as Android or iOS, it is up to the device to update the icon or realm name if the realm owner changes it.
>
> To force an update, the easiest way is to uninstall and reinstall the app.

### Realm social links

It is now possible for realm owners to add different types of social links, such as to a webpage, forum, or Discord channel, for the realm.

The links will be displayed on the landing page for the realm:

![Realm social links on the landing page.](realm-social-links.png)

## Improvements

### Restyled script describe messages

The `privateDescribe` messages that scripts can send have been restyled to look similar to ordinary `describe` messages.

In addition, `privateDescribe` messages are no longer limited by max targets, nor do they reveal which other characters were targeted by the message.

{{< github-issues >}}
{{< github-issue repo="mucklet/mucklet-client" issue="472" >}}
{{< /github-issues >}}

### Mucklet realm card height limit

The realm cards on the [Mucklet.com](https://mucklet.com) start page have been given a height limit, where the rest of the realm description can be read through scrolling.

{{< github-issues >}}
{{< github-issue repo="mucklet/mucklet-client" issue="469" >}}
{{< /github-issues >}}

### Upgraded client web server

The web server that serves the client application has seen some major upgrades:

- Dynamic reverse proxying with file cache
- Dynamic serving of client version based on realm configuration
- Dynamic serving of realms based on a realm ID (later to be used to handle `*.mucklet.com` wildcard domain requests)

Dynamic means, in this case, that its behavior depends on live realm configuration.

### File service ICO support

The service handling images may now generate _.ico_ file thumbnails.

## Fixes

### Setting profile image could deadlock character

When uploading a profile image, it was possible that the character became "deadlocked", not responding to any action. This would then spread to others who interacted with the deadlocked character. This has been fixed, as well as a similar issue for room profile images.

### Mucklet.com account button on mobile

Devices with smaller screens could not see any account button in the top right corner. This has been fixed.

{{< github-issues >}}
{{< github-issue repo="mucklet/mucklet-client" issue="467" >}}
{{< /github-issues >}}

### Realm backups without archives

After failed backup attempts, the control system could end up with backup entries missing an actual archive, causing the system to repeatedly fail when attempting to prune backups. This has been fixed, and a reconciliation feature has been added to recover from similar situations.
