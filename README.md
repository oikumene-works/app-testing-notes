# Test Android apps with AI

In our established workflow, a one-sentence request is enough for Codex to
find app-testing candidates that match our agreed criteria. The person
chooses an app. Codex proposes a bounded test and asks whether to begin;
a short approval can be enough to start. During testing, Codex handles the
agreed technical work and involves the person where listening, physical
actions or observations are needed.

This simplicity has grown through repeated tests. The tools, working
agreements and previous results are recorded and can be reused. This starter
kit shares that accumulated groundwork so others can adapt it to their own
setup and build a similarly straightforward collaboration.

This repository provides a small starter kit and worked examples from that
collaboration. The examples come from Codex on Linux, mainly testing apps
proposed for [F-Droid](https://f-droid.org/en/docs/). The starter has not yet
been tried by a newcomer or validated with another assistant or operating
system.

## Start here

Read the **[first-test instructions](starter/README.md)**. Tell the assistant
which app and question matter to you, or ask for help finding a suitable
candidate. Once you choose an app, the assistant creates or reuses its working
folder, prepares the documents and checks the available tools. It proposes a
bounded test or explains the setup still needed. You review that before app
testing starts.

You do not need to fill in the test template or learn every command first.
The proposal identifies where your participation will be needed. Routine
technical work then proceeds within the scope you have agreed.

## Read an example or go deeper

| I want to… | Read |
| --- | --- |
| See one complete, bounded test record | [Quiet Night: controls under a screen filter](examples/quiet-night.md) |
| Understand backup and restore comparisons | [DumberKit Contacts](examples/dumberkit-contacts.md) |
| Understand testing with a remote service | [Wraith](examples/wraith-odysseus.md) |
| Understand the method and its evidence limits | [Detailed guide and lessons](guide.md) |

The assistant uses the [working agreement](starter/working-agreement.md) and
[test record template](starter/test-record-template.md). They are small text
documents to adapt, not an installer or a test runner. Keep local device data,
personal choices and evidence in your own working folder.

Improve the documents from actual use: explain what was unclear, what you
tried and what change would have helped. Include only information suitable
for public sharing. App-specific findings normally belong in the app
developer's tracker, under the publication scope agreed for that test.

Codex prepared these documents from the project's test records at the person's
request. Each worked example describes the actual human and Codex contributions.

## Reuse and license

Except where otherwise identified, the original documentation and text
templates in this repository are licensed under
[Creative Commons Attribution 4.0 International (CC BY 4.0)](LICENSE).
Credit **oikumene-works / app-testing-notes**, link to the source and license,
and indicate changes when sharing an adaptation. For example:

> Adapted from [app-testing-notes](https://github.com/oikumene-works/app-testing-notes)
> by oikumene-works, licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).
> Changes: [briefly describe your changes].

The license applies to rights the project can grant in its own text. Linked
apps, source code and externally hosted reports or evidence retain their
existing terms. Third-party material identified as such is not relicensed
by this notice. Contribution statements describe what Codex and the person
actually did; they are separate from the reuse license.

## Earlier links to the guide

The detailed sections previously on this page now live in the guide. These
entry points preserve links to the earlier headings.

<a id="testing-android-apps-with-a-person-and-codex"></a>

[Testing Android apps with a person and Codex](guide.md).

<a id="what-ai-does-in-this-arrangement"></a>

[What AI does](guide.md#what-ai-does-in-this-arrangement).

<a id="the-main-parts-of-our-environment"></a>

[The environment](guide.md#the-main-parts-of-our-environment).

<a id="when-the-emulator-itself-fails"></a>

[Emulator failures](guide.md#when-the-emulator-itself-fails).

<a id="how-we-prepare-a-device-for-a-test"></a>

[Device preparation](guide.md#how-we-prepare-a-device-for-a-test).

<a id="how-a-question-becomes-a-test-result"></a>

[From question to result](guide.md#how-a-question-becomes-a-test-result).

<a id="how-codex-gets-evidence-from-the-app"></a>

[Collecting evidence](guide.md#how-codex-gets-evidence-from-the-app).

<a id="retesting-delays-and-queued-work"></a>

[Delays and queued work](guide.md#retesting-delays-and-queued-work).

<a id="speech-input-capture-and-text-delivery"></a>

[Speech input](guide.md#speech-input-capture-and-text-delivery).

<a id="before-a-time-sensitive-test"></a>

[Time-sensitive tests](guide.md#before-a-time-sensitive-test).

<a id="what-the-person-contributes"></a>

[Human contributions](guide.md#what-the-person-contributes).

<a id="how-the-practice-grows"></a>

[How the practice grows](guide.md#how-the-practice-grows).
