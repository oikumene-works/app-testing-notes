# Start with one small Android test

21 November 2026.

Start with an app you want to investigate, or ask the assistant to suggest
candidates using criteria you agree together. Once you choose an app, the
assistant prepares its working folder and documents, checks what is available
and proposes a bounded test. You decide whether that proposal fits, then take
part where the test needs your own actions or observations.

Codex prepared this kit from our testing instructions and completed tests.
The examples use Codex on Linux; this starter has not yet been tried by a
newcomer or validated with another assistant or operating system.

## 1. Choose a starting point and ask to begin

Use an assistant session with access to local files and command tools, and
give it this repository or a link to these instructions. You may first need
to connect the session to a local project or enable that access. Creating
the app's working folder is then the assistant's task; you do not need to
create it by hand. If local access is unavailable, ask for setup help first.

Choose one of these opening requests and replace the bracketed text.

**If you already have an app in mind:**

> Read this repository's starter instructions. I want to investigate
> [app and source link], particularly [one useful question]. Prepare a test
> proposal.

**If you want help choosing an app:**

> Read this repository's starter instructions. Help me agree selection
> criteria for [the kind of app or problem that interests me], then suggest
> a few test candidates.

For the assistant: read the [working agreement](working-agreement.md), then
follow the selected path. If candidates are requested, present them for the
person to choose before preparing an app-specific test. Once an app is
chosen, create or reuse a suitable working folder within the agreed project
or location. Ask about the location only if it is unclear or involves a
meaningful choice. Copy the working agreement and prepare `test-record.md`
from the [template](test-record-template.md), preserving existing records
and keeping local paths, device identifiers and evidence separate from this kit.

Inspect the relevant tools without changing the device. Propose a small
test with its effects, total time, needed human participation and cleanup.
Explain any missing setup. Stop at the proposal; these opening requests do
not ask for tool installation or app execution.

Relevant file excerpts, screenshots and tool results may be sent to the AI
service as context. A local test device does not make that processing offline.
Use fictional inputs where possible and keep unrelated personal content out
of captures. Enter any needed credentials directly into the appropriate
sign-in interface, not into chat or the test record.

## 2. Review the proposal and your part in it

For the selected app, the assistant presents a feasible test proposal or
identifies a concrete missing prerequisite. The proposal covers the app
build, device, cases, data and network effects, total
time and cleanup. The assistant distinguishes working capabilities from
missing, unsupported or unverified ones. You do not need to fill in the
record or choose every technical command yourself.

Agree any necessary setup and human participation before starting. Your own
phone model, language, available time and audio preferences belong here;
the examples' choices and old approvals do not carry over to your test.

### When your actions or observations matter

These are reasons to involve you when relevant, not mandatory checks for
every app. The assistant should identify them during planning.

| Test area | Your part | The assistant's part |
| --- | --- | --- |
| Sounds, speech and notifications | Listen during an agreed interval; describe the words, order, overlap or change you actually heard, including uncertainty. Choose headphones when useful. | Announce the device and planned sound first; check route and settings, keep playback running for the observation, and record technical events separately from hearing. |
| Physical taps and gestures | Make a specified tap, swipe or multi-finger gesture on the actual screen when physical input needs confirmation. Describe the visible response. | Prepare the starting state, pause its own input, capture the sequence and distinguish a physical gesture from an injected command. |
| Camera or other brief physical events | Position the real object or device and trigger the agreed action when timing requires it, such as photographing a display before it turns off. | Prepare capture and logging, then compare the actual captured content with the result rather than a remembered earlier state. |
| Direct screen observations | Describe what is visible on the device when a screenshot is unavailable, ambiguous or needs checking against the actual display. | Retain capture limitations and your observation separately; do not turn viewing into an independent repeat of the whole test. |

You may also need to connect or unlock a device and complete sign-in yourself.
These preparation steps are distinct from observing whether an app works.
The [method guide's human contributions](../guide.md#what-the-person-contributes)
show how these distinctions mattered in completed tests.

For a shared step, the assistant explains one action and what to observe,
prepares the state and gives a clear ready cue. It waits for your response
before advancing, keeping the relevant test conditions in place. It records
your observation and uncertainty before interpreting it. If you cannot take
part, the affected check remains unperformed or limited; the assistant can
propose a different scoped approach without inventing a result.

## 3. Run the agreed test and close it out

Once you authorize execution, the assistant handles routine technical work
within that scope. It records the starting conditions, actions, results and
evidence, and makes the agreed handoffs for your participation. An uncertain
result can justify a focused repeat within the remaining scope and time.

You can follow the test as it runs and take part in the agreed steps. A
separately agreed viewing break gives you time to explore the app freely
for yourself after the planned test cases, before cleanup. The assistant
announces when the app is ready for this exploration, stops its automated
test activity and waits for you to finish. This free exploration is separate
from the recorded test cases.

The assistant reserves time for cleanup. It keeps the report and agreed
evidence, removes only test-owned temporary state, restores changed settings
and verifies cleanup. Any unresolved cleanup item stays visible in the
record. You then review the findings and their limits. Publication is a
separate effect unless already included in your approval.

For a new chat, point it to the working agreement and the current-state
section of `test-record.md`. It should recover the existing scope and clock
before continuing. Starting a new chat does not reset the budget.

## Examples, detail and reuse

The [Quiet Night record](../examples/quiet-night.md) shows a completed small
test. The [detailed guide](../guide.md) explains tools and method lessons;
read the parts needed for your question. You do not need all historical
examples before starting. Grow the setup only when actual use shows a need.

The documents and text templates use [CC BY 4.0](../LICENSE). When sharing an
adapted copy, retain source and license credit and indicate your changes;
the [reuse notice](../README.md#reuse-and-license) gives an example.
