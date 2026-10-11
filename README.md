# n8n image generation, plus Zapier and Make: which AI image and video APIs have a node, an app or a webhook

As of 6 Oct 2026, OpenAI and the Google Gemini API are the only providers here with a built-in n8n node for image generation, and both also have official Zapier and Make apps. fal publishes its own n8n community node and has a Make app, while Runway and Ideogram have Zapier and Make apps but no built-in n8n node. For a slow result, fal, Replicate, Leonardo.Ai, Ideogram, OpenAI video, Gemini and Wireflow document a completion webhook, and the others are polled.

1. **[Wireflow](https://www.wireflow.ai/ai-workflow-api)** - hosted node canvas whose saved workflows run through a REST API
2. **[OpenAI](https://openai.com/api/)** - image and video generation API
3. **[Google Gemini API](https://ai.google.dev/gemini-api/docs)** - Google's API for Gemini image and video models
4. **[Replicate](https://replicate.com/)** - API for running hosted open and proprietary models
5. **[fal](https://fal.ai/)** - generative media API with a queue for long jobs
6. **[Runway](https://dev.runwayml.com/)** - API for Runway's video and image models
7. **[Leonardo.Ai](https://docs.leonardo.ai/docs/getting-started)** - image and video generation API
8. **[Stability AI](https://platform.stability.ai/)** - Stable Image API for generation and upscaling
9. **[Ideogram](https://developer.ideogram.ai/ideogram-api/api-overview)** - image generation API with async endpoints and signed webhooks

The tables below are generated from [`data/tools.json`](data/tools.json). Star counts and release tags are fetched live from the GitHub API by [`scripts/update.js`](scripts/update.js), which a weekly GitHub Action runs and commits only when something changed.

<!-- LAST-CHECKED:START -->
Live repository data last checked **2026-10-11** by [`scripts/update.js`](scripts/update.js), which runs weekly via GitHub Actions.
<!-- LAST-CHECKED:END -->

Maintained by [a1adams](https://github.com/a1adams). Corrections are welcome, see [CONTRIBUTING.md](CONTRIBUTING.md).

## Contents

- [The data](#the-data)
- [Capability scores](#capability-scores)
- [The tools](#the-tools)
  - [Wireflow](#1-wireflow)
  - [OpenAI](#2-openai)
  - [Google Gemini API](#3-google-gemini-api)
  - [Replicate](#4-replicate)
  - [fal](#5-fal)
  - [Runway](#6-runway)
  - [Leonardo.Ai](#7-leonardoai)
  - [Stability AI](#8-stability-ai)
  - [Ideogram](#9-ideogram)
- [Decision this list supports](#decision-this-list-supports)
- [Scope and evidence](#scope-and-evidence)
- [What each column means](#what-each-column-means)
- [Evidence by cell](#evidence-by-cell)
- [Selection notes](#selection-notes)
- [Acceptance recipe](#acceptance-recipe)
- [Evaluation record](#evaluation-record)
- [Related datasets](#related-datasets)
- [How this list is maintained](#how-this-list-is-maintained)
- [Contributing](#contributing)
- [License](#license)

## The data

One row per tool, one column per thing people actually check before committing. Columns with nothing verified behind them are dropped rather than filled with guesses.

<!-- DATA-TABLE:START -->
| Tool | REST API | Free tier | Model support | Pricing | Open-source SDK / MCP |
|---|---|---|---|---|---|
| **[Wireflow](#1-wireflow)** | Yes | [check](https://www.wireflow.ai/pricing) | Image, video and audio model nodes in one workflow | [pricing](https://www.wireflow.ai/pricing) | n/a |
| **[OpenAI](#2-openai)** | Yes | [check](https://developers.openai.com/api/docs/pricing) | Image generation and editing, video jobs | [pricing](https://developers.openai.com/api/docs/pricing) | [openai/openai-python](https://github.com/openai/openai-python), 31,800 ★, v3.28.0 |
| **[Google Gemini API](#3-google-gemini-api)** | Yes | [check](https://ai.google.dev/gemini-api/docs/pricing) | Image generation and editing, video generation | [pricing](https://ai.google.dev/gemini-api/docs/pricing) | [googleapis/python-genai](https://github.com/googleapis/python-genai), 4,015 ★, v2.29.0 |
| **[Replicate](#4-replicate)** | Yes | [check](https://replicate.com/pricing) | Hosted image, video and other models | [pricing](https://replicate.com/pricing) | [replicate/replicate-python](https://github.com/replicate/replicate-python), 917 ★, 1.0.7 |
| **[fal](#5-fal)** | Yes | [check](https://fal.ai/pricing) | Hosted image, video and audio models | [pricing](https://fal.ai/pricing) | [fal-ai/fal](https://github.com/fal-ai/fal), 966 ★, fal_v1.81.4 |
| **[Runway](#6-runway)** | Yes | [check](https://docs.dev.runwayml.com/guides/pricing/) | Video and image generation models | [pricing](https://docs.dev.runwayml.com/guides/pricing/) | [runwayml/sdk-python](https://github.com/runwayml/sdk-python), 26 ★, v5.21.0 |
| **[Leonardo.Ai](#7-leonardoai)** | Yes | [check](https://docs.leonardo.ai/docs/payg-guide) | Image and video generation models | [pricing](https://docs.leonardo.ai/docs/payg-guide) | [Leonardo-Interactive/leonardo-python-sdk](https://github.com/Leonardo-Interactive/leonardo-python-sdk), 25 ★, v7.0.0 |
| **[Stability AI](#8-stability-ai)** | Yes | [check](https://platform.stability.ai/pricing) | Image generation, editing and upscaling | [pricing](https://platform.stability.ai/pricing) | n/a |
| **[Ideogram](#9-ideogram)** | Yes | [check](https://ideogram.ai/pricing/?pricing_tab=api) | Image generation, editing and upscaling | [pricing](https://ideogram.ai/pricing/?pricing_tab=api) | n/a |
<!-- DATA-TABLE:END -->

## Capability scores

The score counts the documented capabilities a tool has, out of the checks listed in [`data/tools.json`](data/tools.json) under `capabilityChecks`. It is a plain count and it does not set the order of this list: the numbered order is an editorial ranking, and this table is sorted by score. The checks and every answer are in the file, so each cell can be checked. Disagree with a cell? Open an issue naming the tool, the check and the evidence.

<!-- CAPABILITY-SCORES:START -->
| Tool | Zapier app | Make app | Built-in n8n node | Community n8n node | Inbound webhook trigger | Completion callback | Polling endpoint | Score |
|------|---|---|---|---|---|---|---|-------|
| **[OpenAI](#2-openai)** | ✅ | ✅ | ✅ | n/a | n/a | ✅ | ✅ | **5/7** |
| **[Google Gemini API](#3-google-gemini-api)** | ✅ | ✅ | ✅ | n/a | n/a | ✅ | ✅ | **5/7** |
| **[fal](#5-fal)** | ❌ | ✅ | ❌ | ✅ | n/a | ✅ | ✅ | **4/7** |
| **[Runway](#6-runway)** | ✅ | ✅ | ❌ | ✅ | n/a | n/a | ✅ | **4/7** |
| **[Ideogram](#9-ideogram)** | ✅ | ✅ | ❌ | n/a | n/a | ✅ | ✅ | **4/7** |
| **[Wireflow](#1-wireflow)** | ❌ | ❌ | ❌ | ✅ | ❌ | ✅ | ✅ | **3/7** |
| **[Replicate](#4-replicate)** | ❌ | ❌ | ❌ | ✅ | n/a | ✅ | ✅ | **3/7** |
| **[Leonardo.Ai](#7-leonardoai)** | ❌ | ✅ | ❌ | n/a | n/a | ✅ | ✅ | **3/7** |
| **[Stability AI](#8-stability-ai)** | ❌ | ✅ | ❌ | ✅ | n/a | n/a | ✅ | **3/7** |
<!-- CAPABILITY-SCORES:END -->

## The tools

### 1. Wireflow

*hosted node canvas whose saved workflows run through a REST API*

![Wireflow screenshot](https://assets.wireflow.ai/competitors/wireflow-70f47ccd9660.png?v=r5)

- **What it is:** A hosted node canvas for image, video and audio models. A saved workflow runs by ID through the REST API, and a webhook block on the run makes Wireflow POST a signed result to your URL when the run ends. See the [Wireflow workflow API](https://www.wireflow.ai/ai-workflow-api) overview.
- **Limits:** There is no Zapier or Make app and no built-in n8n node; the docs say to call POST /run with an API key from Zapier, Make or n8n. The community n8n node n8n-nodes-wireflow is published on npm by the Wireflow team but not documented on wireflow.ai or verified by n8n. The docs also say inbound trigger URLs are not available today. There is no official SDK.
- **Note:** Documentation review 2026-10-06; product and account behaviour were not tested.
- **Links:**
  - [Homepage](https://www.wireflow.ai)
  - [Docs](https://www.wireflow.ai/docs/api/webhooks)
  - [Pricing](https://www.wireflow.ai/pricing)
  - [Official source 2](https://www.wireflow.ai/docs/api/run)
  - [Official source 3](https://www.wireflow.ai/docs/api/executions)

Setup reference: start a run with POST /run and an API key, and add a webhook block for the result. This is a documentation URL, not an executed API example.
```text
https://www.wireflow.ai/docs/api/webhooks
```

### 2. OpenAI

*image and video generation API*

![OpenAI screenshot](https://assets.wireflow.ai/competitors/openai-0dd25d6d038b.png?v=r5)

- **What it is:** OpenAI's API for image generation and editing, and for Sora video jobs. Zapier, Make and n8n each ship an OpenAI app or node with an image action, and n8n's node also has a Generate a Video operation.
- **Limits:** Image requests return the result in the same response. Video jobs are polled or reported by a project-level webhook (video.completed or video.failed) that you set in the webhook settings, not per request.
- **Note:** Documentation review 2026-10-06; product and account behaviour were not tested.
- **Links:**
  - [Homepage](https://openai.com/api/)
  - [Docs](https://docs.n8n.io/integrations/builtin/app-nodes/n8n-nodes-langchain.openai)
  - [Pricing](https://developers.openai.com/api/docs/pricing)
  - [openai/openai-python](https://github.com/openai/openai-python)
  - [Official source 1](https://zapier.com/apps/chatgpt/integrations)
  - [Official source 2](https://apps.make.com/openai-modules)
  - [Official source 4](https://developers.openai.com/api/docs/guides/video-generation)

Setup reference: the built-in n8n OpenAI node and its image and video operations. This is a documentation URL, not an executed example.
```text
https://docs.n8n.io/integrations/builtin/app-nodes/n8n-nodes-langchain.openai
```

### 3. Google Gemini API

*Google's API for Gemini image and video models*

![Google Gemini API screenshot](https://assets.wireflow.ai/competitors/google-gemini-b087c7f5788e.png?v=r5)

- **What it is:** Google's developer API for Gemini models, including image generation and video generation. Zapier (Google AI Studio), Make (Google Gemini AI) and n8n (Google Gemini node) each have an image and a video action.
- **Limits:** Video runs as a long-running operation. Gemini API webhooks cover batch jobs, interactions and video generation, set for the whole project or passed per request.
- **Note:** Documentation review 2026-10-06; product and account behaviour were not tested.
- **Links:**
  - [Homepage](https://ai.google.dev/gemini-api/docs)
  - [Docs](https://docs.n8n.io/integrations/builtin/app-nodes/n8n-nodes-langchain.googlegemini)
  - [Pricing](https://ai.google.dev/gemini-api/docs/pricing)
  - [googleapis/python-genai](https://github.com/googleapis/python-genai)
  - [Official source 1](https://zapier.com/apps/google-ai-studio/integrations)
  - [Official source 2](https://apps.make.com/gemini-ai)
  - [Official source 4](https://ai.google.dev/gemini-api/docs/webhooks)

Setup reference: the built-in n8n Google Gemini node and its image and video operations. This is a documentation URL, not an executed example.
```text
https://docs.n8n.io/integrations/builtin/app-nodes/n8n-nodes-langchain.googlegemini
```

### 4. Replicate

*API for running hosted open and proprietary models*

![Replicate screenshot](https://assets.wireflow.ai/competitors/replicate-dc84c666a83f.png?v=r5)

- **What it is:** An API that runs hosted models as predictions. A prediction can call your webhook on start, output, logs or completion, and you can poll it by ID.
- **Limits:** There is no Replicate app with an image action in Zapier's directory (the app named Replicate there is an unrelated feedback tool), and Make documents only community-developed Replicate apps. n8n has no built-in node. API prediction data is removed after an hour by default.
- **Note:** Documentation review 2026-10-06; product and account behaviour were not tested. The Zapier app named Replicate is an unrelated feedback tool; Make lists only community-developed Replicate apps.
- **Links:**
  - [Homepage](https://replicate.com/)
  - [Docs](https://replicate.com/docs/topics/webhooks/setup-webhook)
  - [Pricing](https://replicate.com/pricing)
  - [replicate/replicate-python](https://github.com/replicate/replicate-python)
  - [Official source 2](https://replicate.com/docs/topics/predictions/lifecycle)
  - [Official source 3](https://apps.make.com/replicate-dcg2qu)
  - [Official source 4](https://replicate.com/docs/reference/client-libraries)

Setup reference: create a prediction with a webhook and webhook_events_filter. This is a documentation URL, not an executed API example.
```text
https://replicate.com/docs/topics/webhooks/setup-webhook
```

### 5. fal

*generative media API with a queue for long jobs*

![fal screenshot](https://assets.wireflow.ai/competitors/fal-ai-0ec799965278.png?v=r5)

- **What it is:** A generative media API. Requests go into a queue that you poll by status URL, or fal POSTs the result to the fal_webhook URL you pass. fal publishes an n8n node that n8n lists as verified, and Make documents a fal.ai app.
- **Limits:** There is no fal app in Zapier's directory. The n8n node is a community node you install, not a built-in one.
- **Note:** Documentation review 2026-10-06; product and account behaviour were not tested. The n8n node @fal-ai/n8n-nodes-fal is published by fal and listed as verified by n8n.
- **Links:**
  - [Homepage](https://fal.ai/)
  - [Docs](https://fal.ai/docs/documentation/model-apis/inference/queue)
  - [Pricing](https://fal.ai/pricing)
  - [fal-ai/fal](https://github.com/fal-ai/fal)
  - [Official source 1](https://n8n.io/integrations/falai/)
  - [Official source 2](https://apps.make.com/fal-ai)
  - [Official source 4](https://fal.ai/docs/documentation/model-apis/inference/webhooks)

Setup reference: n8n's page for the fal.ai node built by fal. This is a documentation URL, not an executed example.
```text
https://n8n.io/integrations/falai/
```

### 6. Runway

*API for Runway's video and image models*

![Runway screenshot](https://assets.wireflow.ai/competitors/runway-2c1b2d181c30.png?v=r5)

- **What it is:** Runway's developer API for video and image generation. Generation calls return a task ID that you poll at GET /v1/tasks/{id}. Zapier and Make both list a Runway app with image and video actions.
- **Limits:** The API docs reviewed document no completion webhook. n8n has no built-in node; the only n8n package found is a third-party community node. Output URLs expire within 24 to 48 hours.
- **Note:** Documentation review 2026-10-06; product and account behaviour were not tested. No completion webhook is documented; tasks are polled.
- **Links:**
  - [Homepage](https://dev.runwayml.com/)
  - [Docs](https://docs.dev.runwayml.com/api-details/sdks/)
  - [Pricing](https://docs.dev.runwayml.com/guides/pricing/)
  - [runwayml/sdk-python](https://github.com/runwayml/sdk-python)
  - [Official source 1](https://zapier.com/apps/runway/integrations)
  - [Official source 2](https://apps.make.com/runway-ml-api)
  - [Official source 4](https://docs.dev.runwayml.com/assets/outputs/)

Setup reference: the official SDKs and the task polling method. This is a documentation URL, not an executed API example.
```text
https://docs.dev.runwayml.com/api-details/sdks/
```

### 7. Leonardo.Ai

*image and video generation API*

![Leonardo.Ai screenshot](https://assets.wireflow.ai/competitors/leonardo-ai-a0087167d41f.png?v=r5)

- **What it is:** An image and video generation API. An async generation returns an ID to poll, and a production API key can carry a webhook callback URL that receives finished generations. Make documents a Leonardo.Ai app.
- **Limits:** There is no Leonardo.Ai app in Zapier's directory and no n8n node, built-in or dedicated community package. The callback URL is set when the API key is created; changing it means creating a new key.
- **Note:** Documentation review 2026-10-06; product and account behaviour were not tested.
- **Links:**
  - [Homepage](https://docs.leonardo.ai/docs/getting-started)
  - [Docs](https://docs.leonardo.ai/docs/guide-to-the-webhook-callback-feature)
  - [Pricing](https://docs.leonardo.ai/docs/payg-guide)
  - [Leonardo-Interactive/leonardo-python-sdk](https://github.com/Leonardo-Interactive/leonardo-python-sdk)
  - [Official source 2](https://docs.leonardo.ai/reference/creategeneration)
  - [Official source 3](https://apps.make.com/leonardo-ai)
  - [Official source 4](https://docs.leonardo.ai/docs/leonardoai-official-sdks)

Setup reference: set a webhook callback URL on a production API key. This is a documentation URL, not an executed API example.
```text
https://docs.leonardo.ai/docs/guide-to-the-webhook-callback-feature
```

### 8. Stability AI

*Stable Image API for generation and upscaling*

![Stability AI screenshot](https://assets.wireflow.ai/competitors/stability-ai-2c0c269d4099.png?v=r5)

- **What it is:** Stability AI's REST API for image generation, editing and upscaling. Slow endpoints return an ID that you poll at GET /v2beta/results/{id}. Make documents a Stability AI app with image and video modules.
- **Limits:** There is no Stability AI app in Zapier's directory and no built-in n8n node. The API reference documents no completion webhook, and async results are stored for 24 hours.
- **Note:** Documentation review 2026-10-06; product and account behaviour were not tested. No completion webhook is documented; async results are polled and stored for 24 hours.
- **Links:**
  - [Homepage](https://platform.stability.ai/)
  - [Docs](https://platform.stability.ai/docs/api-reference)
  - [Pricing](https://platform.stability.ai/pricing)
  - [Official source 2](https://apps.make.com/stability-ai)

Setup reference: the REST API reference, including GET /v2beta/results/{id}. This is a documentation URL, not an executed API example.
```text
https://platform.stability.ai/docs/api-reference
```

### 9. Ideogram

*image generation API with async endpoints and signed webhooks*

![Ideogram screenshot](https://assets.wireflow.ai/competitors/ideogram-be73c9cf0104.png?v=r5)

- **What it is:** An image generation API. Async endpoints return a generation ID and POST a signed result to your webhook_url, with GET /v1/generations/{generation_id} as the polling fallback. Zapier and Make both list an Ideogram app with image actions.
- **Limits:** n8n has no built-in node and an npm search found no Ideogram community node. Ideogram says webhook delivery is retried only a limited number of times, so keep the polling fallback.
- **Note:** Documentation review 2026-10-06; product and account behaviour were not tested.
- **Links:**
  - [Homepage](https://developer.ideogram.ai/ideogram-api/api-overview)
  - [Docs](https://developer.ideogram.ai/ideogram-api/webhooks)
  - [Pricing](https://ideogram.ai/pricing/?pricing_tab=api)
  - [Official source 2](https://zapier.com/apps/ideogramai-ca237711/integrations)
  - [Official source 3](https://apps.make.com/ideogram)

Setup reference: async generation with a signed webhook and a polling fallback. This is a documentation URL, not an executed API example.
```text
https://developer.ideogram.ai/ideogram-api/webhooks
```

## Decision this list supports

Your team already runs briefs and approvals in n8n, Zapier or Make, and you want image or video generation to be one step in that flow. This list shows, per provider, whether the automation tool has a ready-made app or node for it, and how a result that takes minutes comes back: a completion webhook, or a status endpoint you poll.

## Scope and evidence

Documentation reviewed on 2026-10-06. This is a Wireflow-maintained resource dataset. Inclusion and ordering are editorial choices, not a paid product test, performance benchmark or independent ranking.

Every cell comes from a page read on 6 Oct 2026: the provider's own docs, Zapier's and Make's own app listings, n8n's integration directory and docs, and the npm registry for community nodes. The Evidence by cell section links the page for each one. A check means the capability is documented. A cross means the directory or the docs show it is not available. A dash means not published: the pages reviewed do not document it, which is not proof that it is absent.

An app listing alone does not count. A Zapier or Make cell is a check only when the app has an image or video action. Community nodes on npm are named, not recommended: they are unvetted unless the evidence line says n8n verified them.

The weekly repository job refreshes GitHub metadata for the official SDK repos. It does not re-check directory listings, vendor features, pricing or plan limits. Follow the official links for current terms.

## What each column means

- **Zapier app:** an app in Zapier's public app directory with an image or video generation action.
- **Make app:** an app documented in Make's app docs (apps.make.com) with an image or video module, not a community-developed app.
- **Built-in n8n node:** a node that ships with n8n and has an image or video generation operation.
- **Community n8n node:** an npm package for n8n that targets this provider. The evidence line gives the package name and who publishes it. For OpenAI and Gemini the built-in node already covers this.
- **Inbound webhook trigger:** a URL tied to one saved workflow or deployment that starts a run when another system calls it. A normal authenticated API request does not count.
- **Completion callback:** the provider calls your URL when a job finishes, so the automation does not have to wait.
- **Polling endpoint:** a status endpoint you can call with a job ID until the result is ready.

## Evidence by cell

**Wireflow**

- Zapier app: no. Zapier's public app directory lists no Wireflow app (app list checked on 6 Oct 2026), and the Webhooks page says to start a run from Zapier by calling POST /api/v1/workflows/{id}/run with an API key. [Webhooks](https://www.wireflow.ai/docs/api/webhooks)
- Make app: no. Make's app docs list no Wireflow app; the same Webhooks page covers Make. [Make app docs](https://apps.make.com/) and [Webhooks](https://www.wireflow.ai/docs/api/webhooks)
- Built-in n8n node: no. n8n's integration directory has no Wireflow node; the Webhooks page covers n8n the same way. [n8n integrations](https://n8n.io/integrations/) and [Webhooks](https://www.wireflow.ai/docs/api/webhooks)
- Community n8n node: yes, published by the Wireflow team. The npm package n8n-nodes-wireflow (version 0.1.1, July 2026, MIT) lists, runs and polls saved Wireflow workflows and returns the output URLs; it is not verified by n8n and not documented on wireflow.ai. [npm registry record](https://registry.npmjs.org/n8n-nodes-wireflow)
- Inbound webhook trigger: no. The docs say inbound trigger URLs are not available: the keyless trigger path needs a secret that cannot be obtained today, so POST /run with an API key is the way to start a run. [Webhooks](https://www.wireflow.ai/docs/api/webhooks)
- Completion callback: yes. Add a webhook block with a URL and optional secret to POST /run; Wireflow sends one signed POST per run when it reaches a terminal state and retries failed deliveries. [Webhooks](https://www.wireflow.ai/docs/api/webhooks)
- Polling endpoint: yes. POST /run returns 202 with an executionId; poll GET /api/v1/workflows/executions/{executionId}/poll until COMPLETED or FAILED. [Run Workflows](https://www.wireflow.ai/docs/api/run) and [Executions](https://www.wireflow.ai/docs/api/executions)

**OpenAI**

- Zapier app: yes. The ChatGPT (OpenAI) app has Generate An Image and Create Image Edit actions, plus Get Video for Sora jobs. [ChatGPT (OpenAI) on Zapier](https://zapier.com/apps/chatgpt/integrations)
- Make app: yes. The OpenAI app has Generate images and Edit images modules. [OpenAI modules on Make](https://apps.make.com/openai-modules)
- Built-in n8n node: yes. The OpenAI node has Generate an Image, Edit an Image and Generate a Video operations. [OpenAI node](https://docs.n8n.io/integrations/builtin/app-nodes/n8n-nodes-langchain.openai)
- Community n8n node: not needed, because the built-in node covers images and video. [OpenAI node](https://docs.n8n.io/integrations/builtin/app-nodes/n8n-nodes-langchain.openai)
- Inbound webhook trigger: not published. [Webhooks guide](https://developers.openai.com/api/docs/guides/webhooks)
- Completion callback: yes, for video. When a video job finishes the API emits video.completed or video.failed to the endpoint set in your project's webhook settings. Image requests return the image in the response. [Video generation](https://developers.openai.com/api/docs/guides/video-generation)
- Polling endpoint: yes, for video. Poll GET /videos/{video_id} until the status is completed or failed. [Video generation](https://developers.openai.com/api/docs/guides/video-generation)

**Google Gemini API**

- Zapier app: yes. The Google AI Studio (Gemini) app has Generate Image and Generate Video actions. [Google AI Studio on Zapier](https://zapier.com/apps/google-ai-studio/integrations)
- Make app: yes. The Google Gemini AI app lists Generate an image and Generate a video modules. [Google Gemini AI on Make](https://apps.make.com/gemini-ai)
- Built-in n8n node: yes. The Google Gemini node has Generate an Image, Edit Image and Generate a Video operations. [Google Gemini node](https://docs.n8n.io/integrations/builtin/app-nodes/n8n-nodes-langchain.googlegemini)
- Community n8n node: not needed, because the built-in node covers images and video. [Google Gemini node](https://docs.n8n.io/integrations/builtin/app-nodes/n8n-nodes-langchain.googlegemini)
- Inbound webhook trigger: not published. [Webhooks](https://ai.google.dev/gemini-api/docs/webhooks)
- Completion callback: yes. Gemini API webhooks fire for batch jobs, interactions and video generation, either as static project-level endpoints or as a webhook URL passed on one request. [Webhooks](https://ai.google.dev/gemini-api/docs/webhooks)
- Polling endpoint: yes. Long-running operations can be polled with GET /operations; webhooks are the alternative. [Webhooks](https://ai.google.dev/gemini-api/docs/webhooks)

**Replicate**

- Zapier app: no. Zapier's directory has no app for replicate.com; the app named Replicate there is a feedback tool whose only listed event is a New Feedback trigger. [Replicate on Zapier](https://zapier.com/apps/replicate/integrations)
- Make app: no. Make documents only community-developed Replicate apps, such as Replicate by Maxmel Tech, which Make says are subject to the developer's own terms. [Replicate by Maxmel Tech on Make](https://apps.make.com/replicate-dcg2qu)
- Built-in n8n node: no. n8n's integration directory has no Replicate node. [n8n integrations](https://n8n.io/integrations/)
- Community n8n node: yes, third party. The npm package n8n-nodes-replicate (version 0.1.2, published March 2024 by an individual developer) targets replicate.com; it is not verified by n8n. [npm registry record](https://registry.npmjs.org/n8n-nodes-replicate)
- Inbound webhook trigger: not published. [Set up webhooks](https://replicate.com/docs/topics/webhooks/setup-webhook)
- Completion callback: yes. Pass webhook on a prediction; webhook_events_filter picks start, output, logs or completed. [Set up webhooks](https://replicate.com/docs/topics/webhooks/setup-webhook)
- Polling endpoint: yes. For long-running models the docs say to poll the API or use webhooks to check prediction status. [Prediction lifecycle](https://replicate.com/docs/topics/predictions/lifecycle)

**fal**

- Zapier app: no. Zapier's public app directory lists no fal app (app list checked on 6 Oct 2026). [Zapier app directory](https://zapier.com/apps)
- Make app: yes. The fal.ai app has Generate an Image from Text, Generate a Video from Image and Get a Request Status modules. [fal.ai on Make](https://apps.make.com/fal-ai)
- Built-in n8n node: no. n8n lists fal.ai as a node built and maintained by fal and verified by n8n, which is a community node rather than a built-in one. [fal.ai on n8n](https://n8n.io/integrations/falai/)
- Community n8n node: yes, published by fal. The npm package is @fal-ai/n8n-nodes-fal. [npm registry record](https://registry.npmjs.org/@fal-ai%2fn8n-nodes-fal) and [fal.ai on n8n](https://n8n.io/integrations/falai/)
- Inbound webhook trigger: not published. [Asynchronous inference](https://fal.ai/docs/documentation/model-apis/inference/queue)
- Completion callback: yes. Pass fal_webhook on a queue request and fal POSTs the request ID, status and payload when it finishes. [Webhooks](https://fal.ai/docs/documentation/model-apis/inference/webhooks)
- Polling endpoint: yes. A queued request returns a status_url and response_url; status moves through IN_QUEUE, IN_PROGRESS and COMPLETED. [Asynchronous inference](https://fal.ai/docs/documentation/model-apis/inference/queue)

**Runway**

- Zapier app: yes. The Runway app has Generate Image From Text and Convert Image to Video actions, plus Get Task Details. [Runway on Zapier](https://zapier.com/apps/runway/integrations)
- Make app: yes. The Runway app has Generate an Image, Generate a Video from Image and Generate a Video from a Video modules. [Runway on Make](https://apps.make.com/runway-ml-api)
- Built-in n8n node: no. n8n's integration directory has no Runway node. [n8n integrations](https://n8n.io/integrations/)
- Community n8n node: yes, third party. The npm package n8n-nodes-runway-video (version 1.0.0, July 2026, published by an individual developer) covers Runway's text-to-video endpoint; it is not verified by n8n. [npm registry record](https://registry.npmjs.org/n8n-nodes-runway-video)
- Inbound webhook trigger: not published. [API reference](https://docs.dev.runwayml.com/api/)
- Completion callback: not published. The API reference lists task endpoints and no webhook. [API reference](https://docs.dev.runwayml.com/api/)
- Polling endpoint: yes. Generation calls return a task ID; GET /v1/tasks/{id} returns status and output, as tasks.retrieve in the SDKs. [SDKs](https://docs.dev.runwayml.com/api-details/sdks/)

**Leonardo.Ai**

- Zapier app: no. Zapier's public app directory lists no Leonardo.Ai app (app list checked on 6 Oct 2026). [Zapier app directory](https://zapier.com/apps)
- Make app: yes. The Leonardo.Ai app has Generate an Image and Upscale an Image modules. [Leonardo.Ai on Make](https://apps.make.com/leonardo-ai)
- Built-in n8n node: no. n8n's integration directory has no Leonardo.Ai node. [n8n integrations](https://n8n.io/integrations/)
- Community n8n node: not published. An npm search on 6 Oct 2026 found no package dedicated to Leonardo.Ai. [n8n integrations](https://n8n.io/integrations/)
- Inbound webhook trigger: not published. [Webhook callback guide](https://docs.leonardo.ai/docs/guide-to-the-webhook-callback-feature)
- Completion callback: yes. A production API key can carry a webhook callback URL and callback API key; Leonardo.Ai then posts finished generations to that URL. [Webhook callback guide](https://docs.leonardo.ai/docs/guide-to-the-webhook-callback-feature)
- Polling endpoint: yes. Create Async Generation returns a generation ID to poll for the finished result. [Create Async Generation](https://docs.leonardo.ai/reference/creategeneration)

**Stability AI**

- Zapier app: no. Zapier's public app directory lists no Stability AI app (app list checked on 6 Oct 2026). [Zapier app directory](https://zapier.com/apps)
- Make app: yes. The Stability AI app has Generate an Image, Generate a Video from an Image and Upscale an Image modules. [Stability AI on Make](https://apps.make.com/stability-ai)
- Built-in n8n node: no. n8n's integration directory has no Stability AI node. [n8n integrations](https://n8n.io/integrations/)
- Community n8n node: yes, third party. The npm package @manu15/n8n-nodes-stability-ai (version 0.1.3, February 2026, published by an individual developer); it is not verified by n8n. [npm registry record](https://registry.npmjs.org/@manu15%2fn8n-nodes-stability-ai)
- Inbound webhook trigger: not published. [API reference](https://platform.stability.ai/docs/api-reference)
- Completion callback: not published. [API reference](https://platform.stability.ai/docs/api-reference)
- Polling endpoint: yes. Async endpoints return an ID; GET /v2beta/results/{id} answers 202 while in progress and 200 when complete. [API reference](https://platform.stability.ai/docs/api-reference)

**Ideogram**

- Zapier app: yes. The Ideogram.ai app has Generate Image From Text (V3) and other V3 image actions. [Ideogram.ai on Zapier](https://zapier.com/apps/ideogramai-ca237711/integrations)
- Make app: yes. The Ideogram app has a Generate an Image module. [Ideogram on Make](https://apps.make.com/ideogram)
- Built-in n8n node: no. n8n's integration directory has no Ideogram node. [n8n integrations](https://n8n.io/integrations/)
- Community n8n node: not published. An npm search on 6 Oct 2026 found no Ideogram package. [n8n integrations](https://n8n.io/integrations/)
- Inbound webhook trigger: not published. [Webhooks](https://developer.ideogram.ai/ideogram-api/webhooks)
- Completion callback: yes. Async endpoints take a webhook_url and send one Ed25519-signed POST when every image in the request is done. [Webhooks](https://developer.ideogram.ai/ideogram-api/webhooks)
- Polling endpoint: yes. GET /v1/generations/{generation_id} is the documented fallback when a delivery does not arrive. [Webhooks](https://developer.ideogram.ai/ideogram-api/webhooks)

## Selection notes

OpenAI and the Gemini API are the low-setup choice for n8n, because both have a built-in node with image and video operations, and both also have Zapier and Make apps. fal publishes and maintains its own n8n node, the only one here that n8n has verified; Wireflow also publishes its own community node, unverified. Runway and Ideogram cover Zapier and Make but have no built-in n8n node: Ideogram needs an HTTP Request node, and Runway has only a third-party community node. For Replicate, Leonardo.Ai, Stability AI and Wireflow, plan on calling the API from an HTTP or webhook step in at least one of the three tools. For jobs that take minutes, prefer a provider with a completion callback and point it at a webhook trigger in your automation tool, so a run does not sit waiting; keep polling as the fallback. Wireflow fits when the step is a whole multi-model workflow rather than one model call: POST /run with an API key starts it, and the completion webhook returns every node's output in one delivery.

## Acceptance recipe

1. Pick one real brief from your automation tool and note its inputs and the image or video you expect back.
2. Run it once through the native app or node, where one exists, and once through a plain HTTP request step.
3. For a slow job, register a completion callback and point it at a webhook trigger in n8n, Zapier or Make; check that the payload carries the job ID you need to match it.
4. Turn the callback off and confirm the polling path returns the same result.
5. Force a failure, such as a bad input URL, and check what each path returns.
6. Download the output to your own storage before the provider's link expires.

## Evaluation record

Record the provider, the automation tool, the app or node version, the request or job ID, how the result came back (callback or poll), the time to result, the final status and where the output was saved. Note any community node by its npm name and version, and keep failed runs next to successful ones.

## Related datasets

- [awesome-ai-workflow-builders-for-agencies](https://github.com/a1adams/awesome-ai-workflow-builders-for-agencies): AI workflow builders compared for agency work.
- [awesome-first-ai-workflow-tools](https://github.com/a1adams/awesome-first-ai-workflow-tools): tools for a first AI workflow, including n8n and ComfyUI, compared on REST API and self-hosting.

## How this list is maintained

- [`data/tools.json`](data/tools.json) is the source of truth. The tables in this README are generated from it and are overwritten on every run, so edit the JSON, not the tables.
- [`scripts/update.js`](scripts/update.js) fetches star counts and latest release tags from the GitHub API for the tools that publish an official repo, stamps the check date, and regenerates the tables. `--offline` regenerates without the network; `--check` exits non-zero if the README has drifted from the data.
- [`.github/workflows/refresh.yml`](.github/workflows/refresh.yml) runs it weekly and on manual dispatch, and commits only when the data actually changed.
- Prices are deliberately not stored as numbers. A stale price in a comparison table is worse than no price, so the table links to each vendor's own pricing page.

## Contributing

Corrections and additions are welcome, including corrections to the entry for the tool that maintains this list. Open an issue with the tool name, a working link, one line on what it does that the tools already listed do not, and one line on where it stops. Entries are judged on whether they are usable today, not on popularity. Full rules in [CONTRIBUTING.md](CONTRIBUTING.md).

## License

[CC0 1.0 Universal](LICENSE), public domain. Take the data, fork the list, no attribution required.

---

Maintained by [a1adams](https://github.com/a1adams).
