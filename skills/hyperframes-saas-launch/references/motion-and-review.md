# Motion and review for SaaS launches

## Make the shot map actionable

This sample assumes a fictional support product that turns a customer report into a bug ticket. Use the real product's labels and states when making a film. Frame ranges are half-open. The example is 18 seconds at 30 fps.

| Frames | Beat | Product action and the frame to inspect |
| --- | --- | --- |
| 0–90 | Establish | Show the inbox and one incoming report. Inspect the first frame and confirm the selected report is recognizable. |
| 90–225 | Act | Move into the selected report and click its ticket action. Inspect the click frame and the first frame showing the updated state. |
| 225–390 | Prove | Open the resulting ticket with the report attached. Inspect the label and attachment at viewing size and show where the ticket lives. |
| 390–540 | Close | Land the mark and the user's CTA. Inspect the first settled frame and the last decoded frame to confirm the reading hold. |

Adjust beat order and time to suit the product. In an app that already communicates the action in context, a graphic separation or virtual camera move may add little. Use a transition when it helps the viewer follow the next object or location.

## Motion that explains the product

- **Establish and isolate.** Show enough of the interface to orient the viewer. Enlarge the meaningful control or output until its label reads comfortably. Preserve enough surrounding UI for provenance. A push over a static screen can establish focus, but the product action needs a visible state change.
- **Separate and dock.** Use one editable component through the seated, floating, and docked poses so its contents, corners, and identities agree. Record translation, scale, angle, origin, opacity, and paint order where they matter. Anchor a moving card to a meaningful point, such as its active button. When its contents must stay level while a frame tilts, use nested layers.
- **Hand off with a cause.** Let a real click precede the UI response. Let a card, toggle, or cursor guide the next reveal if it belongs in the story. Give separate components their own timing. Design the incoming and outgoing poses together, including which one paints in front and when the last outgoing layer clears.
- **Keep blur on the right layer.** Keep product copy clear at the state the viewer reads. Apply any streak or depth treatment to the moving housing, background, or decorative graphic where possible. For treated footage, use the HyperFrames media workflow for the installed version.
- **Make the last shot read.** Settle the lockup and CTA while there are still frames left in the composition. A pose that lands at the exclusive end of a clip never gets a visible frame.

## HyperFrames workflow

After checking the editor skill and runtime, use a project's existing commands where provided. Otherwise use the CLI, Node.js, FFmpeg, and the supported Chromium runtime. Check the installed CLI's help if a command or flag differs. See the [official HyperFrames guide](https://hyperframes.heygen.com/tools/html-to-video) and [composition documentation](https://hyperframes.heygen.com/concepts/compositions).

```sh
npx hyperframes init launch-video
cd launch-video
npx hyperframes check --json
npx hyperframes preview
npx hyperframes render --output launch.mp4
```

Build between initialization and the check. Run the preview when there is something to review, and render the MP4 when the user requests a video file. Use the project's pinned CLI for project work when it has one. If the renderer fails, use its diagnostics and `npx hyperframes doctor` to identify the actual missing tool or runtime limit.

- Use a timed root in `index.html`. Mount each shot from `compositions/` with stable IDs and explicit starts and durations. Store render assets under `assets/` and write asset paths relative to the project. Use project-local fonts when needed for consistent glyph sizes.
- Author timed layers in markup with `class="clip"`, `data-start`, and `data-duration`. Animate their children. Keep paint order in CSS. Timeline lane order is for editing.
- Register a paused timeline per composition under its composition ID in `window.__timelines`. Derive times from a common frame rate. Convert scene-local keyframes to seconds using the local frame number divided by FPS, and use the scene's global offset only when mounting it. Give every visible element a settled or hidden pose at local frame zero. Use timeline state for motion and state changes so a direct seek does not depend on previous playback. Use timeline-controlled media and avoid wall-clock callbacks or network requests inside the render.

## Verify the actual handoffs

Review a contact sheet for the overall story and separate frame captures for the brief moments most likely to fail. Use the preview or supported snapshot commands. Inspect the actual encoded file after delivery settings have been applied. If a checker flags intentional overlap, confirm the actual composition frame before adjusting the layout or annotation.

| Inspect | Pass condition |
| --- | --- |
| Cold seek to the first two frames of every scene | Delayed objects stay in their intended offscreen or hidden state. |
| The frames around the trigger and handoff | The real state changes in causal order. A departing label remains readable when intended. Component identity, position, and stacking order make sense in motion. |
| Tight crop of the moving object at full size | No unintended second outline, duplicate content, one-frame flash, cropped label, or pop. Whole-frame scores can be inflated by an empty or stationary canvas. |
| Normal-speed playback at target size | A viewer can identify the action, result, and CTA without talking through the clip. |
| Final media and project | Export plays with the expected geometry, frame rate, runtime, and audio treatment. Project can be reopened with the referenced assets. |

When refining, log the frame, the visible defect, and the exact change. Retest the same frames plus either side of the edit. Use the product states and storyboard as the acceptance reference, with any supplied style example used to judge direction and rhythm.
