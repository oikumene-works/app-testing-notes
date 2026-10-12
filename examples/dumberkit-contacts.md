# Testing automatic backups in DumberKit Contacts

12 October 2026. The test took place on 12 October 2026.

DumberKit: Contacts produced backup files containing all five test contacts,
but parts of two people's addresses were missing. A second device restart
also removed the next backup's schedule while the backup setting remained
enabled. We needed separate checks for file creation, file contents, and
the result of restoring the file.

Codex executed the technical tests, collected evidence, compared data,
examined relevant source code, and wrote the reports and this case study.
The person directing the work approved the scope, requested the additional
backup test, and approved publication of the findings. No independent human
test execution or verification was recorded.

## The app and test environment

The app was a contact manager designed for keypad navigation and proposed for
inclusion in F-Droid. Codex used the developer's released APK, the Android
installation file, and checked its identity before installation.

The app ran on a small, portrait-oriented virtual Android device whose screen
was visible on the Linux computer. Codex mainly controlled it with commands
corresponding to a keypad's direction and action buttons, with some taps for
Android permission and file-selection dialogs.

The detailed specifications below identify the environment for anyone
reproducing or comparing the test.

| Part | Used in this test |
| --- | --- |
| App | DumberKit: Contacts 1.0.0, version code 18, `com.dumberkit.contacts` |
| Android | One visible AOSP (Android Open Source Project) Android 16 / API 36 x86_64 emulator; system-image revision 2; emulator version 37.2.12 |
| Display | 480 × 640 pixels, 240 dpi pixel density, portrait orientation, and three-button system navigation |
| Input | ADB directional and action key events; some taps for system permission and file-picker choices |
| Data and network | Five fictional contacts in the app's private storage; external network access blocked and isolation checked |
| Backup-phase settings | System language US English (en-US); app initially Finnish (fi-FI); Europe/Helsinki time zone; system text scale 100%; app default font size Large |

The linked finding reports below include the exact APK fingerprint and
supporting evidence. The result applies to this developer release in this
emulator. We did not test a physical keypad phone, Traditional T9 text entry,
or usability with real users.

## How the additional test arose

In the original test, creating, editing, cancelling changes, searching, and
retaining contacts after restart worked in the paths exercised. Import and
export through a contact file revealed problems. Before the environment was
closed, the person asked for automatic backups to be investigated as well.
This was agreed as an additional test on the same temporary device.

The imported test contacts had predefined expected values. Codex compared
the backups both with those original expectations and with the stored data
captured just before the additional test.

A **preferred-phone marker** identifies a contact's preferred phone number.
It had already been lost during the earlier import and remained absent after
restoration, so this was not a new backup finding. A **favorite-contact marker**
instead marks the whole contact as a favorite in the app. Alice's
favorite-contact marker was present in the stored data immediately before
the backup phase.

## What Codex did and observed

1. Codex enabled automatic backups and restarted the device without changing
   its clock. The app created a file containing all five contacts. Android
   also showed a schedule for the next backup.
2. Codex restarted the device again before the next backup was due. The
   schedule disappeared, although the setting stayed enabled. Opening the
   app and its settings page did not restore the schedule. This was observed
   in the second-restart sequence before any clock change.
3. After preserving the finding, Codex moved only the device clock past the
   original backup window; no second file appeared. After restoring the time,
   Codex opened **Manage automatic backups** and accepted the existing settings
   again without changing their values. This was an action in the setup
   dialog, beyond simply viewing Settings. Codex then read Android's system
   record of scheduled actions and found a new backup alarm. A separate clock
   simulation caused Android's scheduled action to create a second backup.
   These short simulations did not establish reliability overnight or during
   prolonged device sleep.
4. Codex disabled automatic backups, cleared this test app's data, and
   verified the empty starting state. Importing the second backup restored
   five contacts whose compared fields matched the file. The same address
   content was still missing. Alice's favorite-contact marker was not
   represented in the backup and was not restored.

Carlos's address illustrates the change below. The same change had already
appeared in a manual export and occurred again in the automatic backups.
A comparison address with only some fields filled retained its separate fields.

| Address component | Before backup | In the backup and after restoration |
| --- | --- | --- |
| PO box | Box 17 | Empty |
| Extended address | Unit 4 | Empty |
| Street | 123 Sample Street | 123 Sample Street Example City, Sample Region 12345 Exampleland |
| City | Example City | Empty |
| Region | Sample Region | Empty |
| Postcode | 12345 | Empty |
| Country | Exampleland | Empty |

Some address text survived as part of the combined street value. Names,
phone values and types, email addresses, birthday, notes, and Unicode
characters were retained in the comparisons performed. Unicode includes
characters such as the ë and Ö in the fictional name Zoë Östergård.
Counting the contacts alone would not have revealed the address loss.

## How the interpretation was checked

The app's default storage was its own database. An empty result from
Android's shared contacts service therefore did not prove that the app's
contacts were absent. Codex checked both storage locations. After restoration,
the list remained empty on screen even though the records had been saved.
Force-stopping and reopening the app made them visible. Failure to refresh
the display was distinguished from loss of the underlying data.

There were mistakes in Codex's operation too. One attempt during the original
test temporarily marked the wrong person as a favorite. Such attempts were
recorded as control problems and kept separate from app findings. At the
start of the backup phase, the app language had changed to Finnish; the
reason remained unexplained. Clearing its data returned it to English.
The report retained the actual settings of each phase.

## Closing the test and changing our practice

Codex restored the device's actual time and time settings. Once the person
declared testing complete, Codex removed the app and its data, closed the
emulator, and removed the temporary session files. Cleanup was verified.
The retained clean system-image files matched their pre-test fingerprints.

The approved findings were published on 12 October 2026. The reports on
[address information lost during export and backup](https://github.com/lbockaj/DumberKit-Contacts/issues/5)
and [the backup schedule disappearing after restart](https://github.com/lbockaj/DumberKit-Contacts/issues/6)
contain reproduction steps and evidence attachments. The
[summary in F-Droid's review discussion](https://gitlab.com/fdroid/fdroiddata/-/merge_requests/51845#note_3995188493)
also covers the other findings. The published text and attachment contents
were checked at publication time.

After this test, we updated our planning guidance to consider automatic
backups when choosing the scope for an app that stores user data. The person's
additional request exposed a path Codex had omitted from the original scope.
Our questions now include whether the next run remains scheduled and whether
the original content can be recovered, alongside whether a file is created.

[Overview of our testing practice](../README.md).
