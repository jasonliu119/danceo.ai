# AI Dance Video Guide

A practical guide to turning a photo or character image into a dance video with AI. Learn how to choose an image, evaluate a dance reference, and improve the result for people, dogs, and cats.

[Try the Danceo AI dance generator](https://danceo.ai/#generator) · [Make a photo dance](https://danceo.ai/make-photo-dance) · [AI dog dance](https://danceo.ai/ai-dog-dance) · [AI cat dance](https://danceo.ai/ai-cat-dance)

## How photo-to-dance video works

A motion-transfer workflow pairs two inputs: an image defines the subject and appearance, while a reference video guides movement, timing, and framing. The generated clip is an interpretation of those inputs, so results depend on their quality and compatibility.

1. Pick a clear image with one recognizable subject.
2. Choose a short dance video with readable movement and steady framing.
3. Preview the inputs and check the displayed credit cost before generating.
4. Review the result; if movement or appearance is unclear, adjust one input and try again.

## Guides

- [Choosing a photo and dance reference](guides/photo-and-reference.md) — a checklist for better inputs and troubleshooting.
- [AI dog dance ideas](guides/dog-dance.md) — plan a playful dog or character video.
- [AI cat dance ideas](guides/cat-dance.md) — choose a cat image and movement that work together.

## Engineering guides

- [AI dance website architecture](engineering/architecture.md) — media, asynchronous tasks, and reliability.
- [Choosing a video generation API](engineering/api-selection.md) — compare motion transfer, operations, cost, and provider adapters.
- [Prompt design for motion transfer](engineering/prompt-design.md) — examples and a repeatable evaluation process.

## Common questions

**Can I make a photo dance without filming myself?**  
A photo-to-dance workflow uses a still image and a separate movement reference. You still need permission to use both inputs.

**Does the reference video become the final character?**  
The image supplies the subject; the reference guides the motion. The result may differ from either source.

**Which reference is best for a first attempt?**  
Try a short clip with one visible dancer, clear gestures, and a stable camera. Simple movement makes it easier to see what to change.

**What does it cost?**  
Danceo displays an estimated credit cost before generation. Check the current quote and [pricing](https://danceo.ai/pricing) for up-to-date details.

## Responsible use

Use images and videos you created, own, or are authorized to transform. Respect the privacy and rights of people shown, and avoid impersonation or misleading representations. Check the applicable terms before publishing generated media.

---

Maintained by [Danceo](https://danceo.ai/). This repository contains educational material; the generator is available on the website.
