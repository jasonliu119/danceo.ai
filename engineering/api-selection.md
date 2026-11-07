# Choosing an API for AI Dance Video Generation

For a photo-to-dance product, evaluate the model's ability to use both a subject image and a movement reference. Text-to-video and image-to-video APIs do not necessarily offer reference-video motion transfer.

## Compare the complete workflow

| Criterion | Questions to ask |
| --- | --- |
| Inputs | Does the model accept an image and a reference video together? What formats, sizes, and URLs are supported? |
| Motion and identity | Does it preserve the choreography and a recognizable subject across different poses and subjects? |
| Output | What are the supported durations, resolutions, aspect ratios, audio behavior, and download lifetimes? |
| Operations | Are jobs asynchronous? Are polling, webhooks, cancellation, rate limits, and error codes documented? |
| Cost | How is a request billed, including input duration, output duration, retries, and failed jobs? |
| Rights and privacy | Do the provider's terms permit the intended use, storage, and retention of customer media? |

Model capability and gateway capability are separate: the same model may have different parameter names, limits, or availability through different providers. Danceo's implementation includes a Kie provider integration and adapters for different reference-video input schemas. Provider configuration and supported models can change; consult current provider documentation before relying on a particular option.

## Use an adapter boundary

Define an internal request around product concepts such as subject image, reference video, duration, and desired resolution. Translate those concepts into each provider's actual schema in a separate adapter. Normalize job status and error categories on the way back. Do not assume every model supports every field: unsupported fields may be rejected, ignored, or require different semantics.

Keep provider credentials on the server. Store the provider task ID so a job can be checked later, and design retries around the provider's idempotency and billing rules; blindly repeating a submission can create duplicate paid jobs.

## Run a small evaluation

Use the same authorized test images and reference clips across candidates. Include people, original characters, different camera movements, and any subject types your product intends to support. Record identity consistency, motion fidelity, artifacts, completion rate, latency, and total cost. Inspect multiple outputs per case, and retest after a model or API version changes. Results from a small sample indicate tradeoffs, not universal rankings.

See also [architecture](architecture.md) and [prompt design](prompt-design.md).
