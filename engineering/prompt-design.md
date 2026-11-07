# Prompt Design for Photo-to-Dance Video

A motion-transfer prompt complements the subject image and reference video. The image carries appearance; the reference carries motion and framing. A prompt can clarify priorities, but it cannot reliably repair an unclear image or guarantee exact choreography.

## A useful structure

Describe the task, identity, motion, and framing in that order. Keep instructions concrete and avoid asking the model to both follow and replace the same motion.

**Person example**

> Replace the dancer in the reference video with the person in the portrait. Keep the subject recognizable and follow the reference movement and camera framing.

**Dog character example**

> Replace the reference dancer with the dog character in the image. Keep the face, coat color, and markings recognizable. Adapt the movement into a playful performance while retaining the reference framing.

These are illustrative prompts, not a promise of a particular result. Use original or authorized inputs.

## Adapt to the model

Read the selected model's input schema: a reference-video adapter may use a different field for each image and video, and some model endpoints do not accept or use a text prompt at all. Do not assume a prompt that works on one API will be honored by another. In those cases, concentrate on input selection and the settings the endpoint actually supports.

## Iterate systematically

1. Establish a baseline with a clear image, a short stable reference, and a concise prompt.
2. Inspect identity, body shape, motion, framing, and artifacts over the whole clip.
3. Change one variable at a time: the image, the reference, or one instruction.
4. Compare several outputs where practical, since generation can vary between runs.
5. Keep notes on the model, input versions, settings, and outcome so a change can be evaluated later.

Avoid adding a long list of competing adjectives. If identity drifts, prioritize recognizable features; if the movement is unclear, simplify the reference. When the API does not expose prompting, test different inputs instead.

Learn more about [choosing inputs](../guides/photo-and-reference.md), [selecting a video API](api-selection.md), and [Danceo's generator](https://danceo.ai/#generator).
