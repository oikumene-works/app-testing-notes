# Testing Wraith with a remote service

15 October 2026. The test took place on 15 October 2026.

Wraith for Odysseus provides an Android chat interface connected to an
Odysseus server. In a short test of version 0.5.0, basic chat and note
operations worked on the paths exercised, and two interface problems were
reproduced. The test also exposed a gap in our network recording. The
experience shows why each conclusion needs evidence that can answer the
particular question.

Codex prepared the environment, operated the app, collected and interpreted
the evidence, performed cleanup, and wrote the reports and this example.
The person directing the work agreed the scope, entered credentials directly
into the app, reviewed the drafts, questioned a screenshot, and approved
publication of the findings. Their review changed the report; no independent
human repetition of the tests was recorded.

## A small test using a real service

The developer supplied a temporary test server and account. Codex used one
visible Android 16 / API 36 emulator with a 480 × 800 pixel display, English
text, and initially three-button system navigation. The scope allowed at
most eight short chat requests and three hours including preparation,
reporting, and cleanup. Codex pressed Send six times, using only fictional
content.

The emulator's direct internet access was blocked. Its permitted connection
passed through a temporary gateway that allowed only the test server and
the developer's source host. The gateway recorded connection destinations
without decrypting the contents. It could not observe communication between
the server and the external model provider.

Login, the tested conversation persistence, and creating, editing, reopening,
and deleting a test note worked. Codex also reproduced two interface problems:
a completed new reply remained below the visible conversation until scrolling,
and Settings placed Log out beneath Android's navigation bar. These results
apply to this app version, display, and the paths exercised.

## Checking what the network recording contains

The emulator's packet capture recorded Ethernet traffic but missed the app's
Wi-Fi connection through the gateway. It contained only local network
packets. An apparently quiet recording would therefore have been a poor
basis for saying that the app made no external connections.

The gateway logs and checks of the network restrictions supplied separate,
usable evidence. They did not turn the packet capture into a complete record
of app traffic. Codex had omitted a preparation check: making a known,
permitted connection through the route the app would use and confirming that
it appeared in the recording.

That omission led to separate work on a coverage check. The lesson from this
run is already clear: test the recording method with known traffic before
using its silence as evidence.

## Separating screen actions from network and server behavior

During one request, Codex disabled Wi-Fi for 10.26 seconds. Re-enabling it did
not immediately restore connectivity in this restricted emulator setup; an
explicit reconnect was needed. The test therefore did not establish recovery
from an exactly ten-second connection loss.

Once connectivity returned, the answer appeared without manually resending
the request, and a fresh request worked. The extra reconnect delay belonged
to the test setup and was not attributed to Wraith.

Similarly, pressing Stop before answer text appeared returned the app to an
idle state, with the prompt still present. That showed what happened on
screen. It did not establish whether the server or model provider had
stopped processing. The short replies also did not establish whether final
answer text would appear gradually during a longer response.

## How a screenshot question changed the report

The person reviewing the draft noticed that one screenshot appeared to show
two answers without the prompt for the second one. This was a useful reason
to revisit the sequence and nearby captures before publication.

The earlier prompt had asked about a blue kite; Codex had pressed Stop before
any answer text appeared. The next prompt asked about a red boat and was
the request interrupted by the network test. After recovery, one assistant
bubble contained a kite paragraph followed by a boat paragraph. Another
capture showed the red-boat prompt above that whole response.

The evidence did not demonstrate a missing prompt. It also did not establish
whether the model answered both prompts together or whether the server or app
combined content. Codex added this distinction to the F-Droid summary before
publication. The person's question improved the explanation without turning
an unresolved observation into another reproduced app defect.

## Closing and reporting the test

Codex removed the test chat and note, verified logout using gesture
navigation to reach the obscured control, and checked that restarting the
app still required login. The temporary app, device data, keys, and processes
were removed; the retained clean Android image was unchanged. Removing data
through the app did not establish removal from server backups or the model
provider.

The person had no login credentials for the developer's tracker, so they
chose this repository for the detailed findings:

- [New reply remains below the visible conversation](https://github.com/oikumene-works/app-testing-notes/issues/1).
- [Log out overlaps Android navigation](https://github.com/oikumene-works/app-testing-notes/issues/2).

The [F-Droid review summary](https://gitlab.com/fdroid/fdroiddata/-/merge_requests/51956#note_4016883618)
explains that choice and links the reports and
[full report and evidence package](https://github.com/user-attachments/files/33467530/wraith-0.5.0-evidence-20261015.zip).
Codex checked the published texts and attachment contents at publication
time. The test closed with no background monitoring.

[Overview of our testing practice](../README.md).
