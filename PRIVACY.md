# Your data

How the Tools for HEY apps handle what is yours. Written for MenuBar for HEY, and
File for HEY will get its own section when it ships. Last updated 22 September
2026.

This is the short form. The full statement, with every event the app can send
listed by name, is at
[toolsforhey.com/menubar/privacy](https://toolsforhey.com/menubar/privacy), and
where the two ever differ, that page is the one that counts.

Tools for HEY are unofficial native Mac apps built on top of the official HEY CLI,
by Soules Studio LTD. Not affiliated with 37signals. HEY is a trademark of
37signals.

## Your sign in

The apps read your mail through the official `hey` command line tool, which runs
inside the app as a child process. Your sign in lives in the macOS Keychain and
the tool's own config folder, both managed by the tool. The app never reads
them and never stores them anywhere else. The app never talks to app.hey.com
itself.

## What stays on your Mac

The app keeps a cache of the last Imbox and Screener page it showed, so the
popover opens with something rather than nothing. It holds sender names and
addresses, subjects and summaries. It is readable by your user only, and signing
out deletes it. Beside it are your settings and a random install id.

Nothing about your mail leaves your Mac except the traffic between the tool and
HEY, as with any HEY client.

## Usage events and crash reports

If usage events are on, and they are on by default, the app sends PostHog in the
EU the name of an event such as the popover opening, a detail or two such as where
a thread was moved, the app version and build, the macOS version and the install
id. A crash sends a stack trace with the same facts. Never your mail, your name,
your address or your account, and no profile is ever built. PostHog is set to
discard the client IP address, so your address is not stored with the events.

Switch it off under Settings > Privacy. Nothing is sent while it is off.

## Diagnostics you copy

Settings > About has a Copy diagnostics row. Pressing it puts one plain text
report on your clipboard and nothing else happens. Nothing is written to disk and
nothing is sent anywhere. The text leaves your Mac only when you paste it into a
message to support.

It holds what the app knows about itself and its connection: the app and macOS
versions, the version of the bundled `hey` tool, whether the app is running from
a translocated path or a disk image, whether that tool passed the app's trust
check, the connection state, how the last Imbox read and Screener check ended and
the kind of failure if either failed, whether each list is empty, the size of the
cached page file, and up to 50 log lines from the current run. Those lines name
the call that failed and the kind of failure, never the tool's own output. Never
a subject, a sender, a name, an address, a token or the install id.

## Updates

Checking for updates fetches a small feed from toolsforhey.com and the update
itself from this repository on GitHub. Both see your IP address and the app
version, as any download does. No system profile is sent.

## What we do not do

We run no server of our own that holds anything of yours. Nothing is sold,
shared or used for advertising, and there is no account with us.

## Removing everything

Quit the app, delete it from Applications, and delete
`~/Library/Application Support/com.soulesstudio.toolsforhey.menubar`. Signing out
of the tool is a separate step, since its sign in is shared with any other copy
of `hey` on your Mac.

## Questions

Open an issue here or write to support@toolsforhey.com.
