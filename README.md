# Tools for HEY releases

The signed, notarised builds of the [Tools for HEY](https://toolsforhey.com) apps,
by Soules Studio LTD. The source is not public. Issues are open here for bug
reports and questions about the apps, and support@toolsforhey.com reaches the
same person.

Tools for HEY are unofficial native Mac apps built on top of the official HEY CLI.
Not affiliated with 37signals. HEY is a trademark of 37signals.

What the apps keep on your Mac, what they send and what they never do with your
data is in [PRIVACY.md](PRIVACY.md).

## What is here

One GitHub release per app release, tagged by app and version, for example:

- `menubar-0.6.0` for MenuBar for HEY
- `file-1.0.0` for File for HEY, when it ships

Each release carries one asset, the disk image. Downloads for people belong on
[toolsforhey.com](https://toolsforhey.com), which is where the apps are actually
described. This repository is where the file itself is served from.

Each app bundles the official `hey` command line tool from
[github.com/basecamp/hey-cli](https://github.com/basecamp/hey-cli), MIT licensed
by 37signals. The licence text ships inside the app and is shown under
Settings > About.

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
Apple, so macOS opens it without a warning. To check a download yourself, either
compare its SHA-256 with the digest GitHub shows beside the asset, or ask macOS
who signed it:

```
spctl -a -t open --context context:primary-signature -vv MenuBarForHEY-0.6.0.dmg
```

It should answer `accepted` and `source=Notarized Developer ID`. Inside the
image, this should name Soules Studio LTD with team identifier 93XLFSVNZ7:

```
codesign -dv --verbose=2 "/Volumes/MenuBar for HEY/MenuBar for HEY.app"
```

If either check fails, or macOS warns you about a file that came from here, do
not open it, and tell us at support@toolsforhey.com or in an issue.
