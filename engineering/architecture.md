# Architecture of an AI Dance Video Website

An AI dance generator combines a web application, media storage, an asynchronous video model, and a way to track long-running jobs. The following is a reference architecture inspired by the Danceo workflow; it is a design guide, not a public API specification.

```text
Browser → Web application → Generation API → Task store
              │                  │                │
              └→ Media storage   └→ Video provider ←┘
                                         │
Browser ← Status and result ← Processing / storage
```

## Application and media

The browser lets a user preview an image, select an authorized movement reference, inspect the estimated cost, and follow progress. The server authenticates requests, validates inputs and duration, calculates the quote, and creates a task. Images and videos belong in object storage rather than database rows; keep task metadata and ownership in a database.

A TypeScript stack can use React and TanStack Start for the interface and server routes, Drizzle for database access, and object storage for media. Other frameworks can use the same separation of responsibilities.

## Generation lifecycle

1. Validate the image, reference video, permissions, and requested duration.
2. Create a durable task and record the cost and inputs needed to resume it.
3. Submit the inputs to a provider and save its task identifier.
4. Poll the provider or accept a verified webhook, updating the task as it progresses.
5. Store or assemble the result, then show the final video to its owner.
6. Handle failures and credit adjustments consistently, including retries and duplicate notifications.

Long clips may need to be split into segments if a provider has a per-request limit, then joined afterward. Segment boundaries can introduce visual or audio discontinuities, so test the complete output rather than assuming a successful job means a good video.

## Reliability and security

Treat provider callbacks and status checks as repeatable operations. Use idempotent updates or a lease to prevent two workers from advancing the same task at once. Retry temporary failures with bounded backoff, but surface configuration or account failures for operator action. Keep credentials server-side, restrict who can access uploads and results, validate remote media URLs, and apply upload limits. A status-poll-driven design also needs a recovery strategy when the user closes the page.

Read the [API selection guide](api-selection.md) and [prompt design guide](prompt-design.md). For the end-user workflow, visit [Danceo](https://danceo.ai/).
