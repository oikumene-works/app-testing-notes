# [App and version] — [one useful test question]

Template prepared by Codex from the project's testing practice. Replace the
bracketed fields with this run's facts. The assistant fills this record from
inspection and the person's decisions; the person need not complete a form.
Use “unknown”, “not tested” or “not applicable — reason” where appropriate.
Remove these template instructions from the finished report.

## Current state and next step

- Updated: [date, time and time zone]. Status: [proposed / running / waiting /
  complete / stopped with open items].
- Result so far: [bounded conclusion, or not run].
- Next allowed step and trigger: [action or waiting condition; authority].
- Open items and retained resources: [including cleanup and time remaining].
- Record owner: [person or chat responsible for this run].

## Question, scope and authority

[What would this test establish? Link the app, exact earlier finding or review
when relevant. Distinguish an initial test from a focused retest.]

- Included: [selected paths and useful boundary cases].
- Excluded: [material limits, including already-tested paths being skipped].
- Effects: [acquisition/setup, device changes, data, host network reads,
  app network, accounts/services; preserve existing data].
- Budget and stop condition: [total time, cutoff for new cases, cleanup reserve;
  any agreed break for free exploration after the test cases; any excluded
  wait, specified separately from following the running test].
- Authorization: [the person's dated decision and exact covered effects;
  distinguish proposed actions from approved actions].
- Output and publication: [local report/evidence; publication destination and
  authority if any, otherwise not authorized].

## Human participation

- Needed during testing: [listening, physical taps/gestures, camera action,
  direct screen observation, or none needed for the scoped claims; why].
- Agreed handoff: [who does what, ready cue, observation interval, relevant
  conditions to keep active, and when the assistant resumes its input].
- Preparation only: [device connection, unlocking or sign-in; keep these
  separate from human observations of app behavior].
- If unavailable or uncertain: [which result remains limited or untested;
  any scoped repeat or alternative, without assuming approval for expansion].

## Build, environment and baseline

| Item | Actual value and evidence |
| --- | --- |
| Tools and access | [Relevant capabilities: ready / missing / unsupported / unknown; how checked] |
| App artifact | [Source URL, package, version/version code, APK SHA-256, signer check and comparison; source revision if relevant] |
| Target | [Device/emulator, OS build/API; local target identifier in private working copy] |
| Starting state | [Existing installation/data, permissions and relevant settings; baseline evidence] |
| Inputs and conditions | [Exact synthetic values, language/input, network; audio route or other condition when relevant] |
| Recovery and cleanup | [What will be removed, restored, preserved and checked; ownership of resources] |

## Cases and results

Write expectations before acting. Use one block per case; evidence can link to
a small screenshot, excerpt or comparison rather than a complete device dump.

### [T01 — descriptive name]

- Starting state and input: [exact condition].
- Expected: [observable outcome and why it is expected].
- Actions: [enough detail to repeat; repetitions and important timing].
- Who acted and observed: [assistant-injected input or a physical human
  action; keep the person's reported observation and uncertainty distinct].
- Observed: [what happened; pass / fail / inconclusive / blocked / not tested].
- Evidence: [file or link and relevant timestamp; evidence type].
- Limits or control problems: [what this does not establish; none observed is
  different from none possible].

## Interpretation and contributions

[Summarize what the evidence supports and what remains uncertain. Separate
source explanations from runtime results. Name relevant untested paths.]

[State what the named assistant executed, analysed and wrote, and what the
person actually performed or observed. Do not assume independent validation.]

## Timing, cleanup and reporting

- Clock: [preparation start; final records end; time zone; elapsed total and
  any agreed excluded waits; preserve original times after interruptions].
- Cleanup: [removed/restored/stopped/preserved items, verification and evidence;
  remaining uncertainty or action, if any].
- Evidence retained: [location and access level; exclude private material from
  a public copy and replace local-only links with accessible evidence].
- Publication: [not authorized / draft / approved / published; if published,
  destination, actor, exact result and readback evidence].
- Next: [update the current-state section above to agree with this closeout].

Template source: [oikumene-works / app-testing-notes](https://github.com/oikumene-works/app-testing-notes),
[CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).
Template changes: [describe changes when sharing an adapted copy, or none].
