# Quiet Night 2.2.1 — can controls receive input through the screen filter?

Test date: 16 November 2026. Example prepared: 21 November 2026.

This test asked whether the screen filter could work without blocking the
controls underneath. All four selected checks worked on one Pixel 9a
configuration. Codex operated the phone and examined the evidence; the
person connected and unlocked it. The run, including final records and
verified cleanup, took **17 minutes 46 seconds**.

For a first reading, follow [the basic case R01](#r01--original-blocking-condition),
[the interpretation limit in R03](#r03--maximum-settings-and-input-to-another-app)
and [cleanup](#timing-cleanup-and-reporting). R02 and R04 add variations.
The exact build details below can wait until you want to compare environments.

Codex adapted a completed test into the [test record template](../starter/test-record-template.md).
This is a retrospective teaching example, not the original plan or a new run.
Expectations below restate the original test's purpose. The original report
and evidence remain the detailed sources. Historical approval, device choices
and timing do not authorize or prescribe another person's test.

## Current state and next step

- **Historical closeout:** the four cases passed on the identified build and
  phone; cleanup and subsequent authorized publication were verified.
- Result: the reported ordinary-overlay touch blocking did not recur.
- Next at closeout: wait for relevant developer feedback or a new instruction.
  No automatic monitoring or new test was authorized.
- Retained resources: reports and selected evidence; no runtime resource.
- Record owner: the original test's Codex chat. This example does not track
  the app's later development or current issue state.

## Question, scope and authority

Quiet Night applies a screen filter to adjust warmth and dimming. An ordinary
overlay is an app-drawn layer above another screen. In the previous version,
this overlay blocked touches in the tested configuration. The developer
supplied a correction. This retest asked whether
controls now worked through the filter, including changes in dimming and a
short scheduled fade.

The [original finding](https://github.com/JaredTweed/QuietNight/issues/1) and
[2.2.0 report](https://gitlab.com/-/project/36528/uploads/3498ad1f1e4c0f0b5e246032eace723e/QuietNight-2.2.0-test-report.md)
provide the earlier evidence. The
[developer's retest request](https://gitlab.com/fdroid/fdroiddata/-/merge_requests/54381#note_4241127096)
explains the correction being checked.

- Included: the original 45% warmth / 25% dim condition, repeat after reopening,
  live dim changes, maximum settings, another app's underlying surface and a
  short fade if time allowed.
- Excluded: audio, upgrade migration, reboot, overnight use, the accessibility
  overlay's full range and a broad regression test of unrelated features.
- Effects authorized by the person: obtain and qualify the APK, install it on
  the prepared test phone, operate the selected controls, grant the needed
  permissions, collect evidence and clean up. No new account or network
  interception. The APK had no `INTERNET` permission.
- Budget: 45 minutes including preparation, downloads, waits, reporting and
  cleanup. Stop adding cases at 07:58:26; finish by 08:10:26 Europe/Helsinki.
  No viewing wait or excluded time was part of this retest.
- Output: a local report and evidence for review. Publication was separately
  authorized after the test; it was not part of the original runtime approval.

## Human participation

The person connected and unlocked the phone. All four cases then used input
injected through ADB; no physical confirmation taps or listening checks were
part of this round. No human observation handoff was therefore recorded
during these cases. The result supports the injected-input paths exercised;
it does not establish an independently repeated human touch test.

Other tests may need direct listening or physical gestures. The
[starter's participation guidance](../starter/README.md#when-your-actions-or-observations-matter)
explains how to agree those steps before running them; this example does not
add them retroactively.

## Build, environment and baseline

<details>
<summary>Exact APK identity, device and baseline</summary>

| Item | Recorded value |
| --- | --- |
| Tools and access | ADB phone control, screenshot and system-state collection were used successfully. The person connected and unlocked the phone. |
| App | `dev.jaredtweed.quietnight`, 2.2.1, version code 56; source `0860f3a757bd0c1216f56df10a4447089a51983c` |
| Artifact | Developer-signed reference APK from [F-Droid build job 18053859539](https://gitlab.com/JaredTweed/fdroiddata/-/jobs/18053859539), member `tmp/binaries/dev.jaredtweed.quietnight_56.binary.apk` |
| APK SHA-256 | `af17b568fd744d9d0d1000d0990bf3020e688a9d7454a62ed861c43bbf5ed2e9` |
| Signer | Verification passed; certificate SHA-256 `f90cc5f530bc227418eb1d0a016a790b052e6591a5c038a9979ab6e5544a4e2f`, matching the earlier release signer |
| Target | Pixel 9a, GrapheneOS 2026110701, Android 17 / API 37, Owner profile; English app UI |
| Baseline | App absent before fresh installation; relevant settings, third-party packages and audio-stream states captured |
| Permissions | Ordinary overlay and notifications allowed; accessibility service disabled; exact-alarm access granted only for the fade |
| Recovery | Remove the test app and downloads, stop filtering, alarms and owned logging; restore changes and preserve Owner and the pre-existing ADB server |

These are historical environment facts, not a recommended current download
or a required setup for using this kit. The test did not rebuild the app;
successful CI and signature checks were separate from its runtime evidence.

</details>

## Cases and results

Evidence names below are inside the
[public evidence ZIP](https://gitlab.com/-/project/36528/uploads/1dbeaf97471ed443e78d013d14e0820d/QuietNight-2.2.1-retest-evidence.zip).
Its `screenshots/`, `excerpts/` and `metadata/` directories contain the
selected observations. The [full report](https://gitlab.com/-/project/36528/uploads/4972d3c5b7505984a5dcb8ebcff96212/QuietNight-2.2.1-retest-report.md)
provides the detailed sequence and limits.

### R01 — original blocking condition

- Starting state: Always mode, warmth 45%, dim 25%, ordinary overlay allowed,
  accessibility service disabled.
- Expected: the visible filter allows menu input and can be switched off.
- Actions: enable the filter, open More options, use the filter toggle to turn
  it off; force-stop and reopen, then repeat the on/off cycle.
- Observed: **pass on both cycles**. The menu opened, the toggle changed from
  Filter on to Filter off and the overlay disappeared. Settings were retained.
- Evidence: `R01-filter-applied-45-25.png`, `R01-menu-under-filter.png`,
  `R01-filter-off-success.png` and `R01-repeat-off.png`.

### R02 — change dimming while the filter is active

- Starting state: warmth 45%, dim 0%, filter enabled.
- Expected: changing dimming keeps the controls usable.
- Actions: open the menu, drag dimming to 25%, then switch the filter off.
- Observed: **pass**. The value and appearance changed; switching off worked.
- Evidence: `R02-zero-dim-menu.png`, `R02-live-transition-to-25.png` and
  `R02-after-transition-off.png`.

### R03 — maximum settings and input to another app

- Starting state: warmth 100%, dim 85%, ordinary filter visibly active.
- Expected: the app's menu and off control work; input also reaches an
  underlying app outside Quiet Night while the filter is visible.
- Actions: exercise the menu/off control; with the filter active over the
  launcher, swipe up to open its app drawer and tap Settings.
- Observed: **pass on the exercised paths**. The menu and off control worked;
  the drawer opened and the Settings icon launched Settings.
- Evidence: `R03-maximum-menu.png`, `R03-maximum-off-success.png`,
  `R03-launcher-drawer-under-filter.png`, `R03-launcher-tap-settings-success.png`
  and the corresponding system-state excerpts.
- Limit: Settings itself hid the overlay. Navigation inside that unfiltered
  window was excluded from the touch-through claim. The launcher had a visible
  overlay before the icon tap. No Settings values were changed.

### R04 — input during a scheduled fade

- Starting state: Custom 07:35–07:42 Europe/Helsinki, five-minute fade,
  warmth 100%, dim 85%; schedule armed before the start.
- Expected: input remains usable as the filter strengthens, and manual off
  removes it at full appearance.
- Actions: allow the real five-minute fade; open the menu early and near the
  midpoint; switch the filter off at full appearance around 07:40:10.
- Observed: **pass**. Menu taps worked and the next capture showed no overlay
  after switching off. Twenty-nine periodic system opacity samples rose from
  0.0376587 to 0.799805 without exceeding 0.8.
- Evidence: `R04-fade-early-menu.png`, `R04-fade-mid-menu.png`,
  `R04-fade-full.png`, `R04-fade-final-off.png` and `metadata/fade-samples.jsonl`.
- Limits: periodic samples do not measure every frame, physical brightness
  or exact scheduling latency. Automatic ending at 07:42 was not tested;
  the filter had already been switched off manually.

## Interpretation and contributions

These observations support resolution of the reported blocking behavior on
this APK and phone configuration. They do not establish the same outcome on
other devices or versions, or cover the excluded features.

The corrected source used one window for warmth and dimming and limited its
ordinary-overlay opacity. That explains the observations plausibly; the source
change alone would not establish successful input. Similarly, the absence of
matching crash or dropped-touch log messages was supporting evidence, not the
reason to mark the visible controls as working.

Codex acquired and qualified the APK, operated the phone through ADB, examined
screenshots and technical records, performed cleanup, and wrote the report.
The person connected and unlocked the phone. The recorded taps and swipes
were injected by Codex; this round contains no independent human repetition
or listening test.

## Timing, cleanup and reporting

Preparation began at 07:25:26 and final records ended at 07:43:12
Europe/Helsinki: **17 minutes 46 seconds**, with no excluded waits.

Cleanup was verified at 07:40:45. The package, its services, filter windows
and alarms were absent. The captured settings, third-party package inventory
and all 11 audio-stream states matched baseline. Downloads were removed and
the owned logger stopped. Owner and the pre-existing ADB server were preserved.
No browser or emulator had been started. The public bundle includes
`metadata/cleanup-summary.json` and `metadata/execution-clock.json`.

The local evidence was retained. Later that day, under separate authorization,
the report, selected evidence and
[F-Droid MR summary](https://gitlab.com/fdroid/fdroiddata/-/merge_requests/54381#note_4241427934)
were published. The report and ZIP were anonymously downloaded and matched
the intended bytes at publication verification. Raw device dumps and the
device serial were excluded; the APK was not redistributed. This example
links those historical materials without changing or relicensing them.

The reusable lesson is to check whether the condition under investigation
actually held. A successful tap in a window that hides the overlay answers
a different question from a successful tap through a visible overlay.

[Start a test](../starter/README.md) · [Repository overview](../README.md).
