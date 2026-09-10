# Tools for HEY releases

The signed, notarised builds of the [Tools for HEY](https://toolsforhey.com) apps.
Nothing else lives here: no source, no issues, no discussion.

Tools for HEY are unofficial native Mac apps built on top of the official HEY CLI.
Not affiliated with 37signals. HEY is a trademark of 37signals.

## What is here

One GitHub release per app release, tagged by app and version:

- `menubar-1.0.0` for MenuBar for HEY
- `file-1.0.0` for File for HEY, when it ships

Each release carries one asset, the disk image. Downloads for people belong on
[toolsforhey.com](https://toolsforhey.com), which is where the apps are actually
described. This repository is where the file itself is served from.

## Why the binaries are here and not on the website

The apps update themselves through Sparkle, which re downloads the whole disk
image on every update for every existing user. Serving that from the website
would attach a metered, uncappable bill to the apps being popular. GitHub does
not meter release downloads.

## Never delete or rename a release asset

Every published Sparkle feed contains the download URL of the disk image it
describes. An installed copy of an app on an old version asks for that exact URL
when it updates. Delete or rename the asset and that copy can never update again,
silently, with no way back except asking the user to download the app by hand.

Assets here are append only. A bad release is superseded by a new one, never
removed.

## Verifying a download

Every disk image is signed with a Developer ID certificate and notarised by
Apple, so macOS opens it without a warning. If macOS warns you about a file that
came from here, do not open it, and tell us at support@toolsforhey.com.
