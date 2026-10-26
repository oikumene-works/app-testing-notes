# Testing Android apps with a person and Codex

26 October 2026. This describes our practice on that date.

We use one person's questions and Codex's ability to operate software tools to
investigate Android apps. We want to find out whether selected everyday tasks
work, explain problems clearly, and give developers evidence they can use.

Our work has focused on apps proposed for inclusion in
[F-Droid, a community project that distributes free and open source Android software](https://f-droid.org/en/docs/).
The ideas here come from those tests. Someone working on a different kind of
app may find individual parts useful without adopting our whole arrangement.

## What AI does in this arrangement

Codex is the AI assistant we use. It can work with files and run software tools
when those capabilities are available to the task. A tool is a way to perform
an action outside the conversation, such as running a command or reading a
file. The [Codex documentation](https://learn.chatgpt.com/docs/environments/modes)
explains how to choose where a chat's tools run.

In our tests, the person describes a goal in ordinary language. Codex turns
that goal into proposed checks, prepares the test device, operates the app
through commands, and examines the results. It can also write small programs
to compare data. This combination of an AI assistant and tools is often
called an AI agent.

For example, a person might want to know whether a contacts app preserves
addresses through a backup and restore. Codex needs an actual app, a device
on which to run it, known input values, and a way to retrieve the results.
The app's behavior comes from running its code; Codex then interprets the
collected evidence. Codex can make a wrong interpretation, so we retain the
observations and comparison inputs that allow its explanation to be checked.

We did not train a separate AI model for each app. We use existing tools and
give Codex the task, relevant records, and access needed for the agreed work.

## The main parts of our environment

Our physical computer runs Linux, the operating system that hosts the test
tools, temporary device files, and retained reports. These are the main pieces:

| Part | What it means and what we use it for |
| --- | --- |
| Codex | The assistant that plans and carries out the agreed work through available tools, then explains the results. |
| Android Emulator | A program that runs a virtual Android device on the computer. We keep its screen visible in a window. |
| Physical Android phone or tablet | An actual device connected for an agreed test. We record its starting settings, remove test data and restore changes while preserving unrelated content. |
| Android system image and virtual device | The image supplies the Android operating system. The virtual device combines it with settings such as screen size and separate storage for the test. |
| APK | An Android app installation file. We record exactly which APK we install so that the result can be tied to a particular version. |
| ADB | Android Debug Bridge, a tool connecting the computer to Android. Codex uses it to install the app, send actions, and retrieve information. |
| Test data and small scripts | Fictional input values and short programs used for tasks such as comparing the original contacts with an exported file. |
| Evidence and reports | Saved screenshots, text records, data comparisons, and explanations that make the work inspectable afterward. |

Android's documentation explains the
[emulator and virtual devices](https://developer.android.com/studio/run/emulator)
and [ADB's device connection and commands](https://developer.android.com/tools/adb).
The emulator runs the Android app even though the device itself is virtual.
Its window also lets the person follow what is happening.

Here, “local” describes where the Android device and commands run. It does
not mean the AI model runs offline on that computer. Relevant prompts, file
excerpts, screenshots, and tool results can be sent to the AI service as task
context. The [documentation on local execution](https://learn.chatgpt.com/docs/enterprise/chatgpt-work-local-security)
explains this distinction. Blocking the test device's network connection is
a separate measure with a different purpose.

## How we prepare a device for a test

Our current entry point is Codex in the desktop app on the Linux computer.
The person opens our app-testing project and enters requests in its chat,
with the work set to run on this computer. The
[local project](https://learn.chatgpt.com/docs/projects?surface=app)
connects that chat to the folder containing our testing records.

Before trying the opening request below, the person needs the desktop app
installed and signed in, a local project folder selected, and file and
command tools available to the chat. Their permissions must cover reading
the relevant files and running the local checks. The agreed test also needs
access to write its files and operate the Android tools. This connection to
local tools is what lets Codex inspect and operate the computer from the chat.

The computer needs working Android tools, a suitable system image, and enough
resources to run the virtual device. Codex checks what is available and what
the app requires before proposing a test. A different Android version or a
new system-image download may be useful for a specific question; its setup
time and effects belong in that proposal.

For someone starting with an unfamiliar computer, an opening request could be:
“Check which Android testing tools are available here and describe what would
be needed for one visible test of this app.” This asks for an assessment before
installing software or starting a device. In our work, Codex handles the
technical preparation once its scope and effects are agreed.

For a run, Codex prepares a temporary virtual device from a clean system image.
Its Android version, screen size, language, and other relevant settings are
recorded. One visible device serves the agreed test session. We reset app data
when a particular check needs an empty starting point.

For our offline tests, we also set up network isolation for the emulator and
its control tools. Codex checks the network configuration and attempts an
external connection to confirm that it fails. The workstation can still
download the approved APK or read public documentation through a separate
connection. Network blocking requires its own setup and verification.

For the [Wraith test](examples/wraith-odysseus.md), which needed a remote
service, we used a gateway to restrict connections to the agreed destinations.
The developer supplied a temporary account, and the test used fictional
content within a small request limit. A separate question
was whether the network recording covered the route the app actually used.
That recording missed the app's Wi-Fi traffic, so the report kept its limits
separate from the useful evidence supplied by the gateway.

The clean system image can be reused. The temporary device's storage,
installed test app, and session files are removed when the run ends. This
makes it possible to keep useful tools while starting a later test with
fresh app data.

## How a question becomes a test result

Our work usually moves through the following stages. The scope changes with
the app and the question.

1. **Choose a useful question.** The person identifies an app or an area of
   interest. Codex examines its description, existing reports, and relevant
   source code (the program text written by developers), then proposes a
   manageable set of checks. The proposal includes the environment, network
   access, expected effects, and time for
   preparation, testing, reporting, and cleanup.
2. **Agree on the work and identify the app.** Once the task covers the
   proposed actions, Codex proceeds within that scope. It records the APK's
   source, version, and file hash: a fingerprint used to recognize the same
   file later. This identifies the package tested; it does not establish that
   its features work.
3. **Define the inputs and expected outcome.** For a contacts test, we create
   fictional names, phone numbers, and address fields with known values.
   Those values provide a reference after export and restoration. We keep
   the expectation separate from what the app happens to produce.
4. **Act, inspect, and follow up.** Codex performs a short sequence of actions,
   retrieves evidence, checks that the intended action occurred, and compares
   the result with the expectation. An unexpected result may lead to a
   focused repeat or a source-code check within the agreed scope.
5. **Close the run and prepare the findings.** Codex removes the temporary
   environment and verifies that its processes and files are gone. The
   report describes the actions, expected and observed results, supporting
   evidence, and limits. Publication follows the person's decision about
   the content and destination.

Routine choices within an approved test belong to Codex. A new goal, material
change in effects, or publication outside the agreed scope needs a new
decision. This keeps the person involved in choices that matter without
requiring them to enter every command.

## How Codex gets evidence from the app

Our Android tests use commands to operate the device and request snapshots
of its state. A screenshot shows what was drawn on the screen. A
**UI tree** is a structured description of interface elements, such as
labels and buttons. **Logs** record messages or events from the app and
Android. Exported files and database snapshots reveal stored content.

These sources answer different questions. A button may appear in the UI tree
while its label is hidden behind another part of the screen. A list may
look empty even though records have already been saved. We compare sources
when the distinction affects the result.

Our first physical-tablet check, on a Samsung SM-X210, showed why a larger
screen is not enough to describe the test conditions. In
[TEA Kids 1.1.6 / 62](https://github.com/alunoadsnoite/tea-mvp-childs/issues/4#issuecomment-6355504071),
landscape at the existing 110% text size clipped Home content that the attempted
vertical swipes did not reveal. At 200%, portrait also lost visible content.
We recorded orientation, screen dimensions, effective display density and text
scale together. A separate Help label existed in the UI tree and its target
opened Help, yet the label was visually indistinguishable in the screenshot.
These were two observations from one tablet configuration; their causes and
behavior on other tablets were not established.

Codex receives the observations that its tools return. It needs a fresh
observation after an action that changes the screen or data. A command that
completed successfully may still have entered text into the wrong field.
Such attempts are recorded as problems with the test operation and corrected
before drawing conclusions about the app.

In the [DumberKit Contacts example](examples/dumberkit-contacts.md), a backup contained
all five contacts, yet parts of two addresses were missing. Counting the
contacts would have missed the problem. Comparing individual fields with the
known starting values exposed it.

The [PsyJournal test report](https://github.com/FSeixasPT/PsyJournal/issues/1)
also records failures in the evidence tools themselves. Android's usual UI
dump command could not obtain an idle screen while a live timer was active.
Codex used an alternative that did not wait for idle, checked that the output
was new and contained interface elements, and compared it with screenshots.
An older tree, an empty tree, and black screenshots were not treated as proof
of the app's visible state. A successful command alone is not enough.

The person's question about PsyJournal's browser links led to a separate
source-code review. An app's lack of Internet permission does not by itself
answer what information it passes to another app that opens a link. Codex
traced the addresses supplied by PsyJournal 12.0: the reviewed paths did not
append diary entries, doses, or notes, but a selected article address could
reveal the substance of interest. This was evidence about the app's URL
construction; the test did not observe browser traffic or the linked sites.

In the [Violentomètres 1.1.1 test](https://gitlab.com/fdroid/fdroiddata/-/merge_requests/52094#note_4087047253),
Android's system screenshot showed a black app area. Codex obtained readable
images through the [emulator's own screenshot command](https://developer.android.com/studio/run/emulator-take-screenshots),
with the app's default screenshot refusal and Android's `FLAG_SECURE`
protection still enabled. Early captures showed a transition or the previous
screen, so fresh images after visible changes were checked against the UI
tree and window state. This established an observation method for the tested
Android 14 emulator configuration. It did not establish screenshot access
for ordinary Android apps or capture behavior on physical phones.

## What the person contributes

The person chooses what matters, considers Codex's proposal, and can redirect
the work when something important is missing. During the DumberKit test, the
person asked for automatic-backup checks after the original checks were
finished. That request led to an additional finding and a change in our
future planning.

Codex performed the technical test execution, evidence collection, analysis,
and report writing in that example. Watching the emulator or approving the
report did not constitute independent verification. Reports describe any
human observation or independent check only when it actually occurred.

The person providing the tablet for the TEA Kids check had no knowledge of
Portuguese, the app's interface language. Codex operated the app and interpreted
its labels, retaining the original wording alongside English explanations.
The person viewed the final state. This was scoped functional and layout
evidence; it did not establish Portuguese-language quality, independent human
verification or suitability for children.

Some questions also need a physical phone. In the
[AutoScroller test](https://github.com/sebacoden/autoScroll/issues/1), the
person performed swipes and three-finger taps while Codex prepared and
navigated the phones, collected screen and input evidence, and analyzed
the results. A touchscreen log established that three contacts overlapped;
it did not establish which gesture reached the app. Comparing two phones
did not isolate the operating system when the video app and installed
services also differed.

Audible behavior also needs a listener or an audio recording. In the
[Gantry test](https://github.com/mesmerverse/gantry/issues/1), Codex posted
synthetic notifications and inspected settings and logs; the person reported
what the phone actually said and when the notification chime occurred. At
the person's request, cases were repeated one at a time, with an answer
before the next post. A successful speech call did not establish what was
heard or when the sounds began.

The work produces evidence about the tested app version and conditions.
An emulator result alone does not establish how a physical phone feels to
use, whether an app suits a particular group of people, or how reliably a
background feature runs for weeks. Those questions need their own evidence.

## How the practice grows

We first tried to design a general testing framework, then an adaptable
starting system for creating test environments. Our present practice has
grown through individual app tests and the problems they exposed.

We keep shared working instructions in text files, an app-specific record of
what happened and what may happen next, and the original evidence behind each
report. This lets a later conversation recover the relevant context. A
report can include an **issue**, meaning a separately described problem in
a tracking system, with steps to reproduce it. We normally use the
developer's tracker. For Wraith, the person had no login credentials for
that tracker and chose this repository instead. The F-Droid summary explains
the reason and links the findings; they remain reports in our own repository.

Repeated work sometimes justifies a small helper. After the DumberKit test,
Codex built a tool that saves a test phase's screenshot, UI tree, and
background information together. It was checked separately using Android 16's
Settings app. It did not perform the earlier DumberKit test, and it does not
decide whether an app passed.

When an approved report is published, Codex reads the public text and checks
that its attachments are accessible and match the intended files. We retain
that record alongside the test. Later corrections and retests keep their own
dates and app versions.

After PsyJournal, we agreed to publish an approved package in dependency
order: attachments, the full report, and individual issues first; verify
their contents and links; then publish the F-Droid MR summary with those
links already included. This avoids a predictable follow-up edit while
leaving room for later factual corrections.

The [DumberKit Contacts example](examples/dumberkit-contacts.md) follows a
backup test through cleanup and reporting, including mistakes in our
operation and a lesson for later test plans. The
[Wraith example](examples/wraith-odysseus.md) examines the limits of network
evidence and shows how the person's screenshot question improved the report.

Codex wrote and translated this overview at the person's request, using the
project's records and the linked documentation for tool explanations.
