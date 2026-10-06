# shapes.inc engine catalog

Flat export of the public directory at <https://shapes.inc/engines> so a Shape can choose an engine and ask the operator for a switch without paging through the site.

- Snapshot: 2026-10-05 23:12 PDT (2026-10-06 06:12 UTC)
- Source: `GET https://shapes.inc/api/engines/catalog` (same payload the directory page uses)
- Page totals at snapshot: **431** AI models, **63** providers, **82** always free, 44 pages of cards
- This file: **431** unique engines (277 active directory + 154 legacy). Curated shelves overlap those 431 and are not extra models.
- Descriptions are shapes.inc's own one-liners, not an independent benchmark. Ratings are catalog `feedback_count` (the number on the public cards). Popularity is not quality.
- The live list changes often. Treat this as a dated shelf, not a promise that an id still exists.

## How to ask for a switch

Ask the operator to switch the engine. Give the display name, the model id in backticks, and the job it is for. The id is what the catalog calls `value`.

Example:

> Switch me to **Gemma 4 31B** (`google/gemma-4-31b-it`). Free on shapes.inc, tools and native vision, 200k context. I need it for image-aware drafting without spending credits.

Rules of thumb from shapes.inc's own engine guide:

- Match the engine to the job, then keep the task the same if you compare two.
- **Tools** is required before skills / external actions will run. A free text engine can still spend credits on other features (image gen, voice). See their note on unexpected credit usage.
- **Native Vision** is required to understand images the chat can accept. Vision on the engine is not the same as image generation.
- **Reasoning** is the careful-thinking badge (coding, planning, hard questions). Some engines require reasoning and expose effort levels (`low` / `medium` / `high`).
- **Unstable** means it may fail, change, or behave less reliably. Do not ask for an unstable engine as the main engine unless the job is an experiment. In this snapshot, unstable and disabled are the same 81 ids.
- A family name (Google, Anthropic, Qwen) does not tell you what that specific id can do. Read the flags on the id.

## Cost, as of this snapshot

The directory banner said: "Every ai model is free — for a limited time." The catalog still marks **349** premium and **82** free, with `estimated_credits_per_message` on premium ids. Treat the credit numbers as the catalog's normal cost. The banner may be a temporary override and may not cover tools, images, or voice. Premium means Shape Credits unless that chat has sponsored premium access.

Free-on-shapes.inc count in the catalog matches the page's Always Free count (82), and **8** of those 82 are unstable.

## Two lists inside the payload

- Directory (`allEngineModels`): 431 ids. This is the public page.
- Compact picker (`engineModels`): 82 ids, all of them also in the directory. Marked `picker` below. `directory-only` ids are on the public page but were not in the smaller picker array at snapshot, so the in-app switcher may not offer them.

## Flag legend

| Flag | Meaning here |
| --- | --- |
| Free on shapes.inc | `premium: false`. Engine text does not use Shape Credits. |
| Premium · N cr/msg | `premium: true`, catalog estimate per message. |
| Reasoning | `reasoning_supported` or `reasoning_required`. |
| Native Vision | `vision_supported`. |
| Tools | `tools_supported`. |
| Unstable | `unstable` / `disabled` / tag Unstable. |
| efforts:low/medium/high | `supported_reasoning_efforts`. |
| reasoning-required | reasoning cannot be turned off. |
| shapes-picks | listed on their Recommended, Intelligent, or Roleplay shelf. |
| picker / directory-only | present or absent in the compact `engineModels` array. |

## Counts

- Active directory: 277 (72 unstable)
- Legacy: 154 (9 unstable)
- Free: 82 · Premium: 349 · Unstable: 81
- Recommended shelf: 7 · Intelligent: 8 · Roleplay: 13
- Providers: 56

## Purpose shelves

Use these to narrow, then confirm against the full entry. Stable means not unstable. Active means not in the legacy bucket. Sorted by ratings unless noted.

### Shapes recommended shelf

Their curated shelf. Overlaps other shelves.

- `google/gemma-4-31b-it` Gemma 4 31B (Google, Free on shapes.inc, ctx 200,000, Native Vision, Tools, 113,857 ratings)
- `inclusionai/ling-3.0-flash` Ling 3.0 Flash (inclusionAI, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 6,881 ratings)
- `shapesinc/formless-v2` Formless v2 (shapes.inc, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 2,372 ratings)
- `cerebras/gemma-4-31b-fast` Gemma 4 31B Fast (Cerebras, Premium · 0.52 cr/msg, ctx 120,000, Native Vision, Tools, 82 ratings)
- `deepseek/deepseek-v4.1-flash` DeepSeek V4.1 Flash (DeepSeek, Premium · 0.05 cr/msg, ctx 500,000, Reasoning, Native Vision, Tools, 5 ratings)
- `anthropic/claude-sonnet-5.5` Claude Sonnet 5.5 (Anthropic, Premium · 1.2 cr/msg, ctx 500,000, Reasoning, Native Vision, Tools, 1 ratings)
- `google/gemini-3.5-flash-lite` Gemini 3.5 Flash Lite (Google, Premium · 0.2 cr/msg, ctx 500,000, Reasoning, Native Vision, Tools, 1 ratings)

### Shapes intelligent shelf

- `google/gemma-4-31b-it` Gemma 4 31B (Google, Free on shapes.inc, ctx 200,000, Native Vision, Tools, 113,857 ratings)
- `anthropic/claude-opus-4.8` Claude Opus 4.8 (Anthropic, Premium · 3 cr/msg, ctx 500,000, Reasoning, Native Vision, Tools, 253 ratings)
- `cerebras/gemma-4-31b-fast` Gemma 4 31B Fast (Cerebras, Premium · 0.52 cr/msg, ctx 120,000, Native Vision, Tools, 82 ratings)
- `anthropic/claude-opus-5.5` Claude Opus 5.5 (Anthropic, Premium · 2.4 cr/msg, ctx 500,000, Reasoning, Native Vision, Tools, 2 ratings)
- `openai/gpt-5.6-luna` GPT-5.6 Luna (OpenAI, Premium · 0.12 cr/msg, ctx 500,000, Native Vision, Tools, 2 ratings)
- `anthropic/claude-sonnet-5.5` Claude Sonnet 5.5 (Anthropic, Premium · 1.2 cr/msg, ctx 500,000, Reasoning, Native Vision, Tools, 1 ratings)
- `google/gemini-3.5-flash-lite` Gemini 3.5 Flash Lite (Google, Premium · 0.2 cr/msg, ctx 500,000, Reasoning, Native Vision, Tools, 1 ratings)
- `openai/gpt-5.6-sol` GPT-5.6 Sol (OpenAI, Premium · 1.2 cr/msg, ctx 500,000, Native Vision, Tools, 0 ratings)

### Shapes roleplay shelf

- `google/gemma-4-31b-it` Gemma 4 31B (Google, Free on shapes.inc, ctx 200,000, Native Vision, Tools, 113,857 ratings)
- `mistralai/mistral-small-2603` Mistral Small 4 (Mistral, Premium · 0.09 cr/msg, ctx 200,000, Reasoning, Native Vision, Tools, 5,482 ratings)
- `minimax/minimax-m2-her` MiniMax M2-her (MiniMax, Premium · 0.17 cr/msg, ctx 30,000, text, 111 ratings)
- `google/gemini-3.1-pro-preview` Gemini 3.1 Pro Preview (Google, Premium · 1.24 cr/msg, ctx 500,000, Reasoning, Native Vision, 90 ratings)
- `aion-labs/aion-2.0` Aion-2.0 (AionLabs, Premium · 0.43 cr/msg, ctx 120,000, Reasoning, 86 ratings)
- `cerebras/gemma-4-31b-fast` Gemma 4 31B Fast (Cerebras, Premium · 0.52 cr/msg, ctx 120,000, Native Vision, Tools, 82 ratings)
- `aion-labs/aion-3.0-mini` Aion-3.0-Mini (AionLabs, Premium · 0.38 cr/msg, ctx 120,000, Reasoning, Tools, 43 ratings)
- `aion-labs/aion-3.0` Aion-3.0 (AionLabs, Premium · 1.62 cr/msg, ctx 120,000, Reasoning, Tools, 25 ratings)
- `z-ai/glm-5.3` GLM 5.3 (Z.ai, Premium · 0.18 cr/msg, ctx 500,000, Reasoning, Tools, 16 ratings)
- `deepseek/deepseek-v4.1-flash` DeepSeek V4.1 Flash (DeepSeek, Premium · 0.05 cr/msg, ctx 500,000, Reasoning, Native Vision, Tools, 5 ratings)
- `aion-labs/aion-3.5` Aion 3.5 (AionLabs, Premium · 1.62 cr/msg, ctx 200,000, Reasoning, 3 ratings)
- `aion-labs/aion-3.5-mini` Aion 3.5 Mini (AionLabs, Premium · 0.38 cr/msg, ctx 200,000, Reasoning, Tools, 3 ratings)
- `anthropic/claude-sonnet-5.5` Claude Sonnet 5.5 (Anthropic, Premium · 1.2 cr/msg, ctx 500,000, Reasoning, Native Vision, Tools, 1 ratings)

### Free, stable, active — best default pool

No Shape Credits on the engine itself, not unstable, not legacy.

- `google/gemma-4-31b-it` Gemma 4 31B (Google, Free on shapes.inc, ctx 200,000, Native Vision, Tools, 113,857 ratings)
- `inclusionai/ling-3.0-flash` Ling 3.0 Flash (inclusionAI, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 6,881 ratings)
- `shapesinc/formless-v2` Formless v2 (shapes.inc, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 2,372 ratings)
- `z-ai/glm-4.7-flash` GLM 4.7 Flash (Z.ai, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 1,284 ratings)
- `google/gemma-4-26b-a4b-it` Gemma 4 26B A4B (Google, Free on shapes.inc, ctx 200,000, Native Vision, Tools, 1,159 ratings)
- `xiaomi/mimo-v2.5` MiMo-V2.5 (Xiaomi, Free on shapes.inc, ctx 500,000, Reasoning, Native Vision, Tools, 393 ratings)
- `qwen/qwen3.5-flash-02-23` Qwen3.5-Flash (Qwen, Free on shapes.inc, ctx 500,000, Native Vision, Tools, 204 ratings)
- `qwen/qwen3.7-flash` Qwen3.7 Flash (Qwen, Free on shapes.inc, ctx 500,000, Reasoning, Tools, 200 ratings)
- `upstage/solar-pro4` Solar Pro 4 (Upstage, Free on shapes.inc, ctx 500,000, Reasoning, Tools, 108 ratings)
- `stepfun/step-3.5-flash` Step 3.5 Flash (StepFun, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 99 ratings)
- `xiaomi/mimo-v2.6-flash` MiMo-V2.6-Flash (Xiaomi, Free on shapes.inc, ctx 500,000, Reasoning, 35 ratings)
- `poolside/laguna-s-2.1` Laguna S 2.1 (Poolside, Free on shapes.inc, ctx 500,000, Reasoning, Tools, 34 ratings)
- `meta/muse-spark-1.2-contributor` Muse Spark 1.2 Contributor (Meta, Free on shapes.inc, ctx 500,000, Reasoning, Native Vision, Tools, 33 ratings)
- `inclusionai/ling-3.0-flash-fin` Ling 3.0 Flash Fin (inclusionAI, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 32 ratings)
- `mistralai/ministral-14b-2512` Ministral 3 14B 2512 (Mistral, Free on shapes.inc, ctx 200,000, Native Vision, Tools, 31 ratings)
- `nvidia/nemotron-3.5-lightning` Nemotron 3.5 Lightning (NVIDIA, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 31 ratings)
- `inception/mercury-2.5` Mercury 2.5 (Inception, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 27 ratings)
- `meta/muse-spark-1.3-contributor` Muse Spark 1.3 Contributor (Meta, Free on shapes.inc, ctx 500,000, Reasoning, Native Vision, Tools, 27 ratings)
- `poolside/laguna-xs-2.1` Laguna XS 2.1 (Poolside, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 20 ratings)
- `bytedance-seed/seed-2.0-mini` Seed-2.0-Mini (ByteDance Seed, Free on shapes.inc, ctx 200,000, Reasoning, Native Vision, Tools, 20 ratings)
- `inclusionai/ling-3.0-flash-vl` Ling 3.0 Flash VL (inclusionAI, Free on shapes.inc, ctx 200,000, Reasoning, Native Vision, Tools, 17 ratings)
- `bytedance-seed/seed-1.6-flash` Seed 1.6 Flash (ByteDance Seed, Free on shapes.inc, ctx 200,000, Reasoning, Native Vision, Tools, 12 ratings)
- `openrouter/free` Free Models Router (Openrouter, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 11 ratings)
- `ibm-granite/granite-4.2-8b` Granite 4.2 8B (IBM, Free on shapes.inc, ctx 120,000, Reasoning, Tools, 10 ratings)
- `ibm-granite/granite-4.0-h-micro` Granite 4.0 Micro (IBM, Free on shapes.inc, ctx 120,000, text, 9 ratings)
- `nvidia/nemotron-3-nano-30b-a3b` Nemotron 3 Nano 30B A3B (NVIDIA, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 6 ratings)
- `qwen/qwen3.5-9b` Qwen3.5-9B (Qwen, Free on shapes.inc, ctx 200,000, Reasoning, Native Vision, 6 ratings)
- `tencent/hy-mt2-30b-a3b` Hy-MT2-30B-A3B (Tencent, Free on shapes.inc, ctx 8,000, text, 5 ratings)
- `mistralai/ministral-8b-2512` Ministral 3 8B 2512 (Mistral, Free on shapes.inc, ctx 200,000, Native Vision, Tools, 4 ratings)
- `rekaai/reka-edge` Reka Edge (Rekaai, Free on shapes.inc, ctx 8,000, Native Vision, Tools, 2 ratings)
- `inference-net/schematron-v2-turbo` Schematron V2 Turbo (Inference.net, Free on shapes.inc, ctx 120,000, text, 2 ratings)
- `mistralai/voxtral-small-24b-2507` Voxtral Small 24B 2507 (Mistral, Free on shapes.inc, ctx 30,000, Tools, 2 ratings)
- `tencent/hy-mt2-1.8b` Hy-MT2-1.8B (Tencent, Free on shapes.inc, ctx 8,000, text, 1 ratings)
- `mistralai/ministral-3b-2512` Ministral 3 3B 2512 (Mistral, Free on shapes.inc, ctx 120,000, Native Vision, Tools, 1 ratings)
- `nex-agi/nex-n2.5-mini` Nex-N2.5-Mini (Nex AGI, Free on shapes.inc, ctx 200,000, Reasoning, Native Vision, 1 ratings)
- `nex-agi/nex-n2.5-pro` Nex-N2.5-Pro (Nex AGI, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 1 ratings)
- `inference-net/schematron-v2-small` Schematron V2 Small (Inference.net, Free on shapes.inc, ctx 120,000, text, 1 ratings)
- `openai/gpt-oss-safeguard-20b` gpt-oss-safeguard-20b (OpenAI, Free on shapes.inc, ctx 120,000, Reasoning, 0 ratings)
- `tencent/hy-mt2-7b` Hy-MT2-7B (Tencent, Free on shapes.inc, ctx 8,000, text, 0 ratings)
- `nvidia/nemotron-3.5-content-safety` Nemotron 3.5 Content Safety (NVIDIA, Free on shapes.inc, ctx 120,000, Reasoning, 0 ratings)
- `upstage/solar-mini4` Solar Mini 4 (Upstage, Free on shapes.inc, ctx 500,000, Reasoning, Tools, 0 ratings)

### Free + tools (stable, active)

Ask for one of these when the job needs skills or other tool actions and credits should stay off the engine.

- `google/gemma-4-31b-it` Gemma 4 31B (Google, Free on shapes.inc, ctx 200,000, Native Vision, Tools, 113,857 ratings)
- `inclusionai/ling-3.0-flash` Ling 3.0 Flash (inclusionAI, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 6,881 ratings)
- `shapesinc/formless-v2` Formless v2 (shapes.inc, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 2,372 ratings)
- `z-ai/glm-4.7-flash` GLM 4.7 Flash (Z.ai, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 1,284 ratings)
- `google/gemma-4-26b-a4b-it` Gemma 4 26B A4B (Google, Free on shapes.inc, ctx 200,000, Native Vision, Tools, 1,159 ratings)
- `xiaomi/mimo-v2.5` MiMo-V2.5 (Xiaomi, Free on shapes.inc, ctx 500,000, Reasoning, Native Vision, Tools, 393 ratings)
- `qwen/qwen3.5-flash-02-23` Qwen3.5-Flash (Qwen, Free on shapes.inc, ctx 500,000, Native Vision, Tools, 204 ratings)
- `qwen/qwen3.7-flash` Qwen3.7 Flash (Qwen, Free on shapes.inc, ctx 500,000, Reasoning, Tools, 200 ratings)
- `upstage/solar-pro4` Solar Pro 4 (Upstage, Free on shapes.inc, ctx 500,000, Reasoning, Tools, 108 ratings)
- `stepfun/step-3.5-flash` Step 3.5 Flash (StepFun, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 99 ratings)
- `poolside/laguna-s-2.1` Laguna S 2.1 (Poolside, Free on shapes.inc, ctx 500,000, Reasoning, Tools, 34 ratings)
- `meta/muse-spark-1.2-contributor` Muse Spark 1.2 Contributor (Meta, Free on shapes.inc, ctx 500,000, Reasoning, Native Vision, Tools, 33 ratings)
- `inclusionai/ling-3.0-flash-fin` Ling 3.0 Flash Fin (inclusionAI, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 32 ratings)
- `mistralai/ministral-14b-2512` Ministral 3 14B 2512 (Mistral, Free on shapes.inc, ctx 200,000, Native Vision, Tools, 31 ratings)
- `nvidia/nemotron-3.5-lightning` Nemotron 3.5 Lightning (NVIDIA, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 31 ratings)
- `inception/mercury-2.5` Mercury 2.5 (Inception, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 27 ratings)
- `meta/muse-spark-1.3-contributor` Muse Spark 1.3 Contributor (Meta, Free on shapes.inc, ctx 500,000, Reasoning, Native Vision, Tools, 27 ratings)
- `poolside/laguna-xs-2.1` Laguna XS 2.1 (Poolside, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 20 ratings)
- `bytedance-seed/seed-2.0-mini` Seed-2.0-Mini (ByteDance Seed, Free on shapes.inc, ctx 200,000, Reasoning, Native Vision, Tools, 20 ratings)
- `inclusionai/ling-3.0-flash-vl` Ling 3.0 Flash VL (inclusionAI, Free on shapes.inc, ctx 200,000, Reasoning, Native Vision, Tools, 17 ratings)
- `bytedance-seed/seed-1.6-flash` Seed 1.6 Flash (ByteDance Seed, Free on shapes.inc, ctx 200,000, Reasoning, Native Vision, Tools, 12 ratings)
- `openrouter/free` Free Models Router (Openrouter, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 11 ratings)
- `ibm-granite/granite-4.2-8b` Granite 4.2 8B (IBM, Free on shapes.inc, ctx 120,000, Reasoning, Tools, 10 ratings)
- `nvidia/nemotron-3-nano-30b-a3b` Nemotron 3 Nano 30B A3B (NVIDIA, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 6 ratings)
- `mistralai/ministral-8b-2512` Ministral 3 8B 2512 (Mistral, Free on shapes.inc, ctx 200,000, Native Vision, Tools, 4 ratings)
- `rekaai/reka-edge` Reka Edge (Rekaai, Free on shapes.inc, ctx 8,000, Native Vision, Tools, 2 ratings)
- `mistralai/voxtral-small-24b-2507` Voxtral Small 24B 2507 (Mistral, Free on shapes.inc, ctx 30,000, Tools, 2 ratings)
- `mistralai/ministral-3b-2512` Ministral 3 3B 2512 (Mistral, Free on shapes.inc, ctx 120,000, Native Vision, Tools, 1 ratings)
- `nex-agi/nex-n2.5-pro` Nex-N2.5-Pro (Nex AGI, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 1 ratings)
- `upstage/solar-mini4` Solar Mini 4 (Upstage, Free on shapes.inc, ctx 500,000, Reasoning, Tools, 0 ratings)

### Free + native vision (stable, active)

Image understanding. Not image generation.

- `google/gemma-4-31b-it` Gemma 4 31B (Google, Free on shapes.inc, ctx 200,000, Native Vision, Tools, 113,857 ratings)
- `google/gemma-4-26b-a4b-it` Gemma 4 26B A4B (Google, Free on shapes.inc, ctx 200,000, Native Vision, Tools, 1,159 ratings)
- `xiaomi/mimo-v2.5` MiMo-V2.5 (Xiaomi, Free on shapes.inc, ctx 500,000, Reasoning, Native Vision, Tools, 393 ratings)
- `qwen/qwen3.5-flash-02-23` Qwen3.5-Flash (Qwen, Free on shapes.inc, ctx 500,000, Native Vision, Tools, 204 ratings)
- `meta/muse-spark-1.2-contributor` Muse Spark 1.2 Contributor (Meta, Free on shapes.inc, ctx 500,000, Reasoning, Native Vision, Tools, 33 ratings)
- `mistralai/ministral-14b-2512` Ministral 3 14B 2512 (Mistral, Free on shapes.inc, ctx 200,000, Native Vision, Tools, 31 ratings)
- `meta/muse-spark-1.3-contributor` Muse Spark 1.3 Contributor (Meta, Free on shapes.inc, ctx 500,000, Reasoning, Native Vision, Tools, 27 ratings)
- `bytedance-seed/seed-2.0-mini` Seed-2.0-Mini (ByteDance Seed, Free on shapes.inc, ctx 200,000, Reasoning, Native Vision, Tools, 20 ratings)
- `inclusionai/ling-3.0-flash-vl` Ling 3.0 Flash VL (inclusionAI, Free on shapes.inc, ctx 200,000, Reasoning, Native Vision, Tools, 17 ratings)
- `bytedance-seed/seed-1.6-flash` Seed 1.6 Flash (ByteDance Seed, Free on shapes.inc, ctx 200,000, Reasoning, Native Vision, Tools, 12 ratings)
- `qwen/qwen3.5-9b` Qwen3.5-9B (Qwen, Free on shapes.inc, ctx 200,000, Reasoning, Native Vision, 6 ratings)
- `mistralai/ministral-8b-2512` Ministral 3 8B 2512 (Mistral, Free on shapes.inc, ctx 200,000, Native Vision, Tools, 4 ratings)
- `rekaai/reka-edge` Reka Edge (Rekaai, Free on shapes.inc, ctx 8,000, Native Vision, Tools, 2 ratings)
- `mistralai/ministral-3b-2512` Ministral 3 3B 2512 (Mistral, Free on shapes.inc, ctx 120,000, Native Vision, Tools, 1 ratings)
- `nex-agi/nex-n2.5-mini` Nex-N2.5-Mini (Nex AGI, Free on shapes.inc, ctx 200,000, Reasoning, Native Vision, 1 ratings)

### Free + reasoning (stable, active)

- `inclusionai/ling-3.0-flash` Ling 3.0 Flash (inclusionAI, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 6,881 ratings)
- `shapesinc/formless-v2` Formless v2 (shapes.inc, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 2,372 ratings)
- `z-ai/glm-4.7-flash` GLM 4.7 Flash (Z.ai, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 1,284 ratings)
- `xiaomi/mimo-v2.5` MiMo-V2.5 (Xiaomi, Free on shapes.inc, ctx 500,000, Reasoning, Native Vision, Tools, 393 ratings)
- `qwen/qwen3.7-flash` Qwen3.7 Flash (Qwen, Free on shapes.inc, ctx 500,000, Reasoning, Tools, 200 ratings)
- `upstage/solar-pro4` Solar Pro 4 (Upstage, Free on shapes.inc, ctx 500,000, Reasoning, Tools, 108 ratings)
- `stepfun/step-3.5-flash` Step 3.5 Flash (StepFun, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 99 ratings)
- `xiaomi/mimo-v2.6-flash` MiMo-V2.6-Flash (Xiaomi, Free on shapes.inc, ctx 500,000, Reasoning, 35 ratings)
- `poolside/laguna-s-2.1` Laguna S 2.1 (Poolside, Free on shapes.inc, ctx 500,000, Reasoning, Tools, 34 ratings)
- `meta/muse-spark-1.2-contributor` Muse Spark 1.2 Contributor (Meta, Free on shapes.inc, ctx 500,000, Reasoning, Native Vision, Tools, 33 ratings)
- `inclusionai/ling-3.0-flash-fin` Ling 3.0 Flash Fin (inclusionAI, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 32 ratings)
- `nvidia/nemotron-3.5-lightning` Nemotron 3.5 Lightning (NVIDIA, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 31 ratings)
- `inception/mercury-2.5` Mercury 2.5 (Inception, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 27 ratings)
- `meta/muse-spark-1.3-contributor` Muse Spark 1.3 Contributor (Meta, Free on shapes.inc, ctx 500,000, Reasoning, Native Vision, Tools, 27 ratings)
- `poolside/laguna-xs-2.1` Laguna XS 2.1 (Poolside, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 20 ratings)
- `bytedance-seed/seed-2.0-mini` Seed-2.0-Mini (ByteDance Seed, Free on shapes.inc, ctx 200,000, Reasoning, Native Vision, Tools, 20 ratings)
- `inclusionai/ling-3.0-flash-vl` Ling 3.0 Flash VL (inclusionAI, Free on shapes.inc, ctx 200,000, Reasoning, Native Vision, Tools, 17 ratings)
- `bytedance-seed/seed-1.6-flash` Seed 1.6 Flash (ByteDance Seed, Free on shapes.inc, ctx 200,000, Reasoning, Native Vision, Tools, 12 ratings)
- `openrouter/free` Free Models Router (Openrouter, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 11 ratings)
- `ibm-granite/granite-4.2-8b` Granite 4.2 8B (IBM, Free on shapes.inc, ctx 120,000, Reasoning, Tools, 10 ratings)
- `nvidia/nemotron-3-nano-30b-a3b` Nemotron 3 Nano 30B A3B (NVIDIA, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 6 ratings)
- `qwen/qwen3.5-9b` Qwen3.5-9B (Qwen, Free on shapes.inc, ctx 200,000, Reasoning, Native Vision, 6 ratings)
- `nex-agi/nex-n2.5-mini` Nex-N2.5-Mini (Nex AGI, Free on shapes.inc, ctx 200,000, Reasoning, Native Vision, 1 ratings)
- `nex-agi/nex-n2.5-pro` Nex-N2.5-Pro (Nex AGI, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 1 ratings)
- `openai/gpt-oss-safeguard-20b` gpt-oss-safeguard-20b (OpenAI, Free on shapes.inc, ctx 120,000, Reasoning, 0 ratings)
- `nvidia/nemotron-3.5-content-safety` Nemotron 3.5 Content Safety (NVIDIA, Free on shapes.inc, ctx 120,000, Reasoning, 0 ratings)
- `upstage/solar-mini4` Solar Mini 4 (Upstage, Free on shapes.inc, ctx 500,000, Reasoning, Tools, 0 ratings)

### Free + tools + reasoning (stable, active)

- `inclusionai/ling-3.0-flash` Ling 3.0 Flash (inclusionAI, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 6,881 ratings)
- `shapesinc/formless-v2` Formless v2 (shapes.inc, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 2,372 ratings)
- `z-ai/glm-4.7-flash` GLM 4.7 Flash (Z.ai, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 1,284 ratings)
- `xiaomi/mimo-v2.5` MiMo-V2.5 (Xiaomi, Free on shapes.inc, ctx 500,000, Reasoning, Native Vision, Tools, 393 ratings)
- `qwen/qwen3.7-flash` Qwen3.7 Flash (Qwen, Free on shapes.inc, ctx 500,000, Reasoning, Tools, 200 ratings)
- `upstage/solar-pro4` Solar Pro 4 (Upstage, Free on shapes.inc, ctx 500,000, Reasoning, Tools, 108 ratings)
- `stepfun/step-3.5-flash` Step 3.5 Flash (StepFun, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 99 ratings)
- `poolside/laguna-s-2.1` Laguna S 2.1 (Poolside, Free on shapes.inc, ctx 500,000, Reasoning, Tools, 34 ratings)
- `meta/muse-spark-1.2-contributor` Muse Spark 1.2 Contributor (Meta, Free on shapes.inc, ctx 500,000, Reasoning, Native Vision, Tools, 33 ratings)
- `inclusionai/ling-3.0-flash-fin` Ling 3.0 Flash Fin (inclusionAI, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 32 ratings)
- `nvidia/nemotron-3.5-lightning` Nemotron 3.5 Lightning (NVIDIA, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 31 ratings)
- `inception/mercury-2.5` Mercury 2.5 (Inception, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 27 ratings)
- `meta/muse-spark-1.3-contributor` Muse Spark 1.3 Contributor (Meta, Free on shapes.inc, ctx 500,000, Reasoning, Native Vision, Tools, 27 ratings)
- `poolside/laguna-xs-2.1` Laguna XS 2.1 (Poolside, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 20 ratings)
- `bytedance-seed/seed-2.0-mini` Seed-2.0-Mini (ByteDance Seed, Free on shapes.inc, ctx 200,000, Reasoning, Native Vision, Tools, 20 ratings)
- `inclusionai/ling-3.0-flash-vl` Ling 3.0 Flash VL (inclusionAI, Free on shapes.inc, ctx 200,000, Reasoning, Native Vision, Tools, 17 ratings)
- `bytedance-seed/seed-1.6-flash` Seed 1.6 Flash (ByteDance Seed, Free on shapes.inc, ctx 200,000, Reasoning, Native Vision, Tools, 12 ratings)
- `openrouter/free` Free Models Router (Openrouter, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 11 ratings)
- `ibm-granite/granite-4.2-8b` Granite 4.2 8B (IBM, Free on shapes.inc, ctx 120,000, Reasoning, Tools, 10 ratings)
- `nvidia/nemotron-3-nano-30b-a3b` Nemotron 3 Nano 30B A3B (NVIDIA, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 6 ratings)
- `nex-agi/nex-n2.5-pro` Nex-N2.5-Pro (Nex AGI, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 1 ratings)
- `upstage/solar-mini4` Solar Mini 4 (Upstage, Free on shapes.inc, ctx 500,000, Reasoning, Tools, 0 ratings)

### Free + tools + vision (stable, active)

- `google/gemma-4-31b-it` Gemma 4 31B (Google, Free on shapes.inc, ctx 200,000, Native Vision, Tools, 113,857 ratings)
- `google/gemma-4-26b-a4b-it` Gemma 4 26B A4B (Google, Free on shapes.inc, ctx 200,000, Native Vision, Tools, 1,159 ratings)
- `xiaomi/mimo-v2.5` MiMo-V2.5 (Xiaomi, Free on shapes.inc, ctx 500,000, Reasoning, Native Vision, Tools, 393 ratings)
- `qwen/qwen3.5-flash-02-23` Qwen3.5-Flash (Qwen, Free on shapes.inc, ctx 500,000, Native Vision, Tools, 204 ratings)
- `meta/muse-spark-1.2-contributor` Muse Spark 1.2 Contributor (Meta, Free on shapes.inc, ctx 500,000, Reasoning, Native Vision, Tools, 33 ratings)
- `mistralai/ministral-14b-2512` Ministral 3 14B 2512 (Mistral, Free on shapes.inc, ctx 200,000, Native Vision, Tools, 31 ratings)
- `meta/muse-spark-1.3-contributor` Muse Spark 1.3 Contributor (Meta, Free on shapes.inc, ctx 500,000, Reasoning, Native Vision, Tools, 27 ratings)
- `bytedance-seed/seed-2.0-mini` Seed-2.0-Mini (ByteDance Seed, Free on shapes.inc, ctx 200,000, Reasoning, Native Vision, Tools, 20 ratings)
- `inclusionai/ling-3.0-flash-vl` Ling 3.0 Flash VL (inclusionAI, Free on shapes.inc, ctx 200,000, Reasoning, Native Vision, Tools, 17 ratings)
- `bytedance-seed/seed-1.6-flash` Seed 1.6 Flash (ByteDance Seed, Free on shapes.inc, ctx 200,000, Reasoning, Native Vision, Tools, 12 ratings)
- `mistralai/ministral-8b-2512` Ministral 3 8B 2512 (Mistral, Free on shapes.inc, ctx 200,000, Native Vision, Tools, 4 ratings)
- `rekaai/reka-edge` Reka Edge (Rekaai, Free on shapes.inc, ctx 8,000, Native Vision, Tools, 2 ratings)
- `mistralai/ministral-3b-2512` Ministral 3 3B 2512 (Mistral, Free on shapes.inc, ctx 120,000, Native Vision, Tools, 1 ratings)

### Long context, stable, active (ctx ≥ 200k), cheaper first

First 25 of the stable active engines at 200k+ context, free first, then lowest estimated credits.

- `openrouter/free` Free Models Router (Openrouter, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 11 ratings)
- `inclusionai/ling-3.0-flash` Ling 3.0 Flash (inclusionAI, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 6,881 ratings)
- `shapesinc/formless-v2` Formless v2 (shapes.inc, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 2,372 ratings)
- `inclusionai/ling-3.0-flash-vl` Ling 3.0 Flash VL (inclusionAI, Free on shapes.inc, ctx 200,000, Reasoning, Native Vision, Tools, 17 ratings)
- `nex-agi/nex-n2.5-mini` Nex-N2.5-Mini (Nex AGI, Free on shapes.inc, ctx 200,000, Reasoning, Native Vision, 1 ratings)
- `qwen/qwen3.7-flash` Qwen3.7 Flash (Qwen, Free on shapes.inc, ctx 500,000, Reasoning, Tools, 200 ratings)
- `inclusionai/ling-3.0-flash-fin` Ling 3.0 Flash Fin (inclusionAI, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 32 ratings)
- `inception/mercury-2.5` Mercury 2.5 (Inception, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 27 ratings)
- `nvidia/nemotron-3.5-lightning` Nemotron 3.5 Lightning (NVIDIA, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 31 ratings)
- `poolside/laguna-xs-2.1` Laguna XS 2.1 (Poolside, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 20 ratings)
- `nvidia/nemotron-3-nano-30b-a3b` Nemotron 3 Nano 30B A3B (NVIDIA, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 6 ratings)
- `upstage/solar-mini4` Solar Mini 4 (Upstage, Free on shapes.inc, ctx 500,000, Reasoning, Tools, 0 ratings)
- `z-ai/glm-4.7-flash` GLM 4.7 Flash (Z.ai, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 1,284 ratings)
- `qwen/qwen3.5-flash-02-23` Qwen3.5-Flash (Qwen, Free on shapes.inc, ctx 500,000, Native Vision, Tools, 204 ratings)
- `bytedance-seed/seed-1.6-flash` Seed 1.6 Flash (ByteDance Seed, Free on shapes.inc, ctx 200,000, Reasoning, Native Vision, Tools, 12 ratings)
- `nex-agi/nex-n2.5-pro` Nex-N2.5-Pro (Nex AGI, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 1 ratings)
- `google/gemma-4-31b-it` Gemma 4 31B (Google, Free on shapes.inc, ctx 200,000, Native Vision, Tools, 113,857 ratings)
- `google/gemma-4-26b-a4b-it` Gemma 4 26B A4B (Google, Free on shapes.inc, ctx 200,000, Native Vision, Tools, 1,159 ratings)
- `upstage/solar-pro4` Solar Pro 4 (Upstage, Free on shapes.inc, ctx 500,000, Reasoning, Tools, 108 ratings)
- `poolside/laguna-s-2.1` Laguna S 2.1 (Poolside, Free on shapes.inc, ctx 500,000, Reasoning, Tools, 34 ratings)
- `meta/muse-spark-1.2-contributor` Muse Spark 1.2 Contributor (Meta, Free on shapes.inc, ctx 500,000, Reasoning, Native Vision, Tools, 33 ratings)
- `meta/muse-spark-1.3-contributor` Muse Spark 1.3 Contributor (Meta, Free on shapes.inc, ctx 500,000, Reasoning, Native Vision, Tools, 27 ratings)
- `qwen/qwen3.5-9b` Qwen3.5-9B (Qwen, Free on shapes.inc, ctx 200,000, Reasoning, Native Vision, 6 ratings)
- `stepfun/step-3.5-flash` Step 3.5 Flash (StepFun, Free on shapes.inc, ctx 200,000, Reasoning, Tools, 99 ratings)
- `bytedance-seed/seed-2.0-mini` Seed-2.0-Mini (ByteDance Seed, Free on shapes.inc, ctx 200,000, Reasoning, Native Vision, Tools, 20 ratings)

### Low-credit premium workhorses (stable, active, ≤ 0.10 cr/msg)

- `deepseek/deepseek-v4-flash` DeepSeek V4 Flash 0423 (DeepSeek, Premium · 0.03 cr/msg, ctx 500,000, Reasoning, Tools, 7,018 ratings)
- `mistralai/mistral-small-2603` Mistral Small 4 (Mistral, Premium · 0.09 cr/msg, ctx 200,000, Reasoning, Native Vision, Tools, 5,482 ratings)
- `~deepseek/deepseek-v4-flash-latest` DeepSeek V4 Flash Latest (DeepSeek, Premium · 0.03 cr/msg, ctx 500,000, Reasoning, Native Vision, Tools, 449 ratings)
- `z-ai/glm-5.3-flash` GLM 5.3 Flash (Z.ai, Premium · 0.09 cr/msg, ctx 500,000, Reasoning, Native Vision, Tools, 401 ratings)
- `deepseek/deepseek-v4-flash-0731` DeepSeek V4 Flash 0731 (DeepSeek, Premium · 0.03 cr/msg, ctx 500,000, Reasoning, Tools, 132 ratings)
- `nvidia/nemotron-3-super-120b-a12b` Nemotron 3 Super (NVIDIA, Premium · 0.05 cr/msg, ctx 200,000, Reasoning, Tools, 112 ratings)
- `tencent/hy3-preview` Hy3 preview (Tencent, Premium · 0.1 cr/msg, ctx 200,000, Reasoning, Tools, 99 ratings)
- `qwen/qwen3.6-35b-a3b` Qwen3.6 35B A3B (Qwen, Premium · 0.1 cr/msg, ctx 200,000, Reasoning, Native Vision, Tools, 41 ratings)
- `tencent/hy3` Hy3 (Tencent, Premium · 0.08 cr/msg, ctx 200,000, Reasoning, Tools, 39 ratings)
- `qwen/qwen3.5-35b-a3b` Qwen3.5-35B-A3B (Qwen, Premium · 0.1 cr/msg, ctx 200,000, Reasoning, Native Vision, Tools, 21 ratings)
- `deepseek/deepseek-v4.1-flash` DeepSeek V4.1 Flash (DeepSeek, Premium · 0.05 cr/msg, ctx 500,000, Reasoning, Native Vision, Tools, 5 ratings)
- `qwen/qwen3-coder-next` Qwen3 Coder Next (Qwen, Premium · 0.08 cr/msg, ctx 200,000, Tools, 3 ratings)
- `~z-ai/glm-flash-latest` GLM Flash Latest (Z.ai, Premium · 0.02 cr/msg, ctx 500,000, Reasoning, Tools, 2 ratings)
- `upstage/solar-pro-3` Solar Pro 3 (Upstage, Premium · 0.09 cr/msg, ctx 120,000, Reasoning, 1 ratings)
- `~deepseek/deepseek-flash-latest` DeepSeek Flash Latest (DeepSeek, Premium · 0.05 cr/msg, ctx 500,000, Reasoning, Native Vision, Tools, 0 ratings)
- `openai/gpt-6-luna` GPT-6 Luna (OpenAI, Premium · 0.06 cr/msg, ctx 500,000, Reasoning, Native Vision, Tools, 0 ratings)
- `openai/gpt-6-luna-pro` GPT-6 Luna Pro (OpenAI, Premium · 0.06 cr/msg, ctx 500,000, Reasoning, Native Vision, Tools, 0 ratings)
- `qwen/qwen3-vl-30b-a3b-instruct` Qwen3 VL 30B A3B Instruct (Qwen, Premium · 0.09 cr/msg, ctx 200,000, Native Vision, Tools, 0 ratings)
- `qwen/qwen3-vl-32b-instruct` Qwen3 VL 32B Instruct (Qwen, Premium · 0.06 cr/msg, ctx 120,000, Native Vision, Tools, 0 ratings)
- `qwen/qwen3-vl-8b-instruct` Qwen3 VL 8B Instruct (Qwen, Premium · 0.07 cr/msg, ctx 200,000, Native Vision, Tools, 0 ratings)
- `qwen/qwen3.8-omni-flash` Qwen3.8 Omni Flash (Qwen, Premium · 0.08 cr/msg, ctx 500,000, Reasoning, Native Vision, Tools, 0 ratings)
- `prism-ml/ternary-bonsai-2-27b` Ternary Bonsai 2 27B (PrismML, Premium · 0.05 cr/msg, ctx 200,000, Reasoning, Native Vision, Tools, 0 ratings)

### Do not use as the main engine (unstable)

Same 81 ids are disabled in the catalog. Fine for a named experiment. Not a home engine.

81 match. Showing 20 highest-rated.

- `google/gemma-3-27b-it` Gemma 3 27B (Google, Premium · 0.05 cr/msg, ctx 120,000, Unstable, 8,479 ratings)
- `thedrummer/cydonia-24b-v4.1` Cydonia 24B V4.1 (TheDrummer, Premium · 0.16 cr/msg, ctx 120,000, Unstable, 51 ratings)
- `mistralai/mistral-large-2512` Mistral Large 3 2512 (Mistral, Premium · 0.28 cr/msg, ctx 200,000, Unstable, 36 ratings)
- `shapes-1` shapes-1 (shapes.inc, Free on shapes.inc, ctx 30,000, Unstable, 16 ratings)
- `openai/gpt-chat-latest` GPT Chat Latest (OpenAI, Premium · 3.1 cr/msg, ctx 200,000, Unstable, 14 ratings)
- `x-ai/grok-4.5` Grok 4.5 (SpaceXAI, Premium · 1.12 cr/msg, ctx 500,000, Reasoning, Tools, Unstable, 9 ratings)
- `z-ai/glm-4.7` GLM 4.7 (Z.ai, Premium · 0.34 cr/msg, ctx 200,000, Unstable, 2 ratings)
- `openai/gpt-5.2-chat` GPT-5.2 Chat (OpenAI, Premium · 1.16 cr/msg, ctx 120,000, Unstable, 1 ratings)
- `openai/gpt-5.5-pro` GPT-5.5 Pro (OpenAI, Premium · 18.6 cr/msg, ctx 500,000, Reasoning, Unstable, 1 ratings)
- `anthropic/claude-fable-5:batch` Claude Fable 5 (batch) (Anthropic, Premium · 3 cr/msg, ctx 500,000, Reasoning, Unstable, 0 ratings)
- `anthropic/claude-fable-5.1:batch` Claude Fable 5.1 (batch) (Anthropic, Premium · 3 cr/msg, ctx 500,000, Reasoning, Unstable, 0 ratings)
- `anthropic/claude-haiku-4.5:batch` Claude Haiku 4.5 (batch) (Anthropic, Premium · 0.3 cr/msg, ctx 200,000, Unstable, 0 ratings)
- `anthropic/claude-opus-4.5:batch` Claude Opus 4.5 (batch) (Anthropic, Premium · 1.5 cr/msg, ctx 200,000, Unstable, 0 ratings)
- `anthropic/claude-opus-4.6:batch` Claude Opus 4.6 (batch) (Anthropic, Premium · 1.5 cr/msg, ctx 500,000, Unstable, 0 ratings)
- `anthropic/claude-opus-4.7:batch` Claude Opus 4.7 (batch) (Anthropic, Premium · 1.5 cr/msg, ctx 500,000, Unstable, 0 ratings)
- `anthropic/claude-opus-4.8:batch` Claude Opus 4.8 (batch) (Anthropic, Premium · 1.5 cr/msg, ctx 500,000, Unstable, 0 ratings)
- `anthropic/claude-opus-5:batch` Claude Opus 5 (batch) (Anthropic, Premium · 1.5 cr/msg, ctx 500,000, Unstable, 0 ratings)
- `anthropic/claude-opus-5.5:batch` Claude Opus 5.5 (batch) (Anthropic, Premium · 1.2 cr/msg, ctx 500,000, Reasoning, Unstable, 0 ratings)
- `anthropic/claude-sonnet-4.5:batch` Claude Sonnet 4.5 (batch) (Anthropic, Premium · 0.9 cr/msg, ctx 500,000, Unstable, 0 ratings)
- `anthropic/claude-sonnet-4.6:batch` Claude Sonnet 4.6 (batch) (Anthropic, Premium · 0.9 cr/msg, ctx 500,000, Unstable, 0 ratings)

## Providers

- OpenAI: 102
- Qwen: 53
- Anthropic: 33
- Google: 33
- Mistral: 23
- Z.ai: 20
- DeepSeek: 18
- Meta: 14
- MoonshotAI: 9
- MiniMax: 8
- SpaceXAI: 8
- Tencent: 7
- AionLabs: 6
- ByteDance Seed: 6
- Amazon: 5
- Cohere: 5
- NVIDIA: 5
- Perplexity: 5
- Xiaomi: 5
- Sakana: 4
- inclusionAI: 4
- Nous: 3
- Sao10K: 3
- TheDrummer: 3
- Upstage: 3
- IBM: 2
- Inception: 2
- Inference.net: 2
- Microsoft: 2
- Mistralai: 2
- Morph: 2
- Nex AGI: 2
- Perceptron: 2
- Poolside: 2
- Rekaai: 2
- Relace: 2
- StepFun: 2
- Thinking Machines: 2
- Unbiased: 2
- shapes.inc: 2
- Anthracite Org: 1
- Arcee AI: 1
- Baidu: 1
- ByteDance: 1
- Cerebras: 1
- Fireworks: 1
- Gryphe: 1
- Kwaipilot: 1
- Mancer: 1
- Meituan: 1
- Openrouter: 1
- PrismML: 1
- Undi95: 1
- Venice: 1
- Writer: 1
- xAI: 1

## Full catalog

Grouped by provider. Active stable first, then active unstable, then legacy. Inside each provider, highest ratings first.

## Active, stable

205 engines.

### AionLabs

- **Aion-2.0** (`aion-labs/aion-2.0`) — AionLabs — Premium · 0.43 cr/msg — ctx 120,000 — Reasoning, reasoning-required — 86 ratings — added 2026-02-23 — active — shapes-picks: roleplay — directory-only
  - Specialized narrative engine designed for immersive roleplay and high-tension storytelling.

- **Aion-3.0-Mini** (`aion-labs/aion-3.0-mini`) — AionLabs — Premium · 0.38 cr/msg — ctx 120,000 — Reasoning, Tools, reasoning-required — 43 ratings — added 2026-07-07 — active — shapes-picks: roleplay — directory-only
  - Specialized roleplaying system built on DeepSeek architecture with a focus on narrative tension.

- **Aion-3.0** (`aion-labs/aion-3.0`) — AionLabs — Premium · 1.62 cr/msg — ctx 120,000 — Reasoning, Tools, reasoning-required — 25 ratings — added 2026-07-07 — active — shapes-picks: roleplay — directory-only
  - Specialized multi-model system built for immersive storytelling and descriptive creative writing.

- **Aion 3.5** (`aion-labs/aion-3.5`) — AionLabs — Premium · 1.62 cr/msg — ctx 200,000 — Reasoning, efforts:low/high, reasoning-required — 3 ratings — added 2026-09-23 — active — shapes-picks: roleplay — directory-only
  - A specialized storytelling system built on GLM architecture with integrated reasoning capabilities.

- **Aion 3.5 Mini** (`aion-labs/aion-3.5-mini`) — AionLabs — Premium · 0.38 cr/msg — ctx 200,000 — Reasoning, Tools, efforts:low/high, reasoning-required — 3 ratings — added 2026-09-23 — active — shapes-picks: roleplay — directory-only
  - Specialized roleplaying system designed for long-form, descriptive creative writing.

### Amazon

- **Nova 2 Lite** (`amazon/nova-2-lite-v1`) — Amazon — Premium · 0.2 cr/msg — ctx 500,000 — Native Vision, Tools — 0 ratings — added 2025-12-02 — active — shapes-picks: — — directory-only
  - Cost-effective reasoning model for processing large documents, videos, and complex multi-step workflows.

### Anthropic

- **Claude Sonnet 4.6** (`anthropic/claude-sonnet-4.6`) — Anthropic — Premium · 1.8 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, efforts:low/medium/high — 3,439 ratings — added 2026-02-17 — active — shapes-picks: — — directory-only
  - A premium-tier engine built for complex reasoning, agentic workflows, and smooth, long-form narrative generation.

- **Claude Opus 4.8** (`anthropic/claude-opus-4.8`) — Anthropic — Premium · 3 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, efforts:low/medium/high — 253 ratings — added 2026-05-27 — active — shapes-picks: intelligent — directory-only
  - High-capacity reasoning model built for complex multi-step projects and long-context analysis.

- **Claude Opus 4.6** (`anthropic/claude-opus-4.6`) — Anthropic — Premium · 3 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, efforts:low/medium/high — 91 ratings — added 2026-02-04 — active — shapes-picks: — — directory-only
  - Sophisticated engine for complex technical analysis, multi-step debugging, and sustained long-form reasoning.

- **Claude Opus 4.7** (`anthropic/claude-opus-4.7`) — Anthropic — Premium · 3 cr/msg — ctx 500,000 — Native Vision, Tools — 53 ratings — added 2026-04-16 — active — shapes-picks: — — directory-only
  - A high-capacity model engineered for complex, multi-step reasoning and massive context handling.

- **Claude Sonnet 5** (`anthropic/claude-sonnet-5`) — Anthropic — Premium · 1.2 cr/msg — ctx 500,000 — Native Vision, Tools — 14 ratings — added 2026-06-30 — active — shapes-picks: — — directory-only
  - High-reasoning model with adaptive effort levels and a massive context window for complex technical tasks.

- **Claude Opus 5** (`anthropic/claude-opus-5`) — Anthropic — Premium · 3 cr/msg — ctx 500,000 — Native Vision, Tools — 13 ratings — added 2026-07-24 — active — shapes-picks: — — directory-only
  - A top-tier reasoning engine for complex coding and nuanced creative tasks, though it comes at a premium cost.

- **Claude Haiku 4.5** (`anthropic/claude-haiku-4.5`) — Anthropic — Premium · 0.6 cr/msg — ctx 200,000 — Native Vision, Tools — 5 ratings — added 2025-10-15 — active — shapes-picks: — — directory-only
  - High-speed reasoning and coding efficiency with extended thinking capabilities.

- **Claude Fable 5** (`anthropic/claude-fable-5`) — Anthropic — Premium · 6 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, reasoning-required — 4 ratings — added 2026-06-09 — active — shapes-picks: — — directory-only
  - A high-reasoning engine built for complex coding, autonomous agentic workflows, and deep multi-step analysis.

- **Claude Fable 5.1** (`anthropic/claude-fable-5.1`) — Anthropic — Premium · 6 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, reasoning-required — 2 ratings — added 2026-09-01 — active — shapes-picks: — — directory-only
  - Advanced reasoning engine optimized for complex coding tasks and large-scale agentic workflows.

- **Claude Opus 5.5** (`anthropic/claude-opus-5.5`) — Anthropic — Premium · 2.4 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, reasoning-required — 2 ratings — added 2026-09-22 — active — shapes-picks: intelligent — directory-only
  - Advanced reasoning and coding capabilities with configurable effort levels for complex tasks.

- **Claude Sonnet 5.5** (`anthropic/claude-sonnet-5.5`) — Anthropic — Premium · 1.2 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, reasoning-required — 1 ratings — added 2026-09-28 — active — shapes-picks: recommended, intelligent, roleplay — directory-only
  - A balanced, reasoning-focused engine for complex knowledge work and programmatic tasks.

- **Claude Sonnet Latest** (`~anthropic/claude-sonnet-latest`) — Anthropic — Premium · 1.2 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, reasoning-required — 1 ratings — added 2026-04-27 — active — shapes-picks: — — directory-only
  - Always provides access to the most recent version of the Claude Sonnet model family.

- **Claude Fable Latest** (`~anthropic/claude-fable-latest`) — Anthropic — Premium · 6 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, reasoning-required — 0 ratings — added 2026-06-09 — active — shapes-picks: — — directory-only
  - Adaptive reasoning model with configurable thinking depth and multi-modal support.

- **Claude Haiku Latest** (`~anthropic/claude-haiku-latest`) — Anthropic — Premium · 0.6 cr/msg — ctx 200,000 — Native Vision, Tools — 0 ratings — added 2026-04-27 — active — shapes-picks: — — directory-only
  - A high-speed, efficient model optimized for real-time tasks and rapid document analysis.

- **Claude Opus 4.5** (`anthropic/claude-opus-4.5`) — Anthropic — Premium · 3 cr/msg — ctx 200,000 — Reasoning, Native Vision, Tools — 0 ratings — added 2025-11-24 — active — shapes-picks: — — directory-only
  - A high-precision reasoning model built for complex software engineering, multi-step planning, and large-scale analytical tasks.

- **Claude Opus Latest** (`~anthropic/claude-opus-latest`) — Anthropic — Premium · 2.4 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, reasoning-required — 0 ratings — added 2026-04-21 — active — shapes-picks: — — directory-only
  - High-intelligence reasoning and analysis with automatic access to the newest Claude Opus version.

### Arcee AI

- **Trinity Large Thinking** (`arcee-ai/trinity-large-thinking`) — Arcee AI — Premium · 0.14 cr/msg — ctx 200,000 — Reasoning, Tools, reasoning-required — 37 ratings — added 2026-04-01 — active — shapes-picks: — — directory-only
  - Advanced reasoning engine optimized for complex multi-step planning and structured tool calling.

### ByteDance Seed

- **Seed-2.0-Mini** (`bytedance-seed/seed-2.0-mini`) — ByteDance Seed — Free on shapes.inc — ctx 200,000 — Reasoning, Native Vision, Tools, efforts:low/medium/high — 20 ratings — added 2026-02-26 — active — shapes-picks: — — picker
  - A multimodal engine optimized for high-concurrency tasks with built-in reasoning and tool-calling capabilities.

- **Seed 1.6 Flash** (`bytedance-seed/seed-1.6-flash`) — ByteDance Seed — Free on shapes.inc — ctx 200,000 — Reasoning, Native Vision, Tools — 12 ratings — added 2025-12-23 — active — shapes-picks: — — picker
  - Ultra-fast multimodal model built for deep reasoning and large-scale data analysis.

- **Seed 1.6** (`bytedance-seed/seed-1.6`) — ByteDance Seed — Premium · 0.17 cr/msg — ctx 200,000 — Reasoning, Native Vision, Tools — 0 ratings — added 2025-12-23 — active — shapes-picks: — — directory-only
  - Multimodal reasoning model with a large context window for complex image and video analysis.

- **Seed 2.1 Turbo** (`bytedance-seed/seed-2-1-turbo`) — ByteDance Seed — Premium · 0.3 cr/msg — ctx 200,000 — Reasoning, Native Vision, Tools — 0 ratings — added 2026-08-12 — active — shapes-picks: — — directory-only
  - High-capacity multimodal engine optimized for complex coding, reasoning, and long-horizon agent workflows.

- **Seed-2.0-Code** (`bytedance-seed/seed-2.0-code`) — ByteDance Seed — Premium · 0.31 cr/msg — ctx 200,000 — Reasoning, Native Vision, Tools, efforts:low/medium/high — 0 ratings — added 2026-08-12 — active — shapes-picks: — — directory-only
  - Specialized for agentic coding workflows, frontend development, and complex multilingual programming tasks.

- **Seed-2.0-Lite** (`bytedance-seed/seed-2.0-lite`) — ByteDance Seed — Premium · 0.17 cr/msg — ctx 200,000 — Reasoning, Native Vision, Tools, efforts:low/medium/high — 0 ratings — added 2026-03-10 — active — shapes-picks: — — directory-only
  - A low-latency, multimodal model optimized for high-frequency visual analysis and agentic workflows.

### Cerebras

- **Gemma 4 31B Fast** (`cerebras/gemma-4-31b-fast`) — Cerebras — Premium · 0.52 cr/msg — ctx 120,000 — Native Vision, Tools — 82 ratings — added  — active — shapes-picks: recommended, intelligent, roleplay — directory-only
  - A versatile engine for immersive storytelling and complex reasoning—like Gemma 4, but backed by a curated premium provider for up to 20× faster responses.

### Cohere

- **Command A+** (`cohere/command-a-plus`) — Cohere — Premium · 0.18 cr/msg — ctx 120,000 — Reasoning, Native Vision, Tools — 1 ratings — added 2026-09-22 — active — shapes-picks: — — directory-only
  - A specialized engine built for enterprise agentic workflows, structured data extraction, and complex reasoning tasks.

### DeepSeek

- **DeepSeek V3.2** (`deepseek/deepseek-v3.2`) — DeepSeek — Premium · 0.15 cr/msg — ctx 120,000 — Reasoning, Tools — 167,791 ratings — added 2025-12-01 — active — shapes-picks: — — directory-only
  - A high-performance engine built for complex reasoning and long-term narrative consistency.

- **DeepSeek V4 Flash 0423** (`deepseek/deepseek-v4-flash`) — DeepSeek — Premium · 0.03 cr/msg — ctx 500,000 — Reasoning, Tools, efforts:high — 7,018 ratings — added 2026-04-24 — active — shapes-picks: — — directory-only
  - An efficiency-optimized model built for high-throughput reasoning and creative tasks.

- **DeepSeek V4 Pro 0423** (`deepseek/deepseek-v4-pro`) — DeepSeek — Premium · 0.11 cr/msg — ctx 500,000 — Reasoning, Tools, efforts:high — 1,669 ratings — added 2026-04-24 — active — shapes-picks: — — directory-only
  - Advanced reasoning and coding model with high-efficiency architecture for complex tasks.

- **DeepSeek V4 Flash Latest** (`~deepseek/deepseek-v4-flash-latest`) — DeepSeek — Premium · 0.03 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, efforts:low/high — 449 ratings — added 2026-08-01 — active — shapes-picks: — — directory-only
  - High-speed reasoning model with a massive context window and transparent step-by-step thinking.

- **DeepSeek V4 Flash 0731** (`deepseek/deepseek-v4-flash-0731`) — DeepSeek — Premium · 0.03 cr/msg — ctx 500,000 — Reasoning, Tools, efforts:low/high — 132 ratings — added 2026-07-31 — active — shapes-picks: — — directory-only
  - High-performance reasoning and coding engine with an expansive context window for complex analysis.

- **DeepSeek V4 Pro 0813** (`deepseek/deepseek-v4-pro-0813`) — DeepSeek — Premium · 0.74 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools — 5 ratings — added 2026-08-12 — active — shapes-picks: — — directory-only
  - A high-capacity reasoning model optimized for creative writing and complex, long-context tasks.

- **DeepSeek V4.1 Flash** (`deepseek/deepseek-v4.1-flash`) — DeepSeek — Premium · 0.05 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, efforts:low/high — 5 ratings — added 2026-09-10 — active — shapes-picks: recommended, roleplay — directory-only
  - High-efficiency multimodal engine optimized for complex agentic tasks and large-scale reasoning.

- **DeepSeek V4 Flash Vision Exp** (`deepseek/deepseek-v4-flash-vision-exp`) — DeepSeek — Premium · 0.12 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, efforts:low/high — 1 ratings — added 2026-08-21 — active — shapes-picks: — — directory-only
  - Experimental multimodal model optimized for document analysis and complex agent workflows.

- **DeepSeek Flash Latest** (`~deepseek/deepseek-flash-latest`) — DeepSeek — Premium · 0.05 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, efforts:low/high — 0 ratings — added 2026-09-14 — active — shapes-picks: — — directory-only
  - High-speed reasoning engine with a massive context window for complex analysis and long-form document processing.

- **DeepSeek Pro Latest** (`~deepseek/deepseek-pro-latest`) — DeepSeek — Premium · 0.2 cr/msg — ctx 500,000 — Native Vision, Tools — 0 ratings — added 2026-09-14 — active — shapes-picks: — — directory-only
  - A dynamic alias providing automatic access to the most recent DeepSeek Pro model.

### Fireworks

- **Ember-1** (`fireworks/ember-1`) — Fireworks — Premium · 1.8 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, efforts:low/high — 0 ratings — added 2026-09-24 — active — shapes-picks: — — directory-only
  - Efficient reasoning model optimized for coding, knowledge work, and agentic tasks.

### Google

- **Gemma 4 31B** (`google/gemma-4-31b-it`) — Google — Free on shapes.inc — ctx 200,000 — Native Vision, Tools — 113,857 ratings — added 2026-04-02 — active — shapes-picks: recommended, intelligent, roleplay — picker
  - A versatile engine for immersive roleplay and complex narrative building with strong analytical capabilities.

- **Gemini 3.1 Flash Lite Preview** (`google/gemini-3.1-flash-lite-preview`) — Google — Premium · 0.16 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, efforts:low/medium/high — 15,881 ratings — added 2026-03-03 — active — shapes-picks: — — directory-only
  - A high-speed, efficient engine optimized for rapid data extraction and snappy, high-volume conversational tasks.

- **Gemma 4 26B A4B** (`google/gemma-4-26b-a4b-it`) — Google — Free on shapes.inc — ctx 200,000 — Native Vision, Tools — 1,159 ratings — added 2026-04-03 — active — shapes-picks: — — picker
  - A high-performance, instruction-tuned model that balances rapid, dynamic responses with strong reasoning and multimodal capabilities.

- **Gemini 3.1 Flash Lite** (`google/gemini-3.1-flash-lite`) — Google — Premium · 0.16 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, efforts:low/medium/high — 354 ratings — added 2026-05-07 — active — shapes-picks: — — directory-only
  - High-speed, large-context engine optimized for rapid interactions and long-term lore retention.

- **Gemini 3.1 Pro Preview** (`google/gemini-3.1-pro-preview`) — Google — Premium · 1.24 cr/msg — ctx 500,000 — Reasoning, Native Vision, efforts:low/medium/high, reasoning-required — 90 ratings — added 2026-02-19 — active — shapes-picks: roleplay — directory-only
  - A highly coherent multimodal engine that excels at maintaining character consistency and complex reasoning over long-term interactions.

- **Gemini 3 Flash Preview** (`google/gemini-3-flash-preview`) — Google — Premium · 0.31 cr/msg — ctx 500,000 — Native Vision, Tools — 40 ratings — added 2025-12-17 — active — shapes-picks: — — directory-only
  - High-speed multimodal engine optimized for long-term conversational coherence and complex reasoning.

- **Gemini 3.5 Flash** (`google/gemini-3.5-flash`) — Google — Premium · 0.93 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, efforts:low/medium/high, reasoning-required — 9 ratings — added 2026-05-19 — active — shapes-picks: — — directory-only
  - High-efficiency reasoning and coding performance with a massive context window.

- **Gemini 3.7 Flash** (`google/gemini-3.7-flash`) — Google — Premium · 0.45 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, efforts:low/medium/high, reasoning-required — 7 ratings — added 2026-08-13 — active — shapes-picks: — — directory-only
  - A high-speed, multimodal model optimized for creative writing, complex reasoning, and agentic workflows.

- **Gemini 3.8 Flash** (`google/gemini-3.8-flash`) — Google — Premium · 0.45 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, efforts:low/medium/high, reasoning-required — 7 ratings — added 2026-09-02 — active — shapes-picks: — — directory-only
  - A high-performance multimodal model optimized for complex reasoning, coding, and creative writing.

- **Gemini 3.1 Pro Preview Custom Tools** (`google/gemini-3.1-pro-preview-customtools`) — Google — Premium · 1.24 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, efforts:low/medium/high, reasoning-required — 6 ratings — added 2026-02-25 — active — shapes-picks: — — directory-only
  - Optimized for reliable function calling and complex agentic workflows.

- **Gemini Pro Latest** (`~google/gemini-pro-latest`) — Google — Premium · 1.24 cr/msg — ctx 500,000 — Reasoning, Native Vision, efforts:low/medium/high, reasoning-required — 6 ratings — added 2026-04-27 — active — shapes-picks: — — directory-only
  - A dynamic alias providing automatic access to the newest Gemini Pro model for multimodal and long-context tasks.

- **Gemini 3.6 Flash** (`google/gemini-3.6-flash`) — Google — Premium · 0.45 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, efforts:low/medium/high, reasoning-required — 4 ratings — added 2026-07-21 — active — shapes-picks: — — directory-only
  - High-speed multimodal model optimized for efficient coding, agentic workflows, and massive context processing.

- **Gemini Flash Latest** (`~google/gemini-flash-latest`) — Google — Premium · 0.45 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, efforts:low/medium/high, reasoning-required — 3 ratings — added 2026-04-27 — active — shapes-picks: — — directory-only
  - High-performance multimodal workhorse for complex document analysis and large-scale reasoning tasks.

- **Gemini 3.5 Flash Lite** (`google/gemini-3.5-flash-lite`) — Google — Premium · 0.2 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, efforts:low/medium/high, reasoning-required — 1 ratings — added 2026-07-21 — active — shapes-picks: recommended, intelligent — directory-only
  - High-efficiency, low-latency model optimized for rapid processing and large-context tasks.

### IBM

- **Granite 4.2 8B** (`ibm-granite/granite-4.2-8b`) — IBM — Free on shapes.inc — ctx 120,000 — Reasoning, Tools, efforts:low/high — 10 ratings — added 2026-08-31 — active — shapes-picks: — — picker
  - A reasoning-focused model with adjustable thinking modes for coding, math, and agentic workflows.

- **Granite 4.0 Micro** (`ibm-granite/granite-4.0-h-micro`) — IBM — Free on shapes.inc — ctx 120,000 — none — 9 ratings — added 2025-10-20 — active — shapes-picks: — — picker
  - Efficient 3B parameter model optimized for enterprise summarization, classification, and code completion tasks.

### Inception

- **Mercury 2.5** (`inception/mercury-2.5`) — Inception — Free on shapes.inc — ctx 200,000 — Reasoning, Tools, efforts:low/medium/high — 27 ratings — added 2026-09-08 — active — shapes-picks: — — picker
  - High-speed diffusion model optimized for concise prose and efficient tool-based tasks.

- **Mercury 2** (`inception/mercury-2`) — Inception — Premium · 0.14 cr/msg — ctx 120,000 — Reasoning, Tools, efforts:low/medium/high — 6 ratings — added 2026-03-04 — active — shapes-picks: — — directory-only
  - High-speed reasoning engine with tunable depth and parallel token generation.

### inclusionAI

- **Ling 3.0 Flash** (`inclusionai/ling-3.0-flash`) — inclusionAI — Free on shapes.inc — ctx 200,000 — Reasoning, Tools — 6,881 ratings — added 2026-07-23 — active — shapes-picks: recommended — picker
  - A high-performance, reasoning-capable model optimized for long-form creative prose and complex agentic workflows.

- **Ling 3.0 Flash Fin** (`inclusionai/ling-3.0-flash-fin`) — inclusionAI — Free on shapes.inc — ctx 200,000 — Reasoning, Tools — 32 ratings — added 2026-08-27 — active — shapes-picks: — — picker
  - Specialized finance-focused engine for investment research, valuation modeling, and complex document analysis.

- **Ling 3.0 Flash VL** (`inclusionai/ling-3.0-flash-vl`) — inclusionAI — Free on shapes.inc — ctx 200,000 — Reasoning, Native Vision, Tools — 17 ratings — added 2026-09-10 — active — shapes-picks: — — picker
  - Efficient multimodal model capable of processing complex image, video, and text inputs with high-capacity reasoning.

### Inference.net

- **Schematron V2 Turbo** (`inference-net/schematron-v2-turbo`) — Inference.net — Free on shapes.inc — ctx 120,000 — none — 2 ratings — added 2026-09-12 — active — shapes-picks: — — picker
  - High-throughput model specialized for structured HTML-to-JSON data extraction.

- **Schematron V2 Small** (`inference-net/schematron-v2-small`) — Inference.net — Free on shapes.inc — ctx 120,000 — none — 1 ratings — added 2026-09-12 — active — shapes-picks: — — picker
  - Specialized 3B-parameter model for high-volume HTML-to-JSON data extraction.

### Meituan

- **LongCat 2.0** (`meituan/longcat-2.0`) — Meituan — Premium · 0.17 cr/msg — ctx 500,000 — Reasoning, Tools — 11 ratings — added 2026-07-20 — active — shapes-picks: — — directory-only
  - High-capacity sparse model optimized for massive context and complex coding tasks.

### Meta

- **Muse Spark 1.2 Contributor** (`meta/muse-spark-1.2-contributor`) — Meta — Free on shapes.inc — ctx 500,000 — Reasoning, Native Vision, Tools, efforts:low/medium/high, reasoning-required — 33 ratings — added 2026-08-21 — active — shapes-picks: — — picker
  - Cost-effective multimodal reasoning for developers and large-scale agentic workflows.

- **Muse Spark 1.3 Contributor** (`meta/muse-spark-1.3-contributor`) — Meta — Free on shapes.inc — ctx 500,000 — Reasoning, Native Vision, Tools, reasoning-required — 27 ratings — added 2026-09-02 — active — shapes-picks: — — picker
  - Cost-efficient multimodal reasoning for experimentation and agentic workflows.

- **Muse Glimmer 30B** (`meta/muse-glimmer-30b`) — Meta — Premium · 0.2 cr/msg — ctx 120,000 — Reasoning, Native Vision, Tools, efforts:low/medium/high, reasoning-required — 1 ratings — added 2026-08-09 — active — shapes-picks: — — directory-only
  - A capable multimodal model optimized for autonomous agentic workflows and complex reasoning tasks.

- **Muse Spark 1.3** (`meta/muse-spark-1.3`) — Meta — Premium · 0.71 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, efforts:low/medium/high, reasoning-required — 1 ratings — added 2026-09-02 — active — shapes-picks: — — directory-only
  - Multimodal reasoning engine built for complex agentic workflows and long-context analysis.

- **Muse Spark 1.1** (`meta/muse-spark-1.1`) — Meta — Premium · 0.71 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, efforts:low/medium/high, reasoning-required — 0 ratings — added 2026-07-16 — active — shapes-picks: — — directory-only
  - Multimodal reasoning engine built for complex agentic workflows and large-scale code analysis.

- **Muse Spark 1.2** (`meta/muse-spark-1.2`) — Meta — Premium · 0.71 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, efforts:low/medium/high, reasoning-required — 0 ratings — added 2026-08-05 — active — shapes-picks: — — directory-only
  - A reasoning-focused engine built for complex agentic workflows and multi-file analysis.

### MiniMax

- **MiniMax M2-her** (`minimax/minimax-m2-her`) — MiniMax — Premium · 0.17 cr/msg — ctx 30,000 — none — 111 ratings — added 2026-01-23 — active — shapes-picks: roleplay — directory-only
  - Dialogue-focused model built for character-driven storytelling and immersive roleplay.

- **MiniMax M3** (`minimax/minimax-m3`) — MiniMax — Premium · 0.17 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools — 86 ratings — added 2026-05-31 — active — shapes-picks: — — directory-only
  - A high-capacity multimodal engine built for complex narrative consistency and long-horizon reasoning.

- **MiniMax M2.7** (`minimax/minimax-m2.7`) — MiniMax — Premium · 0.12 cr/msg — ctx 200,000 — Reasoning, Tools, reasoning-required — 37 ratings — added 2026-03-18 — active — shapes-picks: — — directory-only
  - Specialized for complex agentic workflows, technical debugging, and multi-step document generation.

- **MiniMax M2** (`minimax/minimax-m2`) — MiniMax — Premium · 0.17 cr/msg — ctx 200,000 — Reasoning, Tools, reasoning-required — 2 ratings — added 2025-10-23 — active — shapes-picks: — — directory-only
  - Efficient reasoning model optimized for coding tasks and multi-step agentic workflows.

- **MiniMax M2.5** (`minimax/minimax-m2.5`) — MiniMax — Premium · 0.16 cr/msg — ctx 200,000 — Reasoning, Tools, reasoning-required — 1 ratings — added 2026-02-12 — active — shapes-picks: — — directory-only
  - Specialized for complex agentic workflows, technical coding tasks, and office productivity.

- **MiniMax M2.1** (`minimax/minimax-m2.1`) — MiniMax — Premium · 0.17 cr/msg — ctx 200,000 — Reasoning, Tools, reasoning-required — 0 ratings — added 2025-12-23 — active — shapes-picks: — — directory-only
  - A specialized model engineered for complex coding tasks and agentic automation workflows.

### Mistral

- **Mistral Small 4** (`mistralai/mistral-small-2603`) — Mistral — Premium · 0.09 cr/msg — ctx 200,000 — Reasoning, Native Vision, Tools — 5,482 ratings — added 2026-03-16 — active — shapes-picks: roleplay — directory-only
  - A versatile multimodal model optimized for complex reasoning, technical analysis, and structured data tasks.

- **Ministral 3 14B 2512** (`mistralai/ministral-14b-2512`) — Mistral — Free on shapes.inc — ctx 200,000 — Native Vision, Tools — 31 ratings — added 2025-12-02 — active — shapes-picks: — — picker
  - Efficient, multimodal model optimized for function calling and structured data tasks.

- **Ministral 3 8B 2512** (`mistralai/ministral-8b-2512`) — Mistral — Free on shapes.inc — ctx 200,000 — Native Vision, Tools — 4 ratings — added 2025-12-02 — active — shapes-picks: — — picker
  - Efficient multimodal model with a massive context window and strong support for structured data tasks.

- **Voxtral Small 24B 2507** (`mistralai/voxtral-small-24b-2507`) — Mistral — Free on shapes.inc — ctx 30,000 — Tools — 2 ratings — added 2025-10-30 — active — shapes-picks: — — picker
  - Specialized multimodal engine for high-accuracy audio transcription, translation, and voice-driven function calling.

- **Ministral 3 3B 2512** (`mistralai/ministral-3b-2512`) — Mistral — Free on shapes.inc — ctx 120,000 — Native Vision, Tools — 1 ratings — added 2025-12-02 — active — shapes-picks: — — picker
  - Efficient, lightweight multimodal model optimized for fast instruction following and vision tasks.

- **Devstral 2 2512** (`mistralai/devstral-2512`) — Mistral — Premium · 0.24 cr/msg — ctx 200,000 — Tools — 0 ratings — added 2025-12-09 — active — shapes-picks: — — directory-only
  - Specialized architecture for complex software engineering, multi-file codebase navigation, and automated bug resolution.

- **Mistral Medium 3.5** (`mistralai/mistral-medium-3-5`) — Mistral — Premium · 0.9 cr/msg — ctx 200,000 — Native Vision, Tools — 0 ratings — added 2026-04-30 — active — shapes-picks: — — directory-only
  - A high-capacity model built for complex reasoning, coding, and multi-modal analysis.

### MoonshotAI

- **Kimi K2.5** (`moonshotai/kimi-k2.5`) — MoonshotAI — Premium · 0.27 cr/msg — ctx 200,000 — Reasoning, Tools — 65 ratings — added 2026-01-27 — active — shapes-picks: — — directory-only
  - A multimodal engine built for expansive world-building, long-form creative writing, and complex agentic reasoning.

- **Kimi K2.6** (`moonshotai/kimi-k2.6`) — MoonshotAI — Premium · 0.56 cr/msg — ctx 200,000 — Reasoning, Native Vision, Tools — 32 ratings — added 2026-04-20 — active — shapes-picks: — — directory-only
  - Advanced multimodal model optimized for complex coding, reasoning, and large-scale task orchestration.

- **Kimi K2 Thinking** (`moonshotai/kimi-k2-thinking`) — MoonshotAI — Premium · 0.35 cr/msg — ctx 200,000 — Reasoning, Tools, reasoning-required — 30 ratings — added 2025-11-06 — active — shapes-picks: — — directory-only
  - Specialized reasoning engine built for long-horizon, multi-step analysis and complex logic workflows.

- **Kimi K3** (`moonshotai/kimi-k3`) — MoonshotAI — Premium · 0.75 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, efforts:low/high — 21 ratings — added 2026-07-16 — active — shapes-picks: — — directory-only
  - A high-capacity reasoning engine capable of handling massive context for complex creative and analytical tasks.

- **Kimi Latest** (`~moonshotai/kimi-latest`) — MoonshotAI — Premium · 0.44 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, efforts:low/high — 17 ratings — added 2026-04-27 — active — shapes-picks: — — directory-only
  - A high-capacity model optimized for complex reasoning, large-scale data analysis, and multimodal inputs.

- **Kimi K2.7 Code** (`moonshotai/kimi-k2.7-code`) — MoonshotAI — Premium · 0.4 cr/msg — ctx 200,000 — Reasoning, Native Vision, Tools, reasoning-required — 2 ratings — added 2026-06-12 — active — shapes-picks: — — directory-only
  - Specialized coding model featuring native multimodal support and mandatory multi-step reasoning.

### Nex AGI

- **Nex-N2.5-Mini** (`nex-agi/nex-n2.5-mini`) — Nex AGI — Free on shapes.inc — ctx 200,000 — Reasoning, Native Vision, efforts:medium/high — 1 ratings — added 2026-09-08 — active — shapes-picks: — — picker
  - An agentic model optimized for multi-file coding, browser automation, and visual reasoning tasks.

- **Nex-N2.5-Pro** (`nex-agi/nex-n2.5-pro`) — Nex AGI — Free on shapes.inc — ctx 200,000 — Reasoning, Tools, efforts:medium/high — 1 ratings — added 2026-09-08 — active — shapes-picks: — — picker
  - Specialized agentic model engineered for complex coding, computer use, and long-horizon automation tasks.

### NVIDIA

- **Nemotron 3 Super** (`nvidia/nemotron-3-super-120b-a12b`) — NVIDIA — Premium · 0.05 cr/msg — ctx 200,000 — Reasoning, Tools — 112 ratings — added 2026-03-11 — active — shapes-picks: — — directory-only
  - Efficient, concise engine optimized for dynamic roleplay and long-context agentic tasks.

- **Nemotron 3.5 Lightning** (`nvidia/nemotron-3.5-lightning`) — NVIDIA — Free on shapes.inc — ctx 200,000 — Reasoning, Tools — 31 ratings — added 2026-08-11 — active — shapes-picks: — — picker
  - A high-throughput model optimized for speed and agentic tasks, though prone to repetitive output patterns.

- **Nemotron 3 Ultra** (`nvidia/nemotron-3-ultra-550b-a55b`) — NVIDIA — Premium · 0.29 cr/msg — ctx 200,000 — Reasoning, Tools, efforts:medium/high — 18 ratings — added 2026-06-04 — active — shapes-picks: — — directory-only
  - High-capacity reasoning model built for complex agentic workflows and deep long-context analysis.

- **Nemotron 3 Nano 30B A3B** (`nvidia/nemotron-3-nano-30b-a3b`) — NVIDIA — Free on shapes.inc — ctx 200,000 — Reasoning, Tools — 6 ratings — added 2025-12-14 — active — shapes-picks: — — picker
  - Efficient hybrid architecture built for complex reasoning and agentic workflows.

- **Nemotron 3.5 Content Safety** (`nvidia/nemotron-3.5-content-safety`) — NVIDIA — Free on shapes.inc — ctx 120,000 — Reasoning — 0 ratings — added 2026-06-04 — active — shapes-picks: — — picker
  - Specialized multimodal guardrail model for classifying content safety and providing auditable reasoning.

### OpenAI

- **GPT-5.4 Nano** (`openai/gpt-5.4-nano`) — OpenAI — Premium · 0.12 cr/msg — ctx 200,000 — Native Vision, Tools — 17 ratings — added 2026-03-17 — active — shapes-picks: — — directory-only
  - A high-speed, cost-efficient engine optimized for data extraction, classification, and high-volume tasks.

- **GPT-5.4** (`openai/gpt-5.4`) — OpenAI — Premium · 1.55 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, efforts:low/medium/high — 13 ratings — added 2026-03-05 — active — shapes-picks: — — directory-only
  - A high-context reasoning engine built for complex technical analysis and production-grade coding.

- **GPT-5.1** (`openai/gpt-5.1`) — OpenAI — Premium · 0.83 cr/msg — ctx 200,000 — Reasoning, Native Vision, Tools, efforts:low/medium/high — 2 ratings — added 2025-11-13 — active — shapes-picks: — — directory-only
  - Adaptive reasoning engine designed for complex coding, structured analysis, and large-scale document processing.

- **GPT-5.6 Luna** (`openai/gpt-5.6-luna`) — OpenAI — Premium · 0.12 cr/msg — ctx 500,000 — Native Vision, Tools — 2 ratings — added 2026-07-09 — active — shapes-picks: intelligent — directory-only
  - High-throughput model optimized for rapid reasoning and large-scale document analysis.

- **GPT-5.4 Pro** (`openai/gpt-5.4-pro`) — OpenAI — Premium · 18.6 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, efforts:medium/high, reasoning-required — 1 ratings — added 2026-03-05 — active — shapes-picks: — — directory-only
  - Advanced reasoning engine built for complex multi-step problem solving and massive context workflows.

- **GPT-5.5** (`openai/gpt-5.5`) — OpenAI — Premium · 3.1 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, efforts:low/medium/high — 1 ratings — added 2026-04-24 — active — shapes-picks: — — directory-only
  - Advanced reasoning and multimodal processing for complex professional and coding workflows.

- **GPT-5.6 Luna Pro** (`openai/gpt-5.6-luna-pro`) — OpenAI — Premium · 0.12 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, efforts:low/medium/high — 1 ratings — added 2026-07-09 — active — shapes-picks: — — directory-only
  - High-accuracy reasoning engine for complex analytical tasks and deep problem-solving.

- **GPT-5.6 Terra** (`openai/gpt-5.6-terra`) — OpenAI — Premium · 1.24 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, efforts:low/medium/high — 1 ratings — added 2026-07-09 — active — shapes-picks: — — directory-only
  - A balanced mid-tier model for complex reasoning, large-scale document analysis, and technical tasks.

- **GPT-6 Astra** (`openai/gpt-6-astra`) — OpenAI — Premium · 6 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, reasoning-required — 1 ratings — added 2026-09-04 — active — shapes-picks: — — directory-only
  - Advanced reasoning engine built for complex software engineering, deep research, and long-horizon tasks.

- **GPT-5.1-Codex** (`openai/gpt-5.1-codex`) — OpenAI — Premium · 0.83 cr/msg — ctx 200,000 — Reasoning, Native Vision, Tools, reasoning-required — 0 ratings — added 2025-11-13 — active — shapes-picks: — — directory-only
  - Specialized coding engine featuring adjustable reasoning effort and native patch application for complex software development.

- **GPT-5.1-Codex-Max** (`openai/gpt-5.1-codex-max`) — OpenAI — Premium · 0.83 cr/msg — ctx 200,000 — Reasoning, Native Vision, reasoning-required — 0 ratings — added 2025-12-04 — active — shapes-picks: — — directory-only
  - Specialized agentic model for complex software engineering and high-context technical analysis.

- **GPT-5.1-Codex-Mini** (`openai/gpt-5.1-codex-mini`) — OpenAI — Premium · 0.17 cr/msg — ctx 200,000 — Reasoning, Native Vision, Tools, efforts:low/medium/high — 0 ratings — added 2025-11-13 — active — shapes-picks: — — directory-only
  - A high-speed, efficient model optimized for coding tasks, structured data extraction, and agentic workflows.

- **GPT-5.2** (`openai/gpt-5.2`) — OpenAI — Premium · 1.16 cr/msg — ctx 200,000 — Reasoning, Native Vision, Tools, efforts:low/medium/high — 0 ratings — added 2025-12-10 — active — shapes-picks: — — directory-only
  - Adaptive reasoning engine designed for complex agentic workflows and large-scale document analysis.

- **GPT-5.2-Codex** (`openai/gpt-5.2-codex`) — OpenAI — Premium · 1.16 cr/msg — ctx 200,000 — Reasoning, Native Vision, Tools, reasoning-required — 0 ratings — added 2026-01-14 — active — shapes-picks: — — directory-only
  - Specialized coding engine featuring multimodal input and adjustable reasoning for complex development tasks.

- **GPT-5.3-Codex** (`openai/gpt-5.3-codex`) — OpenAI — Premium · 1.16 cr/msg — ctx 200,000 — Reasoning, Native Vision, Tools, efforts:low/medium/high — 0 ratings — added 2026-02-24 — active — shapes-picks: — — directory-only
  - Specialized agentic model for complex software engineering, debugging, and iterative code deployment.

- **GPT-5.4 Mini** (`openai/gpt-5.4-mini`) — OpenAI — Premium · 0.46 cr/msg — ctx 200,000 — Reasoning, Native Vision, Tools, efforts:low/medium/high — 0 ratings — added 2026-03-17 — active — shapes-picks: — — directory-only
  - High-efficiency reasoning and coding engine with a massive 400,000-token context window.

- **GPT-5.6 Sol** (`openai/gpt-5.6-sol`) — OpenAI — Premium · 1.2 cr/msg — ctx 500,000 — Native Vision, Tools — 0 ratings — added 2026-07-09 — active — shapes-picks: intelligent — directory-only
  - A flagship model built for complex reasoning, multi-step coding, and large-scale data analysis.

- **GPT-5.6 Sol Pro** (`openai/gpt-5.6-sol-pro`) — OpenAI — Premium · 1.2 cr/msg — ctx 500,000 — Native Vision, Tools — 0 ratings — added 2026-07-09 — active — shapes-picks: — — directory-only
  - Deep-reasoning model optimized for high-stakes analysis and complex problem-solving.

- **GPT-5.6 Terra Pro** (`openai/gpt-5.6-terra-pro`) — OpenAI — Premium · 1.24 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, efforts:low/medium/high — 0 ratings — added 2026-07-09 — active — shapes-picks: — — directory-only
  - High-accuracy reasoning engine for complex, multi-step analytical tasks.

- **GPT-6 Astra Pro** (`openai/gpt-6-astra-pro`) — OpenAI — Premium · 6 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, efforts:low/medium/high, reasoning-required — 0 ratings — added 2026-09-04 — active — shapes-picks: — — directory-only
  - High-accuracy reasoning engine for complex, multi-step problem solving and technical analysis.

- **GPT-6 Luna** (`openai/gpt-6-luna`) — OpenAI — Premium · 0.06 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, efforts:low/medium/high — 0 ratings — added 2026-09-22 — active — shapes-picks: — — directory-only
  - A high-speed, cost-efficient model optimized for rapid chat, classification, and complex agentic tasks.

- **GPT-6 Luna Pro** (`openai/gpt-6-luna-pro`) — OpenAI — Premium · 0.06 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, efforts:low/medium/high — 0 ratings — added 2026-09-22 — active — shapes-picks: — — directory-only
  - High-reasoning model optimized for complex, multi-step problem solving and massive context analysis.

- **GPT-6 Sol** (`openai/gpt-6-sol`) — OpenAI — Premium · 1.2 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, efforts:low/medium/high — 0 ratings — added 2026-09-22 — active — shapes-picks: — — directory-only
  - A balanced reasoning model optimized for complex software engineering and long-context analysis.

- **GPT-6 Sol Pro** (`openai/gpt-6-sol-pro`) — OpenAI — Premium · 1.2 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, efforts:low/medium/high — 0 ratings — added 2026-09-22 — active — shapes-picks: — — directory-only
  - High-accuracy reasoning engine for complex, high-stakes analytical tasks.

- **gpt-oss-safeguard-20b** (`openai/gpt-oss-safeguard-20b`) — OpenAI — Free on shapes.inc — ctx 120,000 — Reasoning, reasoning-required — 0 ratings — added 2025-10-29 — active — shapes-picks: — — picker
  - A specialized 21B-parameter model engineered for safety reasoning, content classification, and trust and safety policy enforcement.

### Openrouter

- **Free Models Router** (`openrouter/free`) — Openrouter — Free on shapes.inc — ctx 200,000 — Reasoning, Tools, efforts:low/medium/high — 11 ratings — added 2026-02-01 — active — shapes-picks: — — picker
  - Access a rotating selection of free AI models for text and image tasks without cost.

### Perceptron

- **Perceptron Mk1** (`perceptron/perceptron-mk1`) — Perceptron — Premium · 0.11 cr/msg — ctx 30,000 — Reasoning, Native Vision — 8 ratings — added 2026-05-12 — active — shapes-picks: — — directory-only
  - Specialized vision-language model for video analysis and complex spatial reasoning.

- **Perceptron Mk1.5** (`perceptron/perceptron-mk1.5`) — Perceptron — Premium · 0.11 cr/msg — ctx 30,000 — Reasoning, Tools, efforts:low/medium/high — 0 ratings — added 2026-09-25 — active — shapes-picks: — — directory-only
  - Multimodal reasoning engine with configurable effort levels for spatial and temporal analysis.

### Perplexity

- **Sonar Pro Search** (`perplexity/sonar-pro-search`) — Perplexity — Premium · 1.8 cr/msg — ctx 200,000 — Reasoning, Native Vision, reasoning-required — 0 ratings — added 2025-10-30 — active — shapes-picks: — — directory-only
  - An agentic search system built for multi-step reasoning and complex research tasks.

### Poolside

- **Laguna S 2.1** (`poolside/laguna-s-2.1`) — Poolside — Free on shapes.inc — ctx 500,000 — Reasoning, Tools — 34 ratings — added 2026-07-21 — active — shapes-picks: — — picker
  - Specialized coding engine featuring native reasoning and a massive context window for complex software engineering tasks.

- **Laguna XS 2.1** (`poolside/laguna-xs-2.1`) — Poolside — Free on shapes.inc — ctx 200,000 — Reasoning, Tools — 20 ratings — added 2026-07-02 — active — shapes-picks: — — picker
  - Specialized coding engine optimized for agentic workflows and complex software engineering tasks.

### PrismML

- **Ternary Bonsai 2 27B** (`prism-ml/ternary-bonsai-2-27b`) — PrismML — Premium · 0.05 cr/msg — ctx 200,000 — Reasoning, Native Vision, Tools, efforts:medium — 0 ratings — added 2026-09-18 — active — shapes-picks: — — directory-only
  - Efficient reasoning model utilizing ternary compression for high-performance analysis and structured data tasks.

### Qwen

- **Qwen3.5-Flash** (`qwen/qwen3.5-flash-02-23`) — Qwen — Free on shapes.inc — ctx 500,000 — Native Vision, Tools — 204 ratings — added 2026-02-25 — active — shapes-picks: — — picker
  - High-efficiency multimodal model with a massive context window for complex tasks.

- **Qwen3.7 Flash** (`qwen/qwen3.7-flash`) — Qwen — Free on shapes.inc — ctx 500,000 — Reasoning, Tools — 200 ratings — added 2026-07-27 — active — shapes-picks: — — picker
  - Multimodal reasoning engine built for complex visual tasks and large-scale data analysis.

- **Qwen3.6 35B A3B** (`qwen/qwen3.6-35b-a3b`) — Qwen — Premium · 0.1 cr/msg — ctx 200,000 — Reasoning, Native Vision, Tools — 41 ratings — added 2026-04-27 — active — shapes-picks: — — directory-only
  - Efficient multimodal model with high-throughput reasoning and extensive context support.

- **Qwen3.7 Plus** (`qwen/qwen3.7-plus`) — Qwen — Premium · 0.19 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools — 32 ratings — added 2026-06-03 — active — shapes-picks: — — directory-only
  - High-performance reasoning model optimized for complex coding, agentic workflows, and multi-modal analysis.

- **Qwen3.5-35B-A3B** (`qwen/qwen3.5-35b-a3b`) — Qwen — Premium · 0.1 cr/msg — ctx 200,000 — Reasoning, Native Vision, Tools — 21 ratings — added 2026-02-25 — active — shapes-picks: — — directory-only
  - Efficient multimodal model with native reasoning capabilities and a massive 262k token context window.

- **Qwen3.6 Flash** (`qwen/qwen3.6-flash`) — Qwen — Premium · 0.12 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools — 16 ratings — added 2026-04-27 — active — shapes-picks: — — directory-only
  - High-speed multimodal model built for massive context processing and efficient document analysis.

- **Qwen3.5-9B** (`qwen/qwen3.5-9b`) — Qwen — Free on shapes.inc — ctx 200,000 — Reasoning, Native Vision — 6 ratings — added 2026-03-10 — active — shapes-picks: — — picker
  - Efficient multimodal model with strong reasoning, coding, and visual analysis capabilities.

- **Qwen3 Coder Next** (`qwen/qwen3-coder-next`) — Qwen — Premium · 0.08 cr/msg — ctx 200,000 — Tools — 3 ratings — added 2026-02-04 — active — shapes-picks: — — directory-only
  - Specialized coding engine optimized for agentic workflows and large-scale repository analysis.

- **Qwen3.6 Plus** (`qwen/qwen3.6-plus`) — Qwen — Premium · 0.2 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools — 2 ratings — added 2026-04-02 — active — shapes-picks: — — directory-only
  - A high-capacity engine built for complex coding, repository-level analysis, and nuanced creative roleplay.

- **Qwen3.7 Max** (`qwen/qwen3.7-max`) — Qwen — Premium · 0.83 cr/msg — ctx 500,000 — Reasoning, Tools — 2 ratings — added 2026-05-21 — active — shapes-picks: — — directory-only
  - A high-performance text-only engine optimized for complex coding, reasoning, and long-horizon agentic tasks.

- **Qwen3.5 Plus 2026-04-20** (`qwen/qwen3.5-plus-20260420`) — Qwen — Premium · 0.19 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools — 1 ratings — added 2026-04-27 — active — shapes-picks: — — directory-only
  - A high-capacity multimodal engine built for massive context analysis and complex reasoning tasks.

- **Qwen3 Max Thinking** (`qwen/qwen3-max-thinking`) — Qwen — Premium · 0.47 cr/msg — ctx 200,000 — Reasoning, Tools — 0 ratings — added 2026-02-09 — active — shapes-picks: — — directory-only
  - Specialized reasoning engine built for complex, multi-step cognitive tasks and deep analysis.

- **Qwen3 VL 30B A3B Instruct** (`qwen/qwen3-vl-30b-a3b-instruct`) — Qwen — Premium · 0.09 cr/msg — ctx 200,000 — Native Vision, Tools — 0 ratings — added 2025-10-06 — active — shapes-picks: — — directory-only
  - Multimodal engine specialized in complex visual reasoning, document analysis, and GUI-based agentic workflows.

- **Qwen3 VL 30B A3B Thinking** (`qwen/qwen3-vl-30b-a3b-thinking`) — Qwen — Premium · 0.15 cr/msg — ctx 200,000 — Reasoning, Native Vision, Tools, reasoning-required — 0 ratings — added 2025-10-06 — active — shapes-picks: — — directory-only
  - Advanced multimodal reasoning model optimized for complex visual analysis and document processing.

- **Qwen3 VL 32B Instruct** (`qwen/qwen3-vl-32b-instruct`) — Qwen — Premium · 0.06 cr/msg — ctx 120,000 — Native Vision, Tools — 0 ratings — added 2025-10-23 — active — shapes-picks: — — directory-only
  - High-precision vision-language model for complex document analysis and spatial reasoning.

- **Qwen3 VL 8B Instruct** (`qwen/qwen3-vl-8b-instruct`) — Qwen — Premium · 0.07 cr/msg — ctx 200,000 — Native Vision, Tools — 0 ratings — added 2025-10-14 — active — shapes-picks: — — directory-only
  - Multimodal vision-language model optimized for high-fidelity image analysis, document parsing, and spatial reasoning.

- **Qwen3 VL 8B Thinking** (`qwen/qwen3-vl-8b-thinking`) — Qwen — Premium · 0.13 cr/msg — ctx 120,000 — Reasoning, Native Vision, Tools, reasoning-required — 0 ratings — added 2025-10-14 — active — shapes-picks: — — directory-only
  - Multimodal reasoning model designed for complex visual analysis and structured problem-solving.

- **Qwen3.5 397B A17B** (`qwen/qwen3.5-397b-a17b`) — Qwen — Premium · 0.29 cr/msg — ctx 200,000 — Reasoning, Native Vision, Tools — 0 ratings — added 2026-02-16 — active — shapes-picks: — — directory-only
  - High-performance reasoning model with native support for complex coding, agentic workflows, and multimodal inputs.

- **Qwen3.5 Plus 2026-02-15** (`qwen/qwen3.5-plus-02-15`) — Qwen — Premium · 0.16 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools — 0 ratings — added 2026-02-16 — active — shapes-picks: — — directory-only
  - High-capacity multimodal engine built for massive document analysis and complex agentic workflows.

- **Qwen3.5-122B-A10B** (`qwen/qwen3.5-122b-a10b`) — Qwen — Premium · 0.17 cr/msg — ctx 200,000 — Reasoning, Native Vision, Tools — 0 ratings — added 2026-02-25 — active — shapes-picks: — — directory-only
  - Advanced reasoning and multimodal model featuring built-in chain-of-thought processing.

- **Qwen3.5-27B** (`qwen/qwen3.5-27b`) — Qwen — Premium · 0.13 cr/msg — ctx 200,000 — Reasoning, Native Vision, Tools — 0 ratings — added 2026-02-25 — active — shapes-picks: — — directory-only
  - Efficient reasoning and coding assistant with native vision-language capabilities.

- **Qwen3.6 27B** (`qwen/qwen3.6-27b`) — Qwen — Premium · 0.23 cr/msg — ctx 200,000 — Reasoning, Native Vision, Tools — 0 ratings — added 2026-04-27 — active — shapes-picks: — — directory-only
  - A reasoning-focused multimodal model optimized for complex coding tasks and multi-step problem solving.

- **Qwen3.6 Max Preview** (`qwen/qwen3.6-max-preview`) — Qwen — Premium · 0.64 cr/msg — ctx 200,000 — Reasoning, Tools — 0 ratings — added 2026-04-27 — active — shapes-picks: — — directory-only
  - High-capacity reasoning model designed for complex coding tasks and long-context analysis.

- **Qwen3.8 2.4T A95B** (`qwen/qwen3.8-2.4t-a95b`) — Qwen — Premium · 1.12 cr/msg — ctx 500,000 — Reasoning, Tools, efforts:low/medium, reasoning-required — 0 ratings — added 2026-08-12 — active — shapes-picks: — — directory-only
  - A high-performance reasoning model built for complex coding, research, and analytical tasks.

- **Qwen3.8 27B** (`qwen/qwen3.8-27b`) — Qwen — Premium · 0.26 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, efforts:low/medium — 0 ratings — added 2026-08-14 — active — shapes-picks: — — directory-only
  - A versatile vision-language model with adjustable reasoning depth for complex coding and analytical tasks.

- **Qwen3.8 Max (0902)** (`qwen/qwen3.8-max-0902`) — Qwen — Premium · 1.12 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, efforts:low/medium/high, reasoning-required — 0 ratings — added 2026-09-03 — active — shapes-picks: — — directory-only
  - A high-capacity reasoning engine optimized for complex agentic workflows and long-context analysis.

- **Qwen3.8 Max Prime** (`qwen/qwen3.8-max-prime`) — Qwen — Premium · 2.24 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, efforts:low/medium/high, reasoning-required — 0 ratings — added 2026-09-23 — active — shapes-picks: — — directory-only
  - High-throughput multimodal reasoning engine with an expansive 1M token context window.

- **Qwen3.8 Omni Flash** (`qwen/qwen3.8-omni-flash`) — Qwen — Premium · 0.08 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools — 0 ratings — added 2026-09-21 — active — shapes-picks: — — directory-only
  - Multimodal reasoning engine built for complex audio, video, and agentic coding tasks.

### Rekaai

- **Reka Edge** (`rekaai/reka-edge`) — Rekaai — Free on shapes.inc — ctx 8,000 — Native Vision, Tools — 2 ratings — added 2026-03-20 — active — shapes-picks: — — picker
  - Efficient multimodal model for image, video, and structured data analysis.

### Relace

- **Relace Search** (`relace/relace-search`) — Relace — Premium · 0.56 cr/msg — ctx 200,000 — Tools — 0 ratings — added 2025-12-08 — active — shapes-picks: — — directory-only
  - Specialized subagent for rapid, parallel codebase exploration and file retrieval.

### Sakana

- **Fugu Ultra v2** (`sakana/fugu-ultra-v2`) — Sakana — Premium · 3.1 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, reasoning-required — 1 ratings — added 2026-09-11 — active — shapes-picks: — — directory-only
  - A multi-agent orchestration system built for complex reasoning, large-scale research, and full-stack development.

- **Fugu Max** (`sakana/fugu-max`) — Sakana — Premium · 1.12 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, efforts:high, reasoning-required — 0 ratings — added 2026-09-11 — active — shapes-picks: — — directory-only
  - Multi-agent orchestration system built for large-scale document analysis and complex reasoning tasks.

- **Fugu Ultra** (`sakana/fugu-ultra`) — Sakana — Premium · 3.1 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, efforts:high, reasoning-required — 0 ratings — added 2026-06-24 — active — shapes-picks: — — directory-only
  - Multi-agent orchestration system built for complex reasoning and massive context processing.

- **Sakana Namazu** (`sakana/sakana-namazu`) — Sakana — Premium · 0.56 cr/msg — ctx 200,000 — Reasoning, Native Vision, Tools, efforts:high — 0 ratings — added 2026-08-11 — active — shapes-picks: — — directory-only
  - Specialized reasoning model optimized for Japanese language tasks, business writing, and complex multi-step workflows.

### shapes.inc

- **Formless v2** (`shapesinc/formless-v2`) — shapes.inc — Free on shapes.inc — ctx 200,000 — Reasoning, Tools — 2,372 ratings — added 2026-09-14 — active — shapes-picks: recommended — picker
  - The shapes.inc engine for conversations, shared stories, and creating together.

### SpaceXAI

- **Grok 4.20** (`x-ai/grok-4.20`) — SpaceXAI — Premium · 0.68 cr/msg — ctx 500,000 — Native Vision, Tools — 50 ratings — added 2026-03-31 — active — shapes-picks: — — directory-only
  - A high-capacity reasoning model that balances complex analytical workflows with expressive, nuanced creative writing.

- **Grok 4.3** (`x-ai/grok-4.3`) — SpaceXAI — Premium · 0.68 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, efforts:low/medium/high — 10 ratings — added 2026-04-30 — active — shapes-picks: — — directory-only
  - A high-capacity reasoning engine built for complex analysis and large-scale document processing.

- **Grok 4.6** (`x-ai/grok-4.6`) — SpaceXAI — Premium · 1.12 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, efforts:low/medium/high, reasoning-required — 5 ratings — added 2026-08-12 — active — shapes-picks: — — directory-only
  - High-performance reasoning model optimized for complex coding, STEM tasks, and agentic workflows.

- **Grok 4.20 Multi-Agent** (`x-ai/grok-4.20-multi-agent`) — SpaceXAI — Premium · 0.68 cr/msg — ctx 500,000 — Reasoning, Native Vision, efforts:low/medium/high, reasoning-required — 2 ratings — added 2026-03-31 — active — shapes-picks: — — directory-only
  - Collaborative agent-based engine built for deep research and complex information synthesis.

- **Grok 4.7** (`x-ai/grok-4.7`) — SpaceXAI — Premium · 1.12 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, efforts:low/medium/high, reasoning-required — 2 ratings — added 2026-09-21 — active — shapes-picks: — — directory-only
  - High-reasoning model optimized for complex software engineering, document drafting, and agentic workflows.

- **Grok Build 0.1** (`x-ai/grok-build-0.1`) — SpaceXAI — Premium · 0.54 cr/msg — ctx 200,000 — Reasoning, Native Vision, Tools, reasoning-required — 0 ratings — added 2026-05-20 — active — shapes-picks: — — directory-only
  - A specialized model engineered for agentic software development and complex coding workflows.

### StepFun

- **Step 3.5 Flash** (`stepfun/step-3.5-flash`) — StepFun — Free on shapes.inc — ctx 200,000 — Reasoning, Tools, reasoning-required — 99 ratings — added 2026-01-29 — active — shapes-picks: — — picker
  - High-efficiency reasoning model designed for complex coding and obedient narrative control.

- **Step 3.7 Flash** (`stepfun/step-3.7-flash`) — StepFun — Premium · 0.12 cr/msg — ctx 200,000 — Reasoning, Native Vision, Tools, efforts:low/medium/high, reasoning-required — 7 ratings — added 2026-05-28 — active — shapes-picks: — — directory-only
  - High-efficiency multimodal engine built for complex reasoning, coding, and large-scale data analysis.

### Tencent

- **Hy3 preview** (`tencent/hy3-preview`) — Tencent — Premium · 0.1 cr/msg — ctx 200,000 — Reasoning, Tools, efforts:low/high — 99 ratings — added 2026-04-22 — active — shapes-picks: — — directory-only
  - A large-scale MoE model optimized for complex reasoning, agentic workflows, and consistent creative roleplay.

- **Hy3** (`tencent/hy3`) — Tencent — Premium · 0.08 cr/msg — ctx 200,000 — Reasoning, Tools, efforts:low/high — 39 ratings — added 2026-07-06 — active — shapes-picks: — — directory-only
  - A high-capacity reasoning model built for complex agentic workflows and long-horizon tasks.

- **Hy-MT2-30B-A3B** (`tencent/hy-mt2-30b-a3b`) — Tencent — Free on shapes.inc — ctx 8,000 — none — 5 ratings — added 2026-08-20 — active — shapes-picks: — — picker
  - Specialized translation engine optimized for technical localization and structured data preservation.

- **Hy4 preview** (`tencent/hy4-preview`) — Tencent — Premium · 0.47 cr/msg — ctx 500,000 — Reasoning, Tools, efforts:low/high — 2 ratings — added 2026-08-28 — active — shapes-picks: — — directory-only
  - A high-capacity model built for complex reasoning, coding, and large-scale data analysis.

- **Hy-MT2-1.8B** (`tencent/hy-mt2-1.8b`) — Tencent — Free on shapes.inc — ctx 8,000 — none — 1 ratings — added 2026-08-20 — active — shapes-picks: — — picker
  - High-speed, specialized translation engine optimized for diverse language pairs and contextual accuracy.

- **Hy-MT2-7B** (`tencent/hy-mt2-7b`) — Tencent — Free on shapes.inc — ctx 8,000 — none — 0 ratings — added 2026-08-19 — active — shapes-picks: — — picker
  - Specialized translation engine designed for high-accuracy language conversion with strict structural and style adherence.

### Thinking Machines

- **Inkling** (`thinkingmachines/inkling`) — Thinking Machines — Premium · 0.56 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, efforts:low/medium/high — 0 ratings — added 2026-07-17 — active — shapes-picks: — — directory-only
  - Multimodal reasoning engine with native support for text, image, and audio analysis.

### Unbiased

- **Pareto** (`unbiased/pareto`) — Unbiased — Premium · 1.4 cr/msg — ctx 200,000 — Native Vision, Tools — 1 ratings — added 2026-09-17 — active — shapes-picks: — — directory-only
  - A multimodal engine built for complex coding, research, and agentic workflows.

- **Pareto 26.10 Preview** (`unbiased/pareto-26.10-preview`) — Unbiased — Premium · 0.46 cr/msg — ctx 500,000 — Native Vision, Tools — 0 ratings — added 2026-10-01 — active — shapes-picks: — — directory-only
  - High-capacity multimodal engine built for complex coding and agentic workflows.

### Upstage

- **Solar Pro 4** (`upstage/solar-pro4`) — Upstage — Free on shapes.inc — ctx 500,000 — Reasoning, Tools, efforts:low/medium/high — 108 ratings — added 2026-08-10 — active — shapes-picks: — — picker
  - A high-capacity model built for complex reasoning, long-document analysis, and agentic workflows.

- **Solar Pro 3** (`upstage/solar-pro-3`) — Upstage — Premium · 0.09 cr/msg — ctx 120,000 — Reasoning, efforts:low/medium/high — 1 ratings — added 2026-01-27 — active — shapes-picks: — — directory-only
  - Efficient Mixture-of-Experts model optimized for Korean, English, and Japanese language tasks.

- **Solar Mini 4** (`upstage/solar-mini4`) — Upstage — Free on shapes.inc — ctx 500,000 — Reasoning, Tools, efforts:low/medium/high — 0 ratings — added 2026-09-23 — active — shapes-picks: — — picker
  - Efficient, high-speed model optimized for agentic tasks and long-context processing in English, Korean, and Japanese.

### Writer

- **Palmyra X5** (`writer/palmyra-x5`) — Writer — Premium · 0.42 cr/msg — ctx 500,000 — none — 0 ratings — added 2026-01-21 — active — shapes-picks: — — directory-only
  - A high-capacity text-to-text engine optimized for massive document processing and enterprise-scale data analysis.

### xAI

- **Grok Latest** (`~x-ai/grok-latest`) — xAI — Premium · 1.12 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, efforts:low/medium/high, reasoning-required — 2 ratings — added 2026-07-08 — active — shapes-picks: — — directory-only
  - Dynamic access to the newest xAI model with advanced reasoning and multimodal support.

### Xiaomi

- **MiMo-V2.5** (`xiaomi/mimo-v2.5`) — Xiaomi — Free on shapes.inc — ctx 500,000 — Reasoning, Native Vision, Tools — 393 ratings — added 2026-04-22 — active — shapes-picks: — — picker
  - A capable multimodal model for creative writing and complex tasks, though hampered by strict safety filters.

- **MiMo-V2.5-Pro** (`xiaomi/mimo-v2.5-pro`) — Xiaomi — Premium · 0.23 cr/msg — ctx 500,000 — Reasoning, Tools — 385 ratings — added 2026-04-22 — active — shapes-picks: — — directory-only
  - A high-capacity model built for complex reasoning and long-form narrative coherence.

- **MiMo-V2.6-Flash** (`xiaomi/mimo-v2.6-flash`) — Xiaomi — Free on shapes.inc — ctx 500,000 — Reasoning — 35 ratings — added 2026-09-21 — active — shapes-picks: — — picker
  - A multimodal, high-context model optimized for complex agentic workflows and long-horizon reasoning.

- **MiMo-V2.6-Pro** (`xiaomi/mimo-v2.6-pro`) — Xiaomi — Premium · 0.23 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools — 1 ratings — added 2026-09-21 — active — shapes-picks: — — directory-only
  - A high-capacity model built for expansive narrative prose and complex agentic reasoning.

- **MiMo-V2.6-Pro-UltraSpeed** (`xiaomi/mimo-v2.6-pro-ultraspeed`) — Xiaomi — Premium · 2.35 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools — 0 ratings — added 2026-09-21 — active — shapes-picks: — — directory-only
  - High-speed, multimodal engine optimized for agentic workflows and long-context analysis.

### Z.ai

- **GLM 4.7 Flash** (`z-ai/glm-4.7-flash`) — Z.ai — Free on shapes.inc — ctx 200,000 — Reasoning, Tools — 1,284 ratings — added 2026-01-19 — active — shapes-picks: — — picker
  - A 30B-parameter Mixture-of-Experts engine designed for agentic coding and complex task planning.

- **GLM 5** (`z-ai/glm-5`) — Z.ai — Premium · 0.34 cr/msg — ctx 200,000 — Reasoning, Tools — 768 ratings — added 2026-02-11 — active — shapes-picks: — — directory-only
  - A high-performance foundation model balancing complex agentic reasoning with immersive, high-quality creative writing.

- **GLM 5.3 Flash** (`z-ai/glm-5.3-flash`) — Z.ai — Premium · 0.09 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, efforts:low/high, reasoning-required — 401 ratings — added 2026-08-26 — active — shapes-picks: — — directory-only
  - A highly descriptive, long-context model ideal for nuanced roleplay and complex agentic tasks.

- **GLM 5.1** (`z-ai/glm-5.1`) — Z.ai — Premium · 0.79 cr/msg — ctx 200,000 — Reasoning, Tools — 382 ratings — added 2026-04-07 — active — shapes-picks: — — directory-only
  - A specialized engine for long-horizon planning, complex coding, and immersive, lore-rich roleplay.

- **GLM 5.2** (`z-ai/glm-5.2`) — Z.ai — Premium · 0.32 cr/msg — ctx 500,000 — Reasoning, Tools, efforts:high — 94 ratings — added 2026-06-16 — active — shapes-picks: — — directory-only
  - A high-capacity reasoning engine capable of managing complex coding projects and creative roleplay.

- **GLM 5V Turbo** (`z-ai/glm-5v-turbo`) — Z.ai — Premium · 0.68 cr/msg — ctx 200,000 — Reasoning, Native Vision, Tools — 18 ratings — added 2026-04-01 — active — shapes-picks: — — directory-only
  - A native multimodal engine built for complex agentic workflows, vision-based coding, and long-horizon planning.

- **GLM 5.3** (`z-ai/glm-5.3`) — Z.ai — Premium · 0.18 cr/msg — ctx 500,000 — Reasoning, Tools, efforts:low/high, reasoning-required — 16 ratings — added 2026-08-18 — active — shapes-picks: roleplay — directory-only
  - Advanced reasoning model optimized for complex creative writing and roleplay tasks.

- **GLM 4.6V** (`z-ai/glm-4.6v`) — Z.ai — Premium · 0.17 cr/msg — ctx 120,000 — Reasoning, Native Vision, Tools — 8 ratings — added 2025-12-08 — active — shapes-picks: — — directory-only
  - Multimodal specialist for high-fidelity visual analysis, document processing, and UI reconstruction.

- **GLM Flash Latest** (`~z-ai/glm-flash-latest`) — Z.ai — Premium · 0.02 cr/msg — ctx 500,000 — Reasoning, Tools, efforts:low/high, reasoning-required — 2 ratings — added 2026-08-27 — active — shapes-picks: — — directory-only
  - High-performance multimodal engine optimized for character-driven roleplay and complex reasoning tasks.

- **GLM 5 Turbo** (`z-ai/glm-5-turbo`) — Z.ai — Premium · 0.68 cr/msg — ctx 200,000 — Reasoning, Tools — 1 ratings — added 2026-03-15 — active — shapes-picks: — — directory-only
  - High-capacity text model optimized for complex agentic workflows and tool-based instruction.

- **GLM 5.3 FlashX** (`z-ai/glm-5.3-flashx`) — Z.ai — Premium · 0.21 cr/msg — ctx 500,000 — Reasoning, Native Vision, Tools, efforts:low/high, reasoning-required — 1 ratings — added 2026-09-18 — active — shapes-picks: — — directory-only
  - High-speed multimodal engine built for massive context and complex reasoning tasks.

- **GLM Latest** (`~z-ai/glm-latest`) — Z.ai — Premium · 0.26 cr/msg — ctx 500,000 — Reasoning, Tools, efforts:low/high, reasoning-required — 1 ratings — added 2026-08-19 — active — shapes-picks: — — directory-only
  - Always provides access to the most current Z.ai model without requiring manual updates.

- **GLM 5.3 Prime** (`z-ai/glm-5.3-prime`) — Z.ai — Premium · 1.58 cr/msg — ctx 500,000 — Reasoning, Tools, efforts:low/high, reasoning-required — 0 ratings — added 2026-09-23 — active — shapes-picks: — — directory-only
  - High-speed variant optimized for rapid coding, agentic workflows, and massive context handling.

## Active, unstable

72 engines.

### Amazon

- **Nova Premier 1.0** (`amazon/nova-premier-v1`) — Amazon — Premium · 1.5 cr/msg — ctx 500,000 — Unstable — 0 ratings — added 2025-10-31 — active, unstable — shapes-picks: — — directory-only
  - A high-capacity multimodal model built for complex reasoning and large-scale data analysis.

### Anthropic

- **Claude Fable 5 (batch)** (`anthropic/claude-fable-5:batch`) — Anthropic — Premium · 3 cr/msg — ctx 500,000 — Reasoning, Unstable, reasoning-required — 0 ratings — added 2026-06-09 — active, unstable — shapes-picks: — — directory-only
  - Specialized for high-effort, asynchronous coding and complex data analysis tasks.

- **Claude Fable 5.1 (batch)** (`anthropic/claude-fable-5.1:batch`) — Anthropic — Premium · 3 cr/msg — ctx 500,000 — Reasoning, Unstable, reasoning-required — 0 ratings — added 2026-09-01 — active, unstable — shapes-picks: — — directory-only
  - Asynchronous engine optimized for large-scale code refactoring and complex reasoning tasks.

- **Claude Haiku 4.5 (batch)** (`anthropic/claude-haiku-4.5:batch`) — Anthropic — Premium · 0.3 cr/msg — ctx 200,000 — Unstable — 0 ratings — added 2025-10-15 — active, unstable — shapes-picks: — — directory-only
  - Efficient, high-volume model optimized for asynchronous coding, reasoning, and large-scale data analysis.

- **Claude Opus 4.5 (batch)** (`anthropic/claude-opus-4.5:batch`) — Anthropic — Premium · 1.5 cr/msg — ctx 200,000 — Unstable — 0 ratings — added 2025-11-24 — active, unstable — shapes-picks: — — directory-only
  - High-reasoning engine optimized for complex, asynchronous data analysis and large-scale software engineering tasks.

- **Claude Opus 4.6 (batch)** (`anthropic/claude-opus-4.6:batch`) — Anthropic — Premium · 1.5 cr/msg — ctx 500,000 — Unstable — 0 ratings — added 2026-02-04 — active, unstable — shapes-picks: — — directory-only
  - High-capacity asynchronous processing for complex codebases and large-scale technical analysis.

- **Claude Opus 4.7 (batch)** (`anthropic/claude-opus-4.7:batch`) — Anthropic — Premium · 1.5 cr/msg — ctx 500,000 — Unstable — 0 ratings — added 2026-04-16 — active, unstable — shapes-picks: — — directory-only
  - Specialized for asynchronous, large-scale reasoning and complex multi-step project orchestration.

- **Claude Opus 4.8 (batch)** (`anthropic/claude-opus-4.8:batch`) — Anthropic — Premium · 1.5 cr/msg — ctx 500,000 — Unstable — 0 ratings — added 2026-05-27 — active, unstable — shapes-picks: — — directory-only
  - High-capacity reasoning engine optimized for asynchronous, large-scale data processing and complex project orchestration.

- **Claude Opus 5 (batch)** (`anthropic/claude-opus-5:batch`) — Anthropic — Premium · 1.5 cr/msg — ctx 500,000 — Unstable — 0 ratings — added 2026-07-24 — active, unstable — shapes-picks: — — directory-only
  - High-capacity asynchronous processing for complex reasoning, coding, and large-scale document analysis.

- **Claude Opus 5.5 (batch)** (`anthropic/claude-opus-5.5:batch`) — Anthropic — Premium · 1.2 cr/msg — ctx 500,000 — Reasoning, Unstable, reasoning-required — 0 ratings — added 2026-09-22 — active, unstable — shapes-picks: — — directory-only
  - High-capacity reasoning and code analysis optimized for asynchronous, high-volume tasks.

- **Claude Sonnet 4.6 (batch)** (`anthropic/claude-sonnet-4.6:batch`) — Anthropic — Premium · 0.9 cr/msg — ctx 500,000 — Unstable — 0 ratings — added 2026-02-17 — active, unstable — shapes-picks: — — directory-only
  - Cost-effective, high-throughput processing for complex reasoning and large-scale data tasks.

- **Claude Sonnet 5 (batch)** (`anthropic/claude-sonnet-5:batch`) — Anthropic — Premium · 0.6 cr/msg — ctx 500,000 — Unstable — 0 ratings — added 2026-06-30 — active, unstable — shapes-picks: — — directory-only
  - High-throughput, asynchronous engine optimized for large-scale coding and complex reasoning tasks.

- **Claude Sonnet 5.5 (batch)** (`anthropic/claude-sonnet-5.5:batch`) — Anthropic — Premium · 0.6 cr/msg — ctx 500,000 — Reasoning, Unstable, reasoning-required — 0 ratings — added 2026-09-28 — active, unstable — shapes-picks: — — directory-only
  - Optimized for high-volume, non-latency-sensitive tasks like coding, document generation, and data processing.

### DeepSeek

- **DeepSeek V4.1 Flash (batch)** (`deepseek/deepseek-v4.1-flash:batch`) — DeepSeek — Premium · 0.06 cr/msg — ctx 500,000 — Unstable — 0 ratings — added 2026-09-10 — active, unstable — shapes-picks: — — directory-only
  - High-efficiency model optimized for asynchronous, large-scale data processing and complex agentic tasks.

### Google

- **Gemini 3 Flash Preview (batch)** (`google/gemini-3-flash-preview:batch`) — Google — Premium · 0.16 cr/msg — ctx 500,000 — Unstable — 0 ratings — added 2025-12-17 — active, unstable — shapes-picks: — — directory-only
  - High-throughput, multimodal reasoning engine optimized for large-scale asynchronous data processing.

- **Gemini 3.1 Flash Lite (batch)** (`google/gemini-3.1-flash-lite:batch`) — Google — Premium · 0.08 cr/msg — ctx 500,000 — Unstable — 0 ratings — added 2026-05-07 — active, unstable — shapes-picks: — — directory-only
  - High-efficiency, asynchronous model built for large-scale data processing and document analysis.

- **Gemini 3.1 Pro Preview (batch)** (`google/gemini-3.1-pro-preview:batch`) — Google — Premium · 0.62 cr/msg — ctx 500,000 — Reasoning, Unstable, reasoning-required — 0 ratings — added 2026-02-19 — active, unstable — shapes-picks: — — directory-only
  - High-throughput multimodal reasoning for large-scale, asynchronous data analysis and complex workflows.

- **Gemini 3.5 Flash (batch)** (`google/gemini-3.5-flash:batch`) — Google — Premium · 0.46 cr/msg — ctx 500,000 — Reasoning, Unstable, reasoning-required — 0 ratings — added 2026-05-19 — active, unstable — shapes-picks: — — directory-only
  - High-volume, asynchronous processing for large-scale coding, reasoning, and multimodal analysis.

- **Gemini 3.5 Flash Lite (batch)** (`google/gemini-3.5-flash-lite:batch`) — Google — Premium · 0.1 cr/msg — ctx 500,000 — Reasoning, Unstable, reasoning-required — 0 ratings — added 2026-07-21 — active, unstable — shapes-picks: — — directory-only
  - High-efficiency model optimized for asynchronous, large-scale data processing and complex agentic workflows.

- **Gemini 3.6 Flash (batch)** (`google/gemini-3.6-flash:batch`) — Google — Premium · 0.22 cr/msg — ctx 500,000 — Reasoning, Unstable, reasoning-required — 0 ratings — added 2026-07-21 — active, unstable — shapes-picks: — — directory-only
  - High-efficiency, asynchronous processing for large-scale document analysis and complex coding tasks.

- **Gemini 3.7 Flash (batch)** (`google/gemini-3.7-flash:batch`) — Google — Premium · 0.22 cr/msg — ctx 500,000 — Reasoning, Unstable, reasoning-required — 0 ratings — added 2026-08-13 — active, unstable — shapes-picks: — — directory-only
  - High-throughput engine built for large-scale, asynchronous reasoning and complex data analysis.

- **Gemini 3.8 Flash (batch)** (`google/gemini-3.8-flash:batch`) — Google — Premium · 0.22 cr/msg — ctx 500,000 — Reasoning, Unstable, reasoning-required — 0 ratings — added 2026-09-02 — active, unstable — shapes-picks: — — directory-only
  - High-volume, asynchronous processing for complex coding, reasoning, and large-scale multimodal analysis.

### inclusionAI

- **Ling 3.1 Flash** (`inclusionai/ling-3.1-flash`) — inclusionAI — Free on shapes.inc — ctx 200,000 — Unstable — 0 ratings — added 2026-10-02 — active, unstable — shapes-picks: — — picker
  - High-capacity reasoning model with a massive context window and zero-cost access.

### Kwaipilot

- **KAT-Coder-Pro V2.5** (`kwaipilot/kat-coder-pro-v2.5`) — Kwaipilot — Premium · 0.43 cr/msg — ctx 200,000 — Unstable — 0 ratings — added 2026-07-10 — active, unstable — shapes-picks: — — directory-only
  - Specialized agentic model built for autonomous repository navigation and complex software engineering workflows.

### Mistral

- **Mistral Large 3 2512** (`mistralai/mistral-large-2512`) — Mistral — Premium · 0.28 cr/msg — ctx 200,000 — Unstable — 36 ratings — added 2025-12-01 — active, unstable — shapes-picks: — — directory-only
  - A high-capacity model built for complex reasoning, large-scale document analysis, and agentic workflows.

- **Ministral 3 8B 2512 (batch)** (`mistralai/ministral-8b-2512:batch`) — Mistral — Free on shapes.inc — ctx 200,000 — Unstable — 0 ratings — added 2025-12-02 — active, unstable — shapes-picks: — — picker
  - Efficient, high-context multimodal processing for large-scale asynchronous tasks.

- **Mistral Large 3 2512 (batch)** (`mistralai/mistral-large-2512:batch`) — Mistral — Premium · 0.14 cr/msg — ctx 200,000 — Unstable — 0 ratings — added 2025-12-01 — active, unstable — shapes-picks: — — directory-only
  - High-capacity asynchronous processing for large-scale reasoning and structured data analysis.

- **Mistral Medium 3.5 (batch)** (`mistralai/mistral-medium-3-5:batch`) — Mistral — Premium · 0.45 cr/msg — ctx 200,000 — Unstable — 0 ratings — added 2026-04-30 — active, unstable — shapes-picks: — — directory-only
  - High-capacity asynchronous model optimized for complex reasoning, coding, and large-scale data processing.

- **Mistral Small 4 (batch)** (`mistralai/mistral-small-2603:batch`) — Mistral — Free on shapes.inc — ctx 200,000 — Unstable — 0 ratings — added 2026-03-16 — active, unstable — shapes-picks: — — picker
  - High-throughput, multimodal model optimized for complex reasoning and large-scale asynchronous tasks.

### MoonshotAI

- **Kimi K3 (batch)** (`moonshotai/kimi-k3:batch`) — MoonshotAI — Premium · 1.37 cr/msg — ctx 500,000 — Unstable — 0 ratings — added 2026-07-16 — active, unstable — shapes-picks: — — directory-only
  - A high-capacity multimodal engine optimized for asynchronous processing of large-scale coding and reasoning tasks.

### OpenAI

- **GPT Chat Latest** (`openai/gpt-chat-latest`) — OpenAI — Premium · 3.1 cr/msg — ctx 200,000 — Unstable — 14 ratings — added 2026-05-05 — active, unstable — shapes-picks: — — directory-only
  - A dynamic alias that automatically provides access to the most recent OpenAI chat model.

- **GPT-5.2 Chat** (`openai/gpt-5.2-chat`) — OpenAI — Premium · 1.16 cr/msg — ctx 120,000 — Unstable — 1 ratings — added 2025-12-10 — active, unstable — shapes-picks: — — directory-only
  - A high-speed, responsive engine optimized for efficient daily interactions and structured data tasks.

- **GPT-5.5 Pro** (`openai/gpt-5.5-pro`) — OpenAI — Premium · 18.6 cr/msg — ctx 500,000 — Reasoning, Unstable, reasoning-required — 1 ratings — added 2026-04-24 — active, unstable — shapes-picks: — — directory-only
  - Advanced reasoning engine built for complex, multi-step problem solving and long-horizon workflows.

- **GPT Astra Latest** (`~openai/gpt-astra-latest`) — OpenAI — Premium · 6 cr/msg — ctx 500,000 — Reasoning, Unstable, reasoning-required — 0 ratings — added 2026-09-11 — active, unstable — shapes-picks: — — directory-only
  - Automatically routes to the most current GPT Astra model for advanced reasoning and large-scale document analysis.

- **GPT Luna Latest** (`~openai/gpt-luna-latest`) — OpenAI — Premium · 0.06 cr/msg — ctx 500,000 — Unstable — 0 ratings — added 2026-09-11 — active, unstable — shapes-picks: — — directory-only
  - A dynamic routing alias that automatically connects to the most current version of the GPT Luna family.

- **GPT Mini Latest** (`~openai/gpt-mini-latest`) — OpenAI — Premium · 0.46 cr/msg — ctx 200,000 — Unstable — 0 ratings — added 2026-04-27 — active, unstable — shapes-picks: — — directory-only
  - A dynamic routing alias that provides automatic access to the most recent iteration of the GPT Mini family.

- **GPT Sol Latest** (`~openai/gpt-sol-latest`) — OpenAI — Premium · 1.2 cr/msg — ctx 500,000 — Reasoning, Unstable, reasoning-required — 0 ratings — added 2026-09-11 — active, unstable — shapes-picks: — — directory-only
  - Dynamic reasoning engine for large-scale data analysis and complex, agentic tasks.

- **GPT Terra Latest** (`~openai/gpt-terra-latest`) — OpenAI — Premium · 1.24 cr/msg — ctx 500,000 — Unstable — 0 ratings — added 2026-09-11 — active, unstable — shapes-picks: — — directory-only
  - High-capacity reasoning engine designed for massive documents and complex analytical workflows.

- **GPT-5 Pro** (`openai/gpt-5-pro`) — OpenAI — Premium · 9.9 cr/msg — ctx 200,000 — Reasoning, Unstable, reasoning-required — 0 ratings — added 2025-10-06 — active, unstable — shapes-picks: — — directory-only
  - A high-performance engine built for complex reasoning, precise coding, and large-scale data analysis.

- **GPT-5 Pro (batch)** (`openai/gpt-5-pro:batch`) — OpenAI — Premium · 4.95 cr/msg — ctx 200,000 — Reasoning, Unstable, reasoning-required — 0 ratings — added 2025-10-06 — active, unstable — shapes-picks: — — directory-only
  - High-accuracy reasoning and complex data processing for asynchronous, large-scale tasks.

- **GPT-5.1 (batch)** (`openai/gpt-5.1:batch`) — OpenAI — Premium · 0.41 cr/msg — ctx 200,000 — Unstable — 0 ratings — added 2025-11-13 — active, unstable — shapes-picks: — — directory-only
  - High-capacity, asynchronous reasoning engine for complex data analysis and large-scale projects.

- **GPT-5.2 (batch)** (`openai/gpt-5.2:batch`) — OpenAI — Premium · 0.58 cr/msg — ctx 200,000 — Unstable — 0 ratings — added 2025-12-10 — active, unstable — shapes-picks: — — directory-only
  - High-capacity frontier reasoning optimized for asynchronous, large-scale data processing.

- **GPT-5.2 Pro** (`openai/gpt-5.2-pro`) — OpenAI — Premium · 13.86 cr/msg — ctx 200,000 — Reasoning, Unstable, reasoning-required — 0 ratings — added 2025-12-10 — active, unstable — shapes-picks: — — directory-only
  - Advanced reasoning model optimized for complex coding, high-stakes accuracy, and long-context analysis.

- **GPT-5.2 Pro (batch)** (`openai/gpt-5.2-pro:batch`) — OpenAI — Premium · 6.93 cr/msg — ctx 200,000 — Reasoning, Unstable, reasoning-required — 0 ratings — added 2025-12-10 — active, unstable — shapes-picks: — — directory-only
  - High-accuracy reasoning and long-context analysis optimized for asynchronous, high-volume tasks.

- **GPT-5.4 (batch)** (`openai/gpt-5.4:batch`) — OpenAI — Premium · 0.78 cr/msg — ctx 500,000 — Unstable — 0 ratings — added 2026-03-05 — active, unstable — shapes-picks: — — directory-only
  - High-capacity asynchronous processing for complex coding, reasoning, and large-scale document analysis.

- **GPT-5.4 Mini (batch)** (`openai/gpt-5.4-mini:batch`) — OpenAI — Premium · 0.23 cr/msg — ctx 200,000 — Unstable — 0 ratings — added 2026-03-17 — active, unstable — shapes-picks: — — directory-only
  - High-throughput engine optimized for large-scale coding, reasoning, and structured data extraction tasks.

- **GPT-5.4 Nano (batch)** (`openai/gpt-5.4-nano:batch`) — OpenAI — Premium · 0.06 cr/msg — ctx 200,000 — Unstable — 0 ratings — added 2026-03-17 — active, unstable — shapes-picks: — — directory-only
  - High-throughput, cost-efficient engine optimized for large-scale data extraction and automated workflows.

- **GPT-5.4 Pro (batch)** (`openai/gpt-5.4-pro:batch`) — OpenAI — Premium · 9.3 cr/msg — ctx 500,000 — Reasoning, Unstable, reasoning-required — 0 ratings — added 2026-03-05 — active, unstable — shapes-picks: — — directory-only
  - High-capacity engine for complex, asynchronous analytical tasks and large-scale data processing.

- **GPT-5.5 (batch)** (`openai/gpt-5.5:batch`) — OpenAI — Premium · 1.55 cr/msg — ctx 500,000 — Unstable — 0 ratings — added 2026-04-24 — active, unstable — shapes-picks: — — directory-only
  - High-capacity frontier model optimized for complex, asynchronous professional analysis and coding tasks.

- **GPT-5.5 Pro (batch)** (`openai/gpt-5.5-pro:batch`) — OpenAI — Premium · 9.3 cr/msg — ctx 500,000 — Reasoning, Unstable, reasoning-required — 0 ratings — added 2026-04-24 — active, unstable — shapes-picks: — — directory-only
  - High-capacity batch processing for complex reasoning and large-scale data analysis.

- **GPT-5.6 Luna (batch)** (`openai/gpt-5.6-luna:batch`) — OpenAI — Premium · 0.06 cr/msg — ctx 500,000 — Unstable — 0 ratings — added 2026-07-09 — active, unstable — shapes-picks: — — directory-only
  - High-capacity engine optimized for asynchronous data analysis and large-scale batch processing.

- **GPT-5.6 Luna Pro (batch)** (`openai/gpt-5.6-luna-pro:batch`) — OpenAI — Premium · 0.06 cr/msg — ctx 500,000 — Unstable — 0 ratings — added 2026-07-09 — active, unstable — shapes-picks: — — directory-only
  - High-reasoning engine optimized for complex, asynchronous batch processing and large-scale data analysis.

- **GPT-5.6 Sol (batch)** (`openai/gpt-5.6-sol:batch`) — OpenAI — Premium · 0.6 cr/msg — ctx 500,000 — Unstable — 0 ratings — added 2026-07-09 — active, unstable — shapes-picks: — — directory-only
  - High-capacity reasoning engine optimized for asynchronous, large-scale data analysis and complex coding workflows.

- **GPT-5.6 Sol Pro (batch)** (`openai/gpt-5.6-sol-pro:batch`) — OpenAI — Premium · 0.6 cr/msg — ctx 500,000 — Unstable — 0 ratings — added 2026-07-09 — active, unstable — shapes-picks: — — directory-only
  - Specialized for high-stakes, asynchronous reasoning tasks and massive document analysis.

- **GPT-5.6 Terra (batch)** (`openai/gpt-5.6-terra:batch`) — OpenAI — Premium · 0.62 cr/msg — ctx 500,000 — Unstable — 0 ratings — added 2026-07-09 — active, unstable — shapes-picks: — — directory-only
  - High-volume, asynchronous processing for complex reasoning and massive document analysis.

- **GPT-5.6 Terra Pro (batch)** (`openai/gpt-5.6-terra-pro:batch`) — OpenAI — Premium · 0.62 cr/msg — ctx 500,000 — Unstable — 0 ratings — added 2026-07-09 — active, unstable — shapes-picks: — — directory-only
  - High-reasoning engine optimized for large-scale, asynchronous data processing and complex document analysis.

- **GPT-6 Astra (batch)** (`openai/gpt-6-astra:batch`) — OpenAI — Premium · 3 cr/msg — ctx 500,000 — Reasoning, Unstable, reasoning-required — 0 ratings — added 2026-09-04 — active, unstable — shapes-picks: — — directory-only
  - High-capacity engine optimized for asynchronous, long-horizon reasoning and large-scale data analysis.

- **GPT-6 Astra Pro (batch)** (`openai/gpt-6-astra-pro:batch`) — OpenAI — Premium · 3 cr/msg — ctx 500,000 — Reasoning, Unstable, reasoning-required — 0 ratings — added 2026-09-04 — active, unstable — shapes-picks: — — directory-only
  - High-accuracy reasoning for large-scale, asynchronous data analysis and complex document processing.

- **GPT-6 Luna (batch)** (`openai/gpt-6-luna:batch`) — OpenAI — Free on shapes.inc — ctx 500,000 — Unstable — 0 ratings — added 2026-09-22 — active, unstable — shapes-picks: — — picker
  - High-efficiency engine built for large-scale, asynchronous data processing and complex reasoning tasks.

- **GPT-6 Luna Pro (batch)** (`openai/gpt-6-luna-pro:batch`) — OpenAI — Free on shapes.inc — ctx 500,000 — Unstable — 0 ratings — added 2026-09-22 — active, unstable — shapes-picks: — — picker
  - High-accuracy reasoning for large-scale, asynchronous document analysis and complex data processing.

- **GPT-6 Sol (batch)** (`openai/gpt-6-sol:batch`) — OpenAI — Premium · 0.6 cr/msg — ctx 500,000 — Unstable — 0 ratings — added 2026-09-22 — active, unstable — shapes-picks: — — directory-only
  - High-reliability model optimized for cost-effective, asynchronous processing of large-scale coding and data tasks.

- **GPT-6 Sol Pro (batch)** (`openai/gpt-6-sol-pro:batch`) — OpenAI — Premium · 0.6 cr/msg — ctx 500,000 — Unstable — 0 ratings — added 2026-09-22 — active, unstable — shapes-picks: — — directory-only
  - High-accuracy reasoning engine optimized for large-scale, asynchronous data processing.

- **GPT-6.1 Sol** (`openai/gpt-6.1-sol`) — OpenAI — Premium · 1.2 cr/msg — ctx 500,000 — Reasoning, Unstable, reasoning-required — 0 ratings — added 2026-09-29 — active, unstable — shapes-picks: — — directory-only
  - High-performance reasoning model optimized for complex coding, document analysis, and agentic workflows.

- **GPT-6.1 Sol Pro** (`openai/gpt-6.1-sol-pro`) — OpenAI — Premium · 1.2 cr/msg — ctx 500,000 — Reasoning, Tools, Unstable, reasoning-required — 0 ratings — added 2026-09-29 — active, unstable — shapes-picks: — — directory-only
  - Advanced reasoning engine optimized for complex, high-stakes analytical tasks.

### Qwen

- **Qwen3.8 Flash** (`qwen/qwen3.8-flash`) — Qwen — Premium · 0.08 cr/msg — ctx 500,000 — Unstable — 0 ratings — added 2026-08-26 — active, unstable — shapes-picks: — — directory-only
  - A reasoning-focused model optimized for complex coding, visual analysis, and agentic workflows.

### shapes.inc

- **shapes-1** (`shapes-1`) — shapes.inc — Free on shapes.inc — ctx 30,000 — Unstable — 16 ratings — added 2026-06-16 — active, unstable — shapes-picks: — — picker
  - shapes.inc's first in-house model, trained and served by shapes.inc.

### SpaceXAI

- **Grok 4.5** (`x-ai/grok-4.5`) — SpaceXAI — Premium · 1.12 cr/msg — ctx 500,000 — Reasoning, Tools, Unstable, efforts:low/medium/high, reasoning-required — 9 ratings — added 2026-07-08 — active, unstable — shapes-picks: — — directory-only
  - A high-reasoning engine optimized for complex coding, STEM tasks, and agentic workflows.

- **Grok 4.3 (batch)** (`x-ai/grok-4.3:batch`) — SpaceXAI — Premium · 0.54 cr/msg — ctx 500,000 — Unstable — 0 ratings — added 2026-04-30 — active, unstable — shapes-picks: — — directory-only
  - A high-capacity reasoning engine optimized for asynchronous, large-scale document analysis and complex agentic tasks.

### Thinking Machines

- **Inkling Small** (`thinkingmachines/inkling-small`) — Thinking Machines — Premium · 0.25 cr/msg — ctx 500,000 — Unstable — 0 ratings — added 2026-07-30 — active, unstable — shapes-picks: — — directory-only
  - Efficient multimodal model optimized for complex reasoning, coding, and large-scale agentic workflows.

### Z.ai

- **GLM 4.7** (`z-ai/glm-4.7`) — Z.ai — Premium · 0.34 cr/msg — ctx 200,000 — Unstable — 2 ratings — added 2025-12-22 — active, unstable — shapes-picks: — — directory-only
  - A reasoning-focused model designed for complex coding, agentic workflows, and long-form logical consistency.

- **GLM 5.3 (batch)** (`z-ai/glm-5.3:batch`) — Z.ai — Premium · 0.27 cr/msg — ctx 500,000 — Reasoning, Unstable, reasoning-required — 0 ratings — added 2026-08-18 — active, unstable — shapes-picks: — — directory-only
  - Specialized reasoning engine for deep analysis of massive codebases and complex agentic workflows.

- **GLM 5.3 Flash (batch)** (`z-ai/glm-5.3-flash:batch`) — Z.ai — Free on shapes.inc — ctx 500,000 — Reasoning, Unstable, reasoning-required — 0 ratings — added 2026-08-26 — active, unstable — shapes-picks: — — picker
  - High-volume multimodal engine optimized for complex coding and long-horizon agentic tasks.

## Legacy

154 engines.

### AionLabs

- **Aion-RP 1.0 (8B)** (`aion-labs/aion-rp-llama-3.1-8b`) — AionLabs — Premium · 0.43 cr/msg — ctx 30,000 — none — 11 ratings — added 2025-02-04 — legacy — shapes-picks: — — directory-only
  - Specialized creative engine optimized for natural, character-driven roleplay and narrative depth.

### Amazon

- **Nova Lite 1.0** (`amazon/nova-lite-v1`) — Amazon — Free on shapes.inc — ctx 200,000 — none — 0 ratings — added 2024-12-05 — legacy — shapes-picks: — — picker
  - Amazon Nova Lite 1.0 is a very low-cost multimodal model from Amazon that focused on fast processing of image, video, and text inputs to generate text output. Amazon Nova Lite...

- **Nova Micro 1.0** (`amazon/nova-micro-v1`) — Amazon — Free on shapes.inc — ctx 120,000 — none — 0 ratings — added 2024-12-05 — legacy — shapes-picks: — — picker
  - A high-speed, cost-efficient text model optimized for rapid summarization and interactive chat.

- **Nova Pro 1.0** (`amazon/nova-pro-v1`) — Amazon — Premium · 0.46 cr/msg — ctx 200,000 — none — 0 ratings — added 2024-12-05 — legacy — shapes-picks: — — directory-only
  - A balanced multimodal model optimized for complex document analysis and visual reasoning.

### Anthracite Org

- **Magnum v4 72B** (`anthracite-org/magnum-v4-72b`) — Anthracite Org — Premium · 1.35 cr/msg — ctx 30,000 — none — 0 ratings — added 2024-10-22 — legacy — shapes-picks: — — directory-only
  - A specialized fine-tune optimized for high-quality creative writing and immersive roleplay.

### Anthropic

- **Claude Sonnet 4.5** (`anthropic/claude-sonnet-4.5`) — Anthropic — Premium · 1.8 cr/msg — ctx 500,000 — Native Vision, Tools — 436 ratings — added 2025-09-29 — legacy — shapes-picks: — — directory-only
  - A high-performance engine for complex coding, agentic tasks, and detailed creative writing with a massive context window.

- **Claude Sonnet 4** (`anthropic/claude-sonnet-4`) — Anthropic — Premium · 1.8 cr/msg — ctx 200,000 — none — 17 ratings — added 2025-05-22 — legacy — shapes-picks: — — directory-only
  - A high-precision engine optimized for complex coding, reasoning, and autonomous agent workflows.

- **Claude Opus 4.1** (`anthropic/claude-opus-4.1`) — Anthropic — Premium · 9 cr/msg — ctx 200,000 — none — 2 ratings — added 2025-08-05 — legacy — shapes-picks: — — directory-only
  - A high-precision model built for complex reasoning, multi-file coding, and large-scale data analysis.

- **Claude Opus 4.1 (batch)** (`anthropic/claude-opus-4.1:batch`) — Anthropic — Premium · 4.5 cr/msg — ctx 200,000 — none — 0 ratings — added 2025-08-05 — legacy — shapes-picks: — — directory-only
  - High-volume, asynchronous processing for complex coding, reasoning, and large-scale data analysis.

- **Claude Sonnet 4.5 (batch)** (`anthropic/claude-sonnet-4.5:batch`) — Anthropic — Premium · 0.9 cr/msg — ctx 500,000 — Unstable — 0 ratings — added 2025-09-29 — legacy, unstable — shapes-picks: — — directory-only
  - High-throughput engine optimized for asynchronous coding tasks and complex agentic workflows.

### Baidu

- **ERNIE 4.5 VL 424B A47B** (`baidu/ernie-4.5-vl-424b-a47b`) — Baidu — Premium · 0.23 cr/msg — ctx 120,000 — none — 6 ratings — added 2025-06-30 — legacy — shapes-picks: — — directory-only
  - High-fidelity multimodal reasoning with support for both standard and chain-of-thought inference modes.

### ByteDance

- **UI-TARS 7B** (`bytedance/ui-tars-1.5-7b`) — ByteDance — Free on shapes.inc — ctx 120,000 — none — 1 ratings — added 2025-07-22 — legacy — shapes-picks: — — picker
  - Specialized vision-language agent designed for navigating desktop, web, and mobile interfaces.

### Cohere

- **Command R7B (12-2024)** (`cohere/command-r7b-12-2024`) — Cohere — Free on shapes.inc — ctx 120,000 — none — 4 ratings — added 2024-12-14 — legacy — shapes-picks: — — picker
  - Efficient reasoning model optimized for large-scale document analysis and complex agentic workflows.

- **Command R (08-2024)** (`cohere/command-r-08-2024`) — Cohere — Premium · 0.09 cr/msg — ctx 120,000 — none — 1 ratings — added 2024-08-30 — legacy — shapes-picks: — — directory-only
  - A specialized model optimized for tool use, complex reasoning, and multilingual retrieval tasks.

- **Command A** (`cohere/command-a`) — Cohere — Premium · 1.45 cr/msg — ctx 200,000 — none — 0 ratings — added 2025-03-13 — legacy — shapes-picks: — — directory-only
  - A large-scale model optimized for complex agentic workflows, coding tasks, and long-context analysis.

- **Command R+ (08-2024)** (`cohere/command-r-plus-08-2024`) — Cohere — Premium · 1.45 cr/msg — ctx 120,000 — none — 0 ratings — added 2024-08-30 — legacy — shapes-picks: — — directory-only
  - A high-performance model specialized in grounded reasoning, multi-step tool use, and complex document analysis.

### DeepSeek

- **DeepSeek V3 0324** (`deepseek/deepseek-chat-v3-0324`) — DeepSeek — Premium · 0.17 cr/msg — ctx 120,000 — none — 281 ratings — added 2025-03-24 — legacy — shapes-picks: — — directory-only
  - A large-scale mixture-of-experts model optimized for complex analytical tasks, coding, and structured data processing.

- **DeepSeek V3.2 Exp** (`deepseek/deepseek-v3.2-exp`) — DeepSeek — Premium · 0.14 cr/msg — ctx 120,000 — Tools — 88 ratings — added 2025-09-29 — legacy — shapes-picks: — — directory-only
  - Experimental model optimized for long-context efficiency and complex reasoning tasks.

- **DeepSeek V3.1** (`deepseek/deepseek-chat-v3.1`) — DeepSeek — Premium · 0.14 cr/msg — ctx 120,000 — Reasoning — 80 ratings — added 2025-08-21 — legacy — shapes-picks: — — directory-only
  - A hybrid reasoning model that lets you toggle between standard responses and deep-thinking mode for complex technical tasks.

- **DeepSeek V3** (`deepseek/deepseek-chat`) — DeepSeek — Premium · 0.15 cr/msg — ctx 120,000 — none — 46 ratings — added 2024-12-26 — legacy — shapes-picks: — — directory-only
  - Highly capable reasoning engine for complex coding, mathematics, and structured data tasks.

- **DeepSeek V3.1 Terminus** (`deepseek/deepseek-v3.1-terminus`) — DeepSeek — Premium · 0.16 cr/msg — ctx 120,000 — Tools — 26 ratings — added 2025-09-22 — legacy — shapes-picks: — — directory-only
  - High-performance hybrid reasoning model optimized for complex coding tasks and agentic workflows.

- **R1** (`deepseek/deepseek-r1`) — DeepSeek — Premium · 0.4 cr/msg — ctx 30,000 — Reasoning, reasoning-required — 0 ratings — added 2025-01-20 — legacy — shapes-picks: — — directory-only
  - A reasoning-focused engine that generates internal chain-of-thought to solve complex coding and analytical problems.

- **R1 0528** (`deepseek/deepseek-r1-0528`) — DeepSeek — Premium · 0.29 cr/msg — ctx 120,000 — Reasoning, reasoning-required — 0 ratings — added 2025-05-28 — legacy — shapes-picks: — — directory-only
  - May 28th update to the [original DeepSeek R1](/deepseek/deepseek-r1) Performance on par with [OpenAI o1](/openai/o1), but open-sourced and with fully open reasoning tokens. It's 671B parameters in size, with 37B active...

### Google

- **Gemma 3 27B** (`google/gemma-3-27b-it`) — Google — Premium · 0.05 cr/msg — ctx 120,000 — Unstable — 8,479 ratings — added 2025-03-12 — legacy, unstable — shapes-picks: — — directory-only
  - A flexible, multimodal engine well-suited for character-driven roleplay and general analysis.

- **Gemini 2.5 Flash Lite** (`google/gemini-2.5-flash-lite`) — Google — Free on shapes.inc — ctx 500,000 — none — 4,358 ratings — added 2025-07-22 — legacy — shapes-picks: — — picker
  - A high-speed, cost-effective engine built for rapid, lightweight interactions and large-scale tasks.

- **Gemini 2.5 Pro** (`google/gemini-2.5-pro`) — Google — Premium · 0.83 cr/msg — ctx 500,000 — Reasoning, reasoning-required — 40 ratings — added 2025-06-17 — legacy — shapes-picks: — — directory-only
  - A high-capacity reasoning engine built for large-scale data analysis, complex coding, and multimodal synthesis.

- **Gemma 2 27B** (`google/gemma-2-27b-it`) — Google — Premium · 0.34 cr/msg — ctx 8,000 — none — 11 ratings — added 2024-07-13 — legacy — shapes-picks: — — directory-only
  - A balanced, instruction-tuned model optimized for efficient reasoning and text generation.

- **Gemini 2.5 Flash** (`google/gemini-2.5-flash`) — Google — Premium · 0.2 cr/msg — ctx 500,000 — none — 6 ratings — added 2025-06-17 — legacy — shapes-picks: — — directory-only
  - High-speed multimodal model optimized for complex reasoning, coding, and large-scale data analysis.

- **Gemma 3 4B** (`google/gemma-3-4b-it`) — Google — Free on shapes.inc — ctx 120,000 — none — 4 ratings — added 2025-03-13 — legacy — shapes-picks: — — picker
  - A lightweight, multimodal model efficient for text and image processing tasks.

- **Gemma 3 12B** (`google/gemma-3-12b-it`) — Google — Free on shapes.inc — ctx 120,000 — none — 1 ratings — added 2025-03-13 — legacy — shapes-picks: — — picker
  - Multimodal model with a large context window for document analysis and image-based tasks.

- **Gemini 2.5 Flash (batch)** (`google/gemini-2.5-flash:batch`) — Google — Premium · 0.1 cr/msg — ctx 500,000 — none — 0 ratings — added 2025-06-17 — legacy — shapes-picks: — — directory-only
  - High-throughput engine for large-scale reasoning, coding, and extensive document analysis.

- **Gemini 2.5 Flash Lite (batch)** (`google/gemini-2.5-flash-lite:batch`) — Google — Free on shapes.inc — ctx 500,000 — none — 0 ratings — added 2025-07-22 — legacy — shapes-picks: — — picker
  - High-throughput, cost-effective engine for processing large-scale datasets and asynchronous analytical tasks.

- **Gemini 2.5 Pro (batch)** (`google/gemini-2.5-pro:batch`) — Google — Premium · 0.41 cr/msg — ctx 500,000 — Reasoning, reasoning-required — 0 ratings — added 2025-06-17 — legacy — shapes-picks: — — directory-only
  - High-volume, multimodal reasoning engine optimized for complex analysis and large-scale asynchronous tasks.

- **Gemini 2.5 Pro Preview 06-05** (`google/gemini-2.5-pro-preview`) — Google — Premium · 0.83 cr/msg — ctx 500,000 — Reasoning, reasoning-required — 0 ratings — added 2025-06-05 — legacy — shapes-picks: — — directory-only
  - Gemini 2.5 Pro is Google’s state-of-the-art AI model designed for advanced reasoning, coding, mathematics, and scientific tasks. It employs “thinking” capabilities, enabling it to reason through responses with enhanced accuracy...

### Gryphe

- **MythoMax 13B** (`gryphe/mythomax-l2-13b`) — Gryphe — Free on shapes.inc — ctx 8,000 — none — 137 ratings — added 2023-07-02 — legacy — shapes-picks: — — picker
  - A classic Llama 2-based model favored for creative writing and roleplay.

### Mancer

- **Weaver (alpha)** (`mancer/weaver`) — Mancer — Premium · 0.21 cr/msg — ctx 8,000 — none — 2 ratings — added 2023-08-02 — legacy — shapes-picks: — — directory-only
  - High-verbosity narrative engine designed to emulate Claude-style prose for creative writing.

### Meta

- **Llama 3.3 70B Instruct** (`meta-llama/llama-3.3-70b-instruct`) — Meta — Premium · 0.12 cr/msg — ctx 120,000 — none — 4,361 ratings — added 2024-12-06 — legacy — shapes-picks: — — directory-only
  - A high-performance, multilingual model ideal for immersive roleplay and long-form creative dialogue.

- **Llama 3.1 70B Instruct** (`meta-llama/llama-3.1-70b-instruct`) — Meta — Premium · 0.21 cr/msg — ctx 120,000 — none — 688 ratings — added 2024-07-23 — legacy — shapes-picks: — — directory-only
  - A balanced model for complex reasoning and long-form dialogue that occasionally struggles with repetition.

- **Llama 4 Maverick** (`meta-llama/llama-4-maverick`) — Meta — Premium · 0.11 cr/msg — ctx 500,000 — none — 167 ratings — added 2025-04-05 — legacy — shapes-picks: — — directory-only
  - A high-capacity multimodal model built for long-context narrative flow and complex visual reasoning.

- **Llama 4 Scout** (`meta-llama/llama-4-scout`) — Meta — Free on shapes.inc — ctx 500,000 — none — 34 ratings — added 2025-04-05 — legacy — shapes-picks: — — picker
  - A mixture-of-experts model optimized for strict persona adherence, visual reasoning, and structured data tasks.

- **Llama 3.1 8B Instruct** (`meta-llama/llama-3.1-8b-instruct`) — Meta — Free on shapes.inc — ctx 120,000 — none — 20 ratings — added 2024-07-23 — legacy — shapes-picks: — — picker
  - Fast, efficient, and capable of handling large context windows for everyday tasks.

- **Llama Guard 4 12B** (`meta-llama/llama-guard-4-12b`) — Meta — Free on shapes.inc — ctx 120,000 — none — 6 ratings — added 2025-04-30 — legacy — shapes-picks: — — picker
  - Specialized multimodal safety classifier for identifying content violations in text and images.

- **Llama 3.2 1B Instruct** (`meta-llama/llama-3.2-1b-instruct`) — Meta — Free on shapes.inc — ctx 30,000 — none — 4 ratings — added 2024-09-25 — legacy — shapes-picks: — — picker
  - Efficient, lightweight model optimized for fast performance in low-resource environments.

- **Llama 3.2 3B Instruct** (`meta-llama/llama-3.2-3b-instruct`) — Meta — Free on shapes.inc — ctx 120,000 — none — 2 ratings — added 2024-09-25 — legacy — shapes-picks: — — picker
  - Efficient, lightweight model optimized for fast text generation and multilingual dialogue.

### Microsoft

- **Phi 4** (`microsoft/phi-4`) — Microsoft — Free on shapes.inc — ctx 8,000 — none — 446 ratings — added 2025-01-10 — legacy — shapes-picks: — — picker
  - A reasoning-focused model designed for step-by-step problem solving and nuanced discussion.

- **WizardLM-2 8x22B** (`microsoft/wizardlm-2-8x22b`) — Microsoft — Premium · 0.32 cr/msg — ctx 30,000 — none — 5 ratings — added 2024-04-16 — legacy — shapes-picks: — — directory-only
  - A high-performance Mixture of Experts model built for complex reasoning and nuanced conversational tasks.

### MiniMax

- **MiniMax M1** (`minimax/minimax-m1`) — MiniMax — Premium · 0.32 cr/msg — ctx 500,000 — none — 16 ratings — added 2025-06-17 — legacy — shapes-picks: — — directory-only
  - A high-capacity reasoning engine built for complex multi-step tasks and massive context processing.

- **MiniMax-01** (`minimax/minimax-01`) — MiniMax — Premium · 0.12 cr/msg — ctx 500,000 — none — 1 ratings — added 2025-01-15 — legacy — shapes-picks: — — directory-only
  - A high-capacity multimodal model built for massive long-context analysis and complex reasoning.

### Mistral

- **Mistral Small 3.1 24B** (`mistralai/mistral-small-3.1-24b-instruct`) — Mistral — Premium · 0.19 cr/msg — ctx 120,000 — none — 17 ratings — added 2025-03-17 — legacy — shapes-picks: — — directory-only
  - Efficient, multimodal model optimized for reasoning, coding, and structured data tasks.

- **Mistral Small 3.2 24B** (`mistralai/mistral-small-3.2-24b-instruct`) — Mistral — Free on shapes.inc — ctx 200,000 — none — 15 ratings — added 2025-06-20 — legacy — shapes-picks: — — picker
  - A versatile 24B parameter model optimized for precise instruction following, coding, and multimodal reasoning.

- **Mistral Nemo** (`mistralai/mistral-nemo`) — Mistral — Free on shapes.inc — ctx 120,000 — none — 7 ratings — added 2024-07-19 — legacy — shapes-picks: — — picker
  - A multilingual, high-context model designed for efficient reasoning and structured data tasks.

- **Mistral Small 3** (`mistralai/mistral-small-24b-instruct-2501`) — Mistral — Free on shapes.inc — ctx 30,000 — none — 2 ratings — added 2025-01-30 — legacy — shapes-picks: — — picker
  - Efficient, low-latency model optimized for multilingual tasks and high-accuracy reasoning.

- **Saba** (`mistralai/mistral-saba`) — Mistral — Premium · 0.11 cr/msg — ctx 30,000 — none — 1 ratings — added 2025-02-17 — legacy — shapes-picks: — — directory-only
  - Specialized language model optimized for Arabic and South Asian linguistic accuracy.

- **Codestral 2508** (`mistralai/codestral-2508`) — Mistral — Premium · 0.17 cr/msg — ctx 200,000 — none — 0 ratings — added 2025-08-01 — legacy — shapes-picks: — — directory-only
  - Specialized coding assistant optimized for low-latency code generation, debugging, and test creation.

- **Codestral 2508 (batch)** (`mistralai/codestral-2508:batch`) — Mistral — Premium · 0.08 cr/msg — ctx 200,000 — none — 0 ratings — added 2025-08-01 — legacy — shapes-picks: — — directory-only
  - Specialized coding engine optimized for high-volume, asynchronous code analysis and generation tasks.

- **Mistral Medium 3** (`mistralai/mistral-medium-3`) — Mistral — Premium · 0.24 cr/msg — ctx 120,000 — none — 0 ratings — added 2025-05-07 — legacy — shapes-picks: — — directory-only
  - A high-performance model built for complex reasoning, coding, and multimodal analysis.

- **Mistral Medium 3.1** (`mistralai/mistral-medium-3.1`) — Mistral — Premium · 0.24 cr/msg — ctx 120,000 — Native Vision, Tools — 0 ratings — added 2025-08-13 — legacy — shapes-picks: — — directory-only
  - Enterprise-grade model optimized for complex coding, STEM reasoning, and structured data tasks.

- **Mistral Medium 3.1 (batch)** (`mistralai/mistral-medium-3.1:batch`) — Mistral — Premium · 0.12 cr/msg — ctx 120,000 — Unstable — 0 ratings — added 2025-08-13 — legacy, unstable — shapes-picks: — — directory-only
  - Enterprise-grade model optimized for high-volume, asynchronous coding and reasoning tasks.

- **Mixtral 8x22B Instruct** (`mistralai/mixtral-8x22b-instruct`) — Mistral — Premium · 1.12 cr/msg — ctx 30,000 — none — 0 ratings — added 2024-04-17 — legacy — shapes-picks: — — directory-only
  - A high-capacity mixture-of-experts model built for complex reasoning, coding, and long-form document analysis.

### Mistralai

- **Mistral Large** (`mistralai/mistral-large`) — Mistralai — Premium · 1.12 cr/msg — ctx 120,000 — none — 0 ratings — added 2024-02-26 — legacy — shapes-picks: — — directory-only
  - A high-performance engine for complex reasoning, multilingual tasks, and large-scale document analysis.

- **Mistral Large 2407** (`mistralai/mistral-large-2407`) — Mistralai — Premium · 1.12 cr/msg — ctx 120,000 — none — 0 ratings — added 2024-11-19 — legacy — shapes-picks: — — directory-only
  - A high-reasoning model optimized for complex coding tasks, multi-language support, and large document analysis.

### MoonshotAI

- **Kimi K2 0905** (`moonshotai/kimi-k2-0905`) — MoonshotAI — Premium · 0.35 cr/msg — ctx 200,000 — Tools — 162 ratings — added 2025-09-04 — legacy — shapes-picks: — — directory-only
  - A high-capacity reasoning engine optimized for complex coding and large-scale document analysis.

- **Kimi K2 0711** (`moonshotai/kimi-k2`) — MoonshotAI — Premium · 0.33 cr/msg — ctx 120,000 — none — 6 ratings — added 2025-07-11 — legacy — shapes-picks: — — directory-only
  - A high-performance text-to-text model built for rapid reasoning, complex coding, and large-scale document analysis.

### Morph

- **Morph V3 Fast** (`morph/morph-v3-fast`) — Morph — Premium · 0.42 cr/msg — ctx 30,000 — none — 0 ratings — added 2025-07-07 — legacy — shapes-picks: — — directory-only
  - High-speed, specialized engine optimized for rapid code transformations and technical refactoring.

- **Morph V3 Large** (`morph/morph-v3-large`) — Morph — Premium · 0.49 cr/msg — ctx 200,000 — none — 0 ratings — added 2025-07-07 — legacy — shapes-picks: — — directory-only
  - Specialized engine for high-accuracy code transformations and large-scale codebase edits.

### Nous

- **Hermes 3 70B Instruct** (`nousresearch/hermes-3-llama-3.1-70b`) — Nous — Premium · 0.36 cr/msg — ctx 120,000 — none — 74 ratings — added 2024-08-18 — legacy — shapes-picks: — — directory-only
  - A highly steerable generalist model that excels at creative writing, complex reasoning, and multi-turn conversation.

- **Hermes 4 405B** (`nousresearch/hermes-4-405b`) — Nous — Premium · 0.56 cr/msg — ctx 120,000 — Reasoning — 10 ratings — added 2025-08-26 — legacy — shapes-picks: — — directory-only
  - A massive, highly steerable reasoning model with a flexible hybrid thought process.

- **Hermes 3 405B Instruct** (`nousresearch/hermes-3-llama-3.1-405b`) — Nous — Premium · 0.52 cr/msg — ctx 120,000 — none — 1 ratings — added 2024-08-16 — legacy — shapes-picks: — — directory-only
  - A highly steerable, large-scale model optimized for complex multi-turn conversations and structured data tasks.

### OpenAI

- **GPT-4o-mini** (`openai/gpt-4o-mini`) — OpenAI — Premium · 0.09 cr/msg — ctx 120,000 — none — 753 ratings — added 2024-07-18 — legacy — shapes-picks: — — directory-only
  - A high-intelligence, low-latency engine optimized for rapid responses and structured data tasks.

- **GPT-5 Nano** (`openai/gpt-5-nano`) — OpenAI — Free on shapes.inc — ctx 200,000 — Reasoning, Native Vision, Tools, efforts:low/medium/high, reasoning-required — 282 ratings — added 2025-08-07 — legacy — shapes-picks: — — picker
  - A high-speed, lightweight engine optimized for structured data and rapid developer tasks.

- **GPT-4.1 Nano** (`openai/gpt-4.1-nano`) — OpenAI — Free on shapes.inc — ctx 500,000 — none — 217 ratings — added 2025-04-14 — legacy — shapes-picks: — — picker
  - A high-speed, cost-effective engine optimized for rapid data extraction and large-scale classification tasks.

- **GPT-3.5 Turbo** (`openai/gpt-3.5-turbo`) — OpenAI — Premium · 0.28 cr/msg — ctx 8,000 — none — 10 ratings — added 2023-05-28 — legacy — shapes-picks: — — directory-only
  - A reliable, cost-effective choice for standard chat and structured text tasks.

- **gpt-oss-120b** (`openai/gpt-oss-120b`) — OpenAI — Free on shapes.inc — ctx 120,000 — Reasoning, Tools, efforts:low/medium/high, reasoning-required — 5 ratings — added 2025-08-05 — legacy — shapes-picks: — — picker
  - A high-performance open-weight model featuring configurable reasoning depth and a massive 131k context window.

- **GPT-4o (2024-05-13)** (`openai/gpt-4o-2024-05-13`) — OpenAI — Premium · 2.8 cr/msg — ctx 120,000 — none — 4 ratings — added 2024-05-13 — legacy — shapes-picks: — — directory-only
  - High-speed multimodal engine optimized for complex reasoning and multilingual text processing.

- **GPT-4.1** (`openai/gpt-4.1`) — OpenAI — Premium · 1.16 cr/msg — ctx 500,000 — none — 3 ratings — added 2025-04-14 — legacy — shapes-picks: — — directory-only
  - A high-recall model built for complex software engineering and deep reasoning over massive documents.

- **GPT-4** (`openai/gpt-4`) — OpenAI — Premium · 16.2 cr/msg — ctx 8,000 — none — 1 ratings — added 2023-05-28 — legacy — shapes-picks: — — directory-only
  - Reliable logic and complex problem-solving with a proven track record.

- **GPT-4o (2024-11-20)** (`openai/gpt-4o-2024-11-20`) — OpenAI — Premium · 1.45 cr/msg — ctx 120,000 — none — 1 ratings — added 2024-11-20 — legacy — shapes-picks: — — directory-only
  - A balanced, high-performance engine for complex reasoning, creative writing, and file-based analysis.

- **GPT-4o-mini (2024-07-18)** (`openai/gpt-4o-mini-2024-07-18`) — OpenAI — Premium · 0.09 cr/msg — ctx 120,000 — none — 1 ratings — added 2024-07-18 — legacy — shapes-picks: — — directory-only
  - A high-throughput, cost-efficient engine optimized for structured outputs and large document processing.

- **GPT-3.5 Turbo (batch)** (`openai/gpt-3.5-turbo:batch`) — OpenAI — Premium · 0.14 cr/msg — ctx 8,000 — none — 0 ratings — added 2023-05-28 — legacy — shapes-picks: — — directory-only
  - Cost-effective, asynchronous processing for high-volume data tasks and structured outputs.

- **GPT-3.5 Turbo (older v0613)** (`openai/gpt-3.5-turbo-0613`) — OpenAI — Premium · 0.54 cr/msg — ctx 8,000 — none — 0 ratings — added 2024-01-25 — legacy — shapes-picks: — — directory-only
  - Fast, legacy model optimized for simple chat and structured data tasks.

- **GPT-3.5 Turbo 16k** (`openai/gpt-3.5-turbo-16k`) — OpenAI — Premium · 1.58 cr/msg — ctx 8,000 — none — 0 ratings — added 2023-08-28 — legacy — shapes-picks: — — directory-only
  - A high-context, cost-effective model for processing longer documents and extended text sequences.

- **GPT-3.5 Turbo Instruct** (`openai/gpt-3.5-turbo-instruct`) — OpenAI — Premium · 0.79 cr/msg — ctx 8,000 — none — 0 ratings — added 2023-09-28 — legacy — shapes-picks: — — directory-only
  - Direct, instruction-following text completion optimized for structured tasks.

- **GPT-4 Turbo** (`openai/gpt-4-turbo`) — OpenAI — Premium · 5.6 cr/msg — ctx 120,000 — none — 0 ratings — added 2024-04-09 — legacy — shapes-picks: — — directory-only
  - A reliable, high-capacity model for complex reasoning, coding, and large-scale document analysis.

- **GPT-4 Turbo (batch)** (`openai/gpt-4-turbo:batch`) — OpenAI — Premium · 2.8 cr/msg — ctx 120,000 — none — 0 ratings — added 2024-04-09 — legacy — shapes-picks: — — directory-only
  - High-throughput, asynchronous processing for large-scale data analysis and complex reasoning tasks.

- **GPT-4.1 (batch)** (`openai/gpt-4.1:batch`) — OpenAI — Premium · 0.58 cr/msg — ctx 500,000 — none — 0 ratings — added 2025-04-14 — legacy — shapes-picks: — — directory-only
  - High-capacity asynchronous processing for complex reasoning and massive document analysis.

- **GPT-4.1 Mini** (`openai/gpt-4.1-mini`) — OpenAI — Premium · 0.23 cr/msg — ctx 500,000 — none — 0 ratings — added 2025-04-14 — legacy — shapes-picks: — — directory-only
  - High-efficiency model optimized for rapid coding, vision analysis, and massive context processing.

- **GPT-4.1 Mini (batch)** (`openai/gpt-4.1-mini:batch`) — OpenAI — Premium · 0.12 cr/msg — ctx 500,000 — none — 0 ratings — added 2025-04-14 — legacy — shapes-picks: — — directory-only
  - Efficient, high-volume processing for large-scale coding, vision, and structured data tasks.

- **GPT-4.1 Nano (batch)** (`openai/gpt-4.1-nano:batch`) — OpenAI — Free on shapes.inc — ctx 500,000 — none — 0 ratings — added 2025-04-14 — legacy — shapes-picks: — — picker
  - High-throughput, cost-efficient engine for large-scale asynchronous data processing and document analysis.

- **GPT-4o** (`openai/gpt-4o`) — OpenAI — Premium · 1.45 cr/msg — ctx 120,000 — none — 0 ratings — added 2024-05-13 — legacy — shapes-picks: — — directory-only
  - A high-speed, multimodal model balanced for complex reasoning, coding, and visual analysis.

- **GPT-4o (2024-08-06)** (`openai/gpt-4o-2024-08-06`) — OpenAI — Premium · 1.45 cr/msg — ctx 120,000 — none — 0 ratings — added 2024-08-06 — legacy — shapes-picks: — — directory-only
  - Reliable, high-performance model optimized for structured data and complex multimodal tasks.

- **GPT-4o (batch)** (`openai/gpt-4o:batch`) — OpenAI — Premium · 0.73 cr/msg — ctx 120,000 — none — 0 ratings — added 2024-05-13 — legacy — shapes-picks: — — directory-only
  - High-volume, cost-effective asynchronous processing for complex reasoning and large-scale data tasks.

- **GPT-4o-mini (batch)** (`openai/gpt-4o-mini:batch`) — OpenAI — Free on shapes.inc — ctx 120,000 — none — 0 ratings — added 2024-07-18 — legacy — shapes-picks: — — picker
  - Cost-effective, high-volume asynchronous processing for structured tasks and complex analysis.

- **GPT-5** (`openai/gpt-5`) — OpenAI — Premium · 0.83 cr/msg — ctx 200,000 — Reasoning, Native Vision, Tools, efforts:low/medium/high, reasoning-required — 0 ratings — added 2025-08-07 — legacy — shapes-picks: — — directory-only
  - Advanced reasoning engine optimized for complex, multi-step tasks and large-scale data analysis.

- **GPT-5 (batch)** (`openai/gpt-5:batch`) — OpenAI — Premium · 0.41 cr/msg — ctx 200,000 — Reasoning, Unstable, reasoning-required — 0 ratings — added 2025-08-07 — legacy, unstable — shapes-picks: — — directory-only
  - High-accuracy reasoning and data analysis for large-scale, asynchronous workloads.

- **GPT-5 Mini** (`openai/gpt-5-mini`) — OpenAI — Premium · 0.17 cr/msg — ctx 200,000 — Reasoning, Native Vision, Tools, efforts:low/medium/high, reasoning-required — 0 ratings — added 2025-08-07 — legacy — shapes-picks: — — directory-only
  - Efficient, high-speed reasoning and coding assistant with a massive 400,000-token context window.

- **GPT-5 Mini (batch)** (`openai/gpt-5-mini:batch`) — OpenAI — Premium · 0.08 cr/msg — ctx 200,000 — Reasoning, Unstable, reasoning-required — 0 ratings — added 2025-08-07 — legacy, unstable — shapes-picks: — — directory-only
  - High-efficiency reasoning and data analysis optimized for large-scale, asynchronous batch processing.

- **GPT-5 Nano (batch)** (`openai/gpt-5-nano:batch`) — OpenAI — Free on shapes.inc — ctx 200,000 — Reasoning, Unstable, reasoning-required — 0 ratings — added 2025-08-07 — legacy, unstable — shapes-picks: — — picker
  - A high-efficiency, large-context engine built for asynchronous batch processing and structured data tasks.

- **gpt-oss-120b (batch)** (`openai/gpt-oss-120b:batch`) — OpenAI — Free on shapes.inc — ctx 120,000 — Reasoning, reasoning-required — 0 ratings — added 2025-08-05 — legacy — shapes-picks: — — picker
  - High-reasoning, asynchronous model optimized for complex agentic workflows and large-scale data processing.

- **gpt-oss-20b** (`openai/gpt-oss-20b`) — OpenAI — Free on shapes.inc — ctx 120,000 — Reasoning, reasoning-required — 0 ratings — added 2025-08-05 — legacy — shapes-picks: — — picker
  - Efficient mixture-of-experts model designed for high-context tasks and reliable tool use.

- **gpt-oss-20b (batch)** (`openai/gpt-oss-20b:batch`) — OpenAI — Free on shapes.inc — ctx 120,000 — Reasoning, reasoning-required — 0 ratings — added 2025-08-05 — legacy — shapes-picks: — — picker
  - Efficient, large-context model optimized for asynchronous data processing and structured analysis.

- **o1** (`openai/o1`) — OpenAI — Premium · 8.7 cr/msg — ctx 200,000 — none — 0 ratings — added 2024-12-17 — legacy — shapes-picks: — — directory-only
  - Advanced reasoning model optimized for complex STEM, coding, and analytical problem-solving.

- **o1-pro** (`openai/o1-pro`) — OpenAI — Premium · 87 cr/msg — ctx 200,000 — none — 0 ratings — added 2025-03-19 — legacy — shapes-picks: — — directory-only
  - Specialized for deep, multi-step reasoning tasks that require extensive internal deliberation.

- **o3** (`openai/o3`) — OpenAI — Premium · 1.16 cr/msg — ctx 200,000 — none — 0 ratings — added 2025-04-16 — legacy — shapes-picks: — — directory-only
  - Specialized reasoning engine for complex multi-step analysis, coding, and scientific problem-solving.

- **o3 (batch)** (`openai/o3:batch`) — OpenAI — Premium · 0.58 cr/msg — ctx 200,000 — none — 0 ratings — added 2025-04-16 — legacy — shapes-picks: — — directory-only
  - High-capacity reasoning engine optimized for complex, asynchronous data processing and technical tasks.

- **o3 Mini** (`openai/o3-mini`) — OpenAI — Premium · 0.64 cr/msg — ctx 200,000 — none — 0 ratings — added 2025-01-31 — legacy — shapes-picks: — — directory-only
  - A specialized reasoning engine optimized for complex STEM, coding, and mathematical problem-solving.

- **o3 Mini (batch)** (`openai/o3-mini:batch`) — OpenAI — Premium · 0.32 cr/msg — ctx 200,000 — none — 0 ratings — added 2025-01-31 — legacy — shapes-picks: — — directory-only
  - Cost-efficient reasoning engine optimized for high-volume, asynchronous STEM and coding tasks.

- **o3 Mini High** (`openai/o3-mini-high`) — OpenAI — Premium · 0.64 cr/msg — ctx 200,000 — Reasoning, reasoning-required — 0 ratings — added 2025-02-12 — legacy — shapes-picks: — — directory-only
  - A specialized reasoning engine optimized for complex coding, mathematics, and technical problem-solving.

- **o3 Pro** (`openai/o3-pro`) — OpenAI — Premium · 11.6 cr/msg — ctx 200,000 — none — 0 ratings — added 2025-06-10 — legacy — shapes-picks: — — directory-only
  - Advanced reasoning engine that prioritizes deep analysis and multi-step problem solving.

- **o4 Mini** (`openai/o4-mini`) — OpenAI — Premium · 0.64 cr/msg — ctx 200,000 — none — 0 ratings — added 2025-04-16 — legacy — shapes-picks: — — directory-only
  - Efficient reasoning model optimized for complex STEM tasks, coding, and structured data analysis.

- **o4 Mini (batch)** (`openai/o4-mini:batch`) — OpenAI — Premium · 0.32 cr/msg — ctx 200,000 — none — 0 ratings — added 2025-04-16 — legacy — shapes-picks: — — directory-only
  - High-throughput reasoning engine optimized for complex coding, STEM analysis, and asynchronous batch processing.

- **o4 Mini High** (`openai/o4-mini-high`) — OpenAI — Premium · 0.64 cr/msg — ctx 200,000 — Reasoning, reasoning-required — 0 ratings — added 2025-04-16 — legacy — shapes-picks: — — directory-only
  - A specialized reasoning model optimized for complex STEM tasks, coding, and multi-step problem solving.

### Perplexity

- **Sonar Reasoning Pro** (`perplexity/sonar-reasoning-pro`) — Perplexity — Premium · 1.16 cr/msg — ctx 120,000 — none — 1 ratings — added 2025-03-07 — legacy — shapes-picks: — — directory-only
  - Advanced reasoning model built for complex, multi-step analysis and information retrieval.

- **Sonar** (`perplexity/sonar`) — Perplexity — Premium · 0.52 cr/msg — ctx 120,000 — none — 0 ratings — added 2025-01-27 — legacy — shapes-picks: — — directory-only
  - Fast, cost-effective model optimized for real-time information retrieval and cited answers.

- **Sonar Deep Research** (`perplexity/sonar-deep-research`) — Perplexity — Premium · 1.16 cr/msg — ctx 120,000 — none — 0 ratings — added 2025-03-07 — legacy — shapes-picks: — — directory-only
  - Autonomous research agent for multi-step information gathering and complex synthesis.

- **Sonar Pro** (`perplexity/sonar-pro`) — Perplexity — Premium · 1.8 cr/msg — ctx 200,000 — none — 0 ratings — added 2025-03-07 — legacy — shapes-picks: — — directory-only
  - High-density research engine optimized for complex, multi-step information retrieval.

### Qwen

- **Qwen2.5 72B Instruct** (`qwen/qwen-2.5-72b-instruct`) — Qwen — Premium · 0.19 cr/msg — ctx 30,000 — none — 28 ratings — added 2024-09-19 — legacy — shapes-picks: — — directory-only
  - A high-performance model for coding, structured data, and complex instruction following.

- **Qwen3 235B A22B Instruct 2507** (`qwen/qwen3-235b-a22b-2507`) — Qwen — Premium · 0.06 cr/msg — ctx 200,000 — none — 9 ratings — added 2025-07-21 — legacy — shapes-picks: — — directory-only
  - A high-capacity mixture-of-experts model built for complex reasoning, coding, and large-scale document analysis.

- **Qwen3 Coder 30B A3B Instruct** (`qwen/qwen3-coder-30b-a3b-instruct`) — Qwen — Free on shapes.inc — ctx 200,000 — none — 5 ratings — added 2025-07-31 — legacy — shapes-picks: — — picker
  - Specialized Mixture-of-Experts model for high-efficiency coding, repository-scale analysis, and structured function calling.

- **Qwen-Plus** (`qwen/qwen-plus`) — Qwen — Premium · 0.15 cr/msg — ctx 500,000 — none — 4 ratings — added 2025-02-01 — legacy — shapes-picks: — — directory-only
  - A high-performance text-only engine optimized for massive context windows and complex analytical tasks.

- **Qwen3 32B** (`qwen/qwen3-32b`) — Qwen — Free on shapes.inc — ctx 120,000 — none — 2 ratings — added 2025-04-28 — legacy — shapes-picks: — — picker
  - A flexible model featuring dedicated reasoning and standard modes for complex logic, coding, and general conversation.

- **Qwen3 VL 235B A22B Instruct** (`qwen/qwen3-vl-235b-a22b-instruct`) — Qwen — Premium · 0.14 cr/msg — ctx 200,000 — Native Vision, Tools — 2 ratings — added 2025-09-23 — legacy — shapes-picks: — — directory-only
  - Advanced multimodal model for complex visual analysis, document extraction, and high-performance text reasoning.

- **Qwen2.5 VL 72B Instruct** (`qwen/qwen2.5-vl-72b-instruct`) — Qwen — Premium · 0.42 cr/msg — ctx 120,000 — none — 1 ratings — added 2025-02-01 — legacy — shapes-picks: — — directory-only
  - A high-fidelity multimodal model for complex visual analysis, document extraction, and technical diagram interpretation.

- **Qwen3 14B** (`qwen/qwen3-14b`) — Qwen — Free on shapes.inc — ctx 120,000 — none — 1 ratings — added 2025-04-28 — legacy — shapes-picks: — — picker
  - Versatile language model with a toggleable thinking mode for complex logic and creative tasks.

- **Qwen3 30B A3B** (`qwen/qwen3-30b-a3b`) — Qwen — Premium · 0.07 cr/msg — ctx 120,000 — none — 1 ratings — added 2025-04-28 — legacy — shapes-picks: — — directory-only
  - Efficient mixture-of-experts model with toggleable reasoning modes for complex tasks.

- **Qwen3 30B A3B Instruct 2507** (`qwen/qwen3-30b-a3b-instruct-2507`) — Qwen — Free on shapes.inc — ctx 200,000 — none — 1 ratings — added 2025-07-29 — legacy — shapes-picks: — — picker
  - Efficient mixture-of-experts model optimized for fast instruction following and complex coding tasks.

- **Qwen3 8B** (`qwen/qwen3-8b`) — Qwen — Premium · 0.07 cr/msg — ctx 120,000 — none — 1 ratings — added 2025-04-28 — legacy — shapes-picks: — — directory-only
  - A dual-mode model featuring specialized reasoning for logic and coding alongside efficient general conversation.

- **Qwen Plus 0728** (`qwen/qwen-plus-2025-07-28`) — Qwen — Premium · 0.15 cr/msg — ctx 500,000 — Tools — 0 ratings — added 2025-09-08 — legacy — shapes-picks: — — directory-only
  - A balanced, high-capacity reasoning engine designed for large-scale text analysis and structured data tasks.

- **Qwen2.5 7B Instruct** (`qwen/qwen-2.5-7b-instruct`) — Qwen — Free on shapes.inc — ctx 30,000 — none — 0 ratings — added 2024-10-16 — legacy — shapes-picks: — — picker
  - Efficient, instruction-tuned model with strong coding, math, and structured output capabilities.

- **Qwen2.5 Coder 32B Instruct** (`qwen/qwen-2.5-coder-32b-instruct`) — Qwen — Premium · 0.35 cr/msg — ctx 30,000 — none — 0 ratings — added 2024-11-11 — legacy — shapes-picks: — — directory-only
  - Specialized model for high-accuracy code generation, debugging, and technical reasoning.

- **Qwen3 235B A22B** (`qwen/qwen3-235b-a22b`) — Qwen — Premium · 0.26 cr/msg — ctx 120,000 — none — 0 ratings — added 2025-04-28 — legacy — shapes-picks: — — directory-only
  - Flexible mixture-of-experts model with dedicated modes for deep reasoning and efficient conversation.

- **Qwen3 235B A22B Thinking 2507** (`qwen/qwen3-235b-a22b-thinking-2507`) — Qwen — Premium · 0.16 cr/msg — ctx 120,000 — Reasoning, reasoning-required — 0 ratings — added 2025-07-25 — legacy — shapes-picks: — — directory-only
  - A specialized reasoning engine that forces a deep-thought process for complex logic and technical tasks.

- **Qwen3 30B A3B Thinking 2507** (`qwen/qwen3-30b-a3b-thinking-2507`) — Qwen — Premium · 0.15 cr/msg — ctx 30,000 — Reasoning, Tools, reasoning-required — 0 ratings — added 2025-08-28 — legacy — shapes-picks: — — directory-only
  - Specialized reasoning model that generates detailed internal thought processes for complex problem-solving.

- **Qwen3 Coder 480B A35B** (`qwen/qwen3-coder`) — Qwen — Premium · 0.17 cr/msg — ctx 200,000 — none — 0 ratings — added 2025-07-23 — legacy — shapes-picks: — — directory-only
  - Specialized Mixture-of-Experts model engineered for complex software development and large-scale repository analysis.

- **Qwen3 Coder Flash** (`qwen/qwen3-coder-flash`) — Qwen — Premium · 0.12 cr/msg — ctx 500,000 — Tools — 0 ratings — added 2025-09-17 — legacy — shapes-picks: — — directory-only
  - A high-speed, cost-efficient engine optimized for autonomous programming and large-scale codebase analysis.

- **Qwen3 Coder Plus** (`qwen/qwen3-coder-plus`) — Qwen — Premium · 0.39 cr/msg — ctx 500,000 — Tools — 0 ratings — added 2025-09-23 — legacy — shapes-picks: — — directory-only
  - Specialized for complex programming tasks, agentic workflows, and large-scale code analysis.

- **Qwen3 Max** (`qwen/qwen3-max`) — Qwen — Premium · 0.47 cr/msg — ctx 200,000 — Tools — 0 ratings — added 2025-09-23 — legacy — shapes-picks: — — directory-only
  - High-capacity text engine optimized for complex reasoning, tool-calling, and large-scale data retrieval.

- **Qwen3 Next 80B A3B Instruct** (`qwen/qwen3-next-80b-a3b-instruct`) — Qwen — Premium · 0.07 cr/msg — ctx 200,000 — Tools, Unstable — 0 ratings — added 2025-09-11 — legacy, unstable — shapes-picks: — — directory-only
  - High-throughput instruction model built for stable, long-context tasks and efficient coding.

- **Qwen3 Next 80B A3B Thinking** (`qwen/qwen3-next-80b-a3b-thinking`) — Qwen — Premium · 0.1 cr/msg — ctx 200,000 — Reasoning, Tools, reasoning-required — 0 ratings — added 2025-09-11 — legacy — shapes-picks: — — directory-only
  - A reasoning-first model that provides structured thinking traces to solve complex math, coding, and logical problems.

- **Qwen3 VL 235B A22B Thinking** (`qwen/qwen3-vl-235b-a22b-thinking`) — Qwen — Premium · 0.28 cr/msg — ctx 120,000 — Reasoning, Native Vision, Tools, reasoning-required — 0 ratings — added 2025-09-23 — legacy — shapes-picks: — — directory-only
  - Multimodal reasoning engine optimized for complex STEM analysis, visual coding, and agentic tool use.

### Rekaai

- **Reka Flash 3** (`rekaai/reka-flash-3`) — Rekaai — Free on shapes.inc — ctx 30,000 — Reasoning, reasoning-required — 1 ratings — added 2025-03-12 — legacy — shapes-picks: — — picker
  - Efficient, low-latency model optimized for fast English-language reasoning and structured text generation.

### Relace

- **Relace Apply 3** (`relace/relace-apply-3`) — Relace — Premium · 0.45 cr/msg — ctx 200,000 — Unstable — 0 ratings — added 2025-09-26 — legacy, unstable — shapes-picks: — — directory-only
  - Specialized engine for merging AI-generated code edits directly into source files.

### Sao10K

- **Llama 3 8B Lunaris** (`sao10k/l3-lunaris-8b`) — Sao10K — Free on shapes.inc — ctx 8,000 — none — 1,258 ratings — added 2024-08-13 — legacy — shapes-picks: — — picker
  - A lightweight, expressive engine optimized for creative roleplay and fast, character-driven dialogue.

- **Llama 3.3 Euryale 70B** (`sao10k/l3.3-euryale-70b`) — Sao10K — Premium · 0.34 cr/msg — ctx 120,000 — none — 15 ratings — added 2024-12-18 — legacy — shapes-picks: — — directory-only
  - Specialized for immersive, character-driven storytelling and long-form creative roleplay.

- **Llama 3.1 Euryale 70B v2.2** (`sao10k/l3.1-euryale-70b`) — Sao10K — Premium · 0.44 cr/msg — ctx 120,000 — none — 0 ratings — added 2024-08-28 — legacy — shapes-picks: — — directory-only
  - Specialized for immersive creative writing and nuanced roleplay with improved multi-turn coherence.

### Tencent

- **Hunyuan A13B Instruct** (`tencent/hunyuan-a13b-instruct`) — Tencent — Premium · 0.08 cr/msg — ctx 120,000 — none — 0 ratings — added 2025-07-08 — legacy — shapes-picks: — — directory-only
  - Efficient reasoning and analytical performance with a large context window.

### TheDrummer

- **Cydonia 24B V4.1** (`thedrummer/cydonia-24b-v4.1`) — TheDrummer — Premium · 0.16 cr/msg — ctx 120,000 — Unstable — 51 ratings — added 2025-09-27 — legacy, unstable — shapes-picks: — — directory-only
  - Uncensored creative writing and roleplay model built for high prompt adherence.

- **UnslopNemo 12B** (`thedrummer/unslopnemo-12b`) — TheDrummer — Premium · 0.21 cr/msg — ctx 500,000 — none — 12 ratings — added 2024-11-08 — legacy — shapes-picks: — — directory-only
  - Optimized for creative storytelling and role-play with high-speed inference.

- **Skyfall 36B V2** (`thedrummer/skyfall-36b-v2`) — TheDrummer — Premium · 0.29 cr/msg — ctx 30,000 — none — 2 ratings — added 2025-03-10 — legacy — shapes-picks: — — directory-only
  - Specialized for creative writing and nuanced roleplay with a 32k context window.

### Undi95

- **ReMM SLERP 13B** (`undi95/remm-slerp-l2-13b`) — Undi95 — Premium · 0.19 cr/msg — ctx 8,000 — none — 21 ratings — added 2023-07-22 — legacy — shapes-picks: — — directory-only
  - A community-favorite Llama 2 merge optimized for creative writing and roleplay.

### Venice

- **Uncensored** (`cognitivecomputations/dolphin-mistral-24b-venice-edition`) — Venice — Premium · 0.12 cr/msg — ctx 120,000 — none — 12 ratings — added 2025-07-09 — legacy — shapes-picks: — — directory-only
  - Highly steerable, uncensored model with a massive 128k context window for extended creative tasks.

### Z.ai

- **GLM 4.6** (`z-ai/glm-4.6`) — Z.ai — Premium · 0.25 cr/msg — ctx 200,000 — Reasoning, Tools — 15 ratings — added 2025-09-30 — legacy — shapes-picks: — — directory-only
  - A high-capacity model optimized for complex coding, agentic tool use, and long-context reasoning.

- **GLM 4.5 Air** (`z-ai/glm-4.5-air`) — Z.ai — Premium · 0.08 cr/msg — ctx 120,000 — none — 6 ratings — added 2025-07-25 — legacy — shapes-picks: — — directory-only
  - Efficient agent-centric model optimized for complex reasoning and tool-use tasks.

- **GLM 4.5** (`z-ai/glm-4.5`) — Z.ai — Premium · 0.34 cr/msg — ctx 120,000 — none — 0 ratings — added 2025-07-25 — legacy — shapes-picks: — — directory-only
  - High-performance foundation model optimized for complex reasoning and agentic workflows.

- **GLM 4.5V** (`z-ai/glm-4.5v`) — Z.ai — Premium · 0.34 cr/msg — ctx 30,000 — Reasoning, Native Vision, Tools — 0 ratings — added 2025-08-11 — legacy — shapes-picks: — — directory-only
  - Multimodal model with precise visual grounding and a toggleable deep reasoning mode.

## Flat index

One line per engine for search. Same 431 ids.

| id | name | provider | tier | cr/msg | ctx | tools | vision | reasoning | unstable | ratings | bucket | picks | picker |
| --- | --- | --- | --- | ---: | ---: | --- | --- | --- | --- | ---: | --- | --- | --- |
| `aion-labs/aion-3.5` | Aion 3.5 | AionLabs | premium | 1.62 | 200000 | no | no | yes | no | 3 | active | roleplay | no |
| `aion-labs/aion-3.5-mini` | Aion 3.5 Mini | AionLabs | premium | 0.38 | 200000 | yes | no | yes | no | 3 | active | roleplay | no |
| `aion-labs/aion-2.0` | Aion-2.0 | AionLabs | premium | 0.43 | 120000 | no | no | yes | no | 86 | active | roleplay | no |
| `aion-labs/aion-3.0` | Aion-3.0 | AionLabs | premium | 1.62 | 120000 | yes | no | yes | no | 25 | active | roleplay | no |
| `aion-labs/aion-3.0-mini` | Aion-3.0-Mini | AionLabs | premium | 0.38 | 120000 | yes | no | yes | no | 43 | active | roleplay | no |
| `amazon/nova-2-lite-v1` | Nova 2 Lite | Amazon | premium | 0.2 | 500000 | yes | yes | no | no | 0 | active |  | no |
| `amazon/nova-premier-v1` | Nova Premier 1.0 | Amazon | premium | 1.5 | 500000 | no | no | no | yes | 0 | active |  | no |
| `anthropic/claude-fable-5` | Claude Fable 5 | Anthropic | premium | 6 | 500000 | yes | yes | yes | no | 4 | active |  | no |
| `anthropic/claude-fable-5:batch` | Claude Fable 5 (batch) | Anthropic | premium | 3 | 500000 | no | no | yes | yes | 0 | active |  | no |
| `anthropic/claude-fable-5.1` | Claude Fable 5.1 | Anthropic | premium | 6 | 500000 | yes | yes | yes | no | 2 | active |  | no |
| `anthropic/claude-fable-5.1:batch` | Claude Fable 5.1 (batch) | Anthropic | premium | 3 | 500000 | no | no | yes | yes | 0 | active |  | no |
| `~anthropic/claude-fable-latest` | Claude Fable Latest | Anthropic | premium | 6 | 500000 | yes | yes | yes | no | 0 | active |  | no |
| `anthropic/claude-haiku-4.5` | Claude Haiku 4.5 | Anthropic | premium | 0.6 | 200000 | yes | yes | no | no | 5 | active |  | no |
| `anthropic/claude-haiku-4.5:batch` | Claude Haiku 4.5 (batch) | Anthropic | premium | 0.3 | 200000 | no | no | no | yes | 0 | active |  | no |
| `~anthropic/claude-haiku-latest` | Claude Haiku Latest | Anthropic | premium | 0.6 | 200000 | yes | yes | no | no | 0 | active |  | no |
| `anthropic/claude-opus-4.5` | Claude Opus 4.5 | Anthropic | premium | 3 | 200000 | yes | yes | yes | no | 0 | active |  | no |
| `anthropic/claude-opus-4.5:batch` | Claude Opus 4.5 (batch) | Anthropic | premium | 1.5 | 200000 | no | no | no | yes | 0 | active |  | no |
| `anthropic/claude-opus-4.6` | Claude Opus 4.6 | Anthropic | premium | 3 | 500000 | yes | yes | yes | no | 91 | active |  | no |
| `anthropic/claude-opus-4.6:batch` | Claude Opus 4.6 (batch) | Anthropic | premium | 1.5 | 500000 | no | no | no | yes | 0 | active |  | no |
| `anthropic/claude-opus-4.7` | Claude Opus 4.7 | Anthropic | premium | 3 | 500000 | yes | yes | no | no | 53 | active |  | no |
| `anthropic/claude-opus-4.7:batch` | Claude Opus 4.7 (batch) | Anthropic | premium | 1.5 | 500000 | no | no | no | yes | 0 | active |  | no |
| `anthropic/claude-opus-4.8` | Claude Opus 4.8 | Anthropic | premium | 3 | 500000 | yes | yes | yes | no | 253 | active | intelligent | no |
| `anthropic/claude-opus-4.8:batch` | Claude Opus 4.8 (batch) | Anthropic | premium | 1.5 | 500000 | no | no | no | yes | 0 | active |  | no |
| `anthropic/claude-opus-5` | Claude Opus 5 | Anthropic | premium | 3 | 500000 | yes | yes | no | no | 13 | active |  | no |
| `anthropic/claude-opus-5:batch` | Claude Opus 5 (batch) | Anthropic | premium | 1.5 | 500000 | no | no | no | yes | 0 | active |  | no |
| `anthropic/claude-opus-5.5` | Claude Opus 5.5 | Anthropic | premium | 2.4 | 500000 | yes | yes | yes | no | 2 | active | intelligent | no |
| `anthropic/claude-opus-5.5:batch` | Claude Opus 5.5 (batch) | Anthropic | premium | 1.2 | 500000 | no | no | yes | yes | 0 | active |  | no |
| `~anthropic/claude-opus-latest` | Claude Opus Latest | Anthropic | premium | 2.4 | 500000 | yes | yes | yes | no | 0 | active |  | no |
| `anthropic/claude-sonnet-4.6` | Claude Sonnet 4.6 | Anthropic | premium | 1.8 | 500000 | yes | yes | yes | no | 3439 | active |  | no |
| `anthropic/claude-sonnet-4.6:batch` | Claude Sonnet 4.6 (batch) | Anthropic | premium | 0.9 | 500000 | no | no | no | yes | 0 | active |  | no |
| `anthropic/claude-sonnet-5` | Claude Sonnet 5 | Anthropic | premium | 1.2 | 500000 | yes | yes | no | no | 14 | active |  | no |
| `anthropic/claude-sonnet-5:batch` | Claude Sonnet 5 (batch) | Anthropic | premium | 0.6 | 500000 | no | no | no | yes | 0 | active |  | no |
| `anthropic/claude-sonnet-5.5` | Claude Sonnet 5.5 | Anthropic | premium | 1.2 | 500000 | yes | yes | yes | no | 1 | active | recommended, intelligent, roleplay | no |
| `anthropic/claude-sonnet-5.5:batch` | Claude Sonnet 5.5 (batch) | Anthropic | premium | 0.6 | 500000 | no | no | yes | yes | 0 | active |  | no |
| `~anthropic/claude-sonnet-latest` | Claude Sonnet Latest | Anthropic | premium | 1.2 | 500000 | yes | yes | yes | no | 1 | active |  | no |
| `arcee-ai/trinity-large-thinking` | Trinity Large Thinking | Arcee AI | premium | 0.14 | 200000 | yes | no | yes | no | 37 | active |  | no |
| `bytedance-seed/seed-1.6` | Seed 1.6 | ByteDance Seed | premium | 0.17 | 200000 | yes | yes | yes | no | 0 | active |  | no |
| `bytedance-seed/seed-1.6-flash` | Seed 1.6 Flash | ByteDance Seed | free | 0.04 | 200000 | yes | yes | yes | no | 12 | active |  | yes |
| `bytedance-seed/seed-2-1-turbo` | Seed 2.1 Turbo | ByteDance Seed | premium | 0.3 | 200000 | yes | yes | yes | no | 0 | active |  | no |
| `bytedance-seed/seed-2.0-code` | Seed-2.0-Code | ByteDance Seed | premium | 0.31 | 200000 | yes | yes | yes | no | 0 | active |  | no |
| `bytedance-seed/seed-2.0-lite` | Seed-2.0-Lite | ByteDance Seed | premium | 0.17 | 200000 | yes | yes | yes | no | 0 | active |  | no |
| `bytedance-seed/seed-2.0-mini` | Seed-2.0-Mini | ByteDance Seed | free | 0.06 | 200000 | yes | yes | yes | no | 20 | active |  | yes |
| `cerebras/gemma-4-31b-fast` | Gemma 4 31B Fast | Cerebras | premium | 0.52 | 120000 | yes | yes | no | no | 82 | active | recommended, intelligent, roleplay | no |
| `cohere/command-a-plus` | Command A+ | Cohere | premium | 0.18 | 120000 | yes | yes | yes | no | 1 | active |  | no |
| `~deepseek/deepseek-flash-latest` | DeepSeek Flash Latest | DeepSeek | premium | 0.05 | 500000 | yes | yes | yes | no | 0 | active |  | no |
| `~deepseek/deepseek-pro-latest` | DeepSeek Pro Latest | DeepSeek | premium | 0.2 | 500000 | yes | yes | no | no | 0 | active |  | no |
| `deepseek/deepseek-v3.2` | DeepSeek V3.2 | DeepSeek | premium | 0.15 | 120000 | yes | no | yes | no | 167791 | active |  | no |
| `deepseek/deepseek-v4-flash` | DeepSeek V4 Flash 0423 | DeepSeek | premium | 0.03 | 500000 | yes | no | yes | no | 7018 | active |  | no |
| `deepseek/deepseek-v4-flash-0731` | DeepSeek V4 Flash 0731 | DeepSeek | premium | 0.03 | 500000 | yes | no | yes | no | 132 | active |  | no |
| `~deepseek/deepseek-v4-flash-latest` | DeepSeek V4 Flash Latest | DeepSeek | premium | 0.03 | 500000 | yes | yes | yes | no | 449 | active |  | no |
| `deepseek/deepseek-v4-flash-vision-exp` | DeepSeek V4 Flash Vision Exp | DeepSeek | premium | 0.12 | 500000 | yes | yes | yes | no | 1 | active |  | no |
| `deepseek/deepseek-v4-pro` | DeepSeek V4 Pro 0423 | DeepSeek | premium | 0.11 | 500000 | yes | no | yes | no | 1669 | active |  | no |
| `deepseek/deepseek-v4-pro-0813` | DeepSeek V4 Pro 0813 | DeepSeek | premium | 0.74 | 500000 | yes | yes | yes | no | 5 | active |  | no |
| `deepseek/deepseek-v4.1-flash` | DeepSeek V4.1 Flash | DeepSeek | premium | 0.05 | 500000 | yes | yes | yes | no | 5 | active | recommended, roleplay | no |
| `deepseek/deepseek-v4.1-flash:batch` | DeepSeek V4.1 Flash (batch) | DeepSeek | premium | 0.06 | 500000 | no | no | no | yes | 0 | active |  | no |
| `fireworks/ember-1` | Ember-1 | Fireworks | premium | 1.8 | 500000 | yes | yes | yes | no | 0 | active |  | no |
| `google/gemini-3-flash-preview` | Gemini 3 Flash Preview | Google | premium | 0.31 | 500000 | yes | yes | no | no | 40 | active |  | no |
| `google/gemini-3-flash-preview:batch` | Gemini 3 Flash Preview (batch) | Google | premium | 0.16 | 500000 | no | no | no | yes | 0 | active |  | no |
| `google/gemini-3.1-flash-lite` | Gemini 3.1 Flash Lite | Google | premium | 0.16 | 500000 | yes | yes | yes | no | 354 | active |  | no |
| `google/gemini-3.1-flash-lite:batch` | Gemini 3.1 Flash Lite (batch) | Google | premium | 0.08 | 500000 | no | no | no | yes | 0 | active |  | no |
| `google/gemini-3.1-flash-lite-preview` | Gemini 3.1 Flash Lite Preview | Google | premium | 0.16 | 500000 | yes | yes | yes | no | 15881 | active |  | no |
| `google/gemini-3.1-pro-preview` | Gemini 3.1 Pro Preview | Google | premium | 1.24 | 500000 | no | yes | yes | no | 90 | active | roleplay | no |
| `google/gemini-3.1-pro-preview:batch` | Gemini 3.1 Pro Preview (batch) | Google | premium | 0.62 | 500000 | no | no | yes | yes | 0 | active |  | no |
| `google/gemini-3.1-pro-preview-customtools` | Gemini 3.1 Pro Preview Custom Tools | Google | premium | 1.24 | 500000 | yes | yes | yes | no | 6 | active |  | no |
| `google/gemini-3.5-flash` | Gemini 3.5 Flash | Google | premium | 0.93 | 500000 | yes | yes | yes | no | 9 | active |  | no |
| `google/gemini-3.5-flash:batch` | Gemini 3.5 Flash (batch) | Google | premium | 0.46 | 500000 | no | no | yes | yes | 0 | active |  | no |
| `google/gemini-3.5-flash-lite` | Gemini 3.5 Flash Lite | Google | premium | 0.2 | 500000 | yes | yes | yes | no | 1 | active | recommended, intelligent | no |
| `google/gemini-3.5-flash-lite:batch` | Gemini 3.5 Flash Lite (batch) | Google | premium | 0.1 | 500000 | no | no | yes | yes | 0 | active |  | no |
| `google/gemini-3.6-flash` | Gemini 3.6 Flash | Google | premium | 0.45 | 500000 | yes | yes | yes | no | 4 | active |  | no |
| `google/gemini-3.6-flash:batch` | Gemini 3.6 Flash (batch) | Google | premium | 0.22 | 500000 | no | no | yes | yes | 0 | active |  | no |
| `google/gemini-3.7-flash` | Gemini 3.7 Flash | Google | premium | 0.45 | 500000 | yes | yes | yes | no | 7 | active |  | no |
| `google/gemini-3.7-flash:batch` | Gemini 3.7 Flash (batch) | Google | premium | 0.22 | 500000 | no | no | yes | yes | 0 | active |  | no |
| `google/gemini-3.8-flash` | Gemini 3.8 Flash | Google | premium | 0.45 | 500000 | yes | yes | yes | no | 7 | active |  | no |
| `google/gemini-3.8-flash:batch` | Gemini 3.8 Flash (batch) | Google | premium | 0.22 | 500000 | no | no | yes | yes | 0 | active |  | no |
| `~google/gemini-flash-latest` | Gemini Flash Latest | Google | premium | 0.45 | 500000 | yes | yes | yes | no | 3 | active |  | no |
| `~google/gemini-pro-latest` | Gemini Pro Latest | Google | premium | 1.24 | 500000 | no | yes | yes | no | 6 | active |  | no |
| `google/gemma-4-26b-a4b-it` | Gemma 4 26B A4B | Google | free | 0.05 | 200000 | yes | yes | no | no | 1159 | active |  | yes |
| `google/gemma-4-31b-it` | Gemma 4 31B | Google | free | 0.05 | 200000 | yes | yes | no | no | 113857 | active | recommended, intelligent, roleplay | yes |
| `ibm-granite/granite-4.0-h-micro` | Granite 4.0 Micro | IBM | free | 0.01 | 120000 | no | no | no | no | 9 | active |  | yes |
| `ibm-granite/granite-4.2-8b` | Granite 4.2 8B | IBM | free | 0.03 | 120000 | yes | no | yes | no | 10 | active |  | yes |
| `inception/mercury-2` | Mercury 2 | Inception | premium | 0.14 | 120000 | yes | no | yes | no | 6 | active |  | no |
| `inception/mercury-2.5` | Mercury 2.5 | Inception | free | 0.02 | 200000 | yes | no | yes | no | 27 | active |  | yes |
| `inference-net/schematron-v2-small` | Schematron V2 Small | Inference.net | free | 0.03 | 120000 | no | no | no | no | 1 | active |  | yes |
| `inference-net/schematron-v2-turbo` | Schematron V2 Turbo | Inference.net | free | 0.02 | 120000 | no | no | no | no | 2 | active |  | yes |
| `kwaipilot/kat-coder-pro-v2.5` | KAT-Coder-Pro V2.5 | Kwaipilot | premium | 0.43 | 200000 | no | no | no | yes | 0 | active |  | no |
| `meituan/longcat-2.0` | LongCat 2.0 | Meituan | premium | 0.17 | 500000 | yes | no | yes | no | 11 | active |  | no |
| `meta/muse-glimmer-30b` | Muse Glimmer 30B | Meta | premium | 0.2 | 120000 | yes | yes | yes | no | 1 | active |  | no |
| `meta/muse-spark-1.1` | Muse Spark 1.1 | Meta | premium | 0.71 | 500000 | yes | yes | yes | no | 0 | active |  | no |
| `meta/muse-spark-1.2` | Muse Spark 1.2 | Meta | premium | 0.71 | 500000 | yes | yes | yes | no | 0 | active |  | no |
| `meta/muse-spark-1.2-contributor` | Muse Spark 1.2 Contributor | Meta | free | 0.05 | 500000 | yes | yes | yes | no | 33 | active |  | yes |
| `meta/muse-spark-1.3` | Muse Spark 1.3 | Meta | premium | 0.71 | 500000 | yes | yes | yes | no | 1 | active |  | no |
| `meta/muse-spark-1.3-contributor` | Muse Spark 1.3 Contributor | Meta | free | 0.05 | 500000 | yes | yes | yes | no | 27 | active |  | yes |
| `minimax/minimax-m2` | MiniMax M2 | MiniMax | premium | 0.17 | 200000 | yes | no | yes | no | 2 | active |  | no |
| `minimax/minimax-m2-her` | MiniMax M2-her | MiniMax | premium | 0.17 | 30000 | no | no | no | no | 111 | active | roleplay | no |
| `minimax/minimax-m2.1` | MiniMax M2.1 | MiniMax | premium | 0.17 | 200000 | yes | no | yes | no | 0 | active |  | no |
| `minimax/minimax-m2.5` | MiniMax M2.5 | MiniMax | premium | 0.16 | 200000 | yes | no | yes | no | 1 | active |  | no |
| `minimax/minimax-m2.7` | MiniMax M2.7 | MiniMax | premium | 0.12 | 200000 | yes | no | yes | no | 37 | active |  | no |
| `minimax/minimax-m3` | MiniMax M3 | MiniMax | premium | 0.17 | 500000 | yes | yes | yes | no | 86 | active |  | no |
| `mistralai/devstral-2512` | Devstral 2 2512 | Mistral | premium | 0.24 | 200000 | yes | no | no | no | 0 | active |  | no |
| `mistralai/ministral-14b-2512` | Ministral 3 14B 2512 | Mistral | free | 0.1 | 200000 | yes | yes | no | no | 31 | active |  | yes |
| `mistralai/ministral-3b-2512` | Ministral 3 3B 2512 | Mistral | free | 0.05 | 120000 | yes | yes | no | no | 1 | active |  | yes |
| `mistralai/ministral-8b-2512` | Ministral 3 8B 2512 | Mistral | free | 0.08 | 200000 | yes | yes | no | no | 4 | active |  | yes |
| `mistralai/ministral-8b-2512:batch` | Ministral 3 8B 2512 (batch) | Mistral | free | 0.04 | 200000 | no | no | no | yes | 0 | active |  | yes |
| `mistralai/mistral-large-2512` | Mistral Large 3 2512 | Mistral | premium | 0.28 | 200000 | no | no | no | yes | 36 | active |  | no |
| `mistralai/mistral-large-2512:batch` | Mistral Large 3 2512 (batch) | Mistral | premium | 0.14 | 200000 | no | no | no | yes | 0 | active |  | no |
| `mistralai/mistral-medium-3-5` | Mistral Medium 3.5 | Mistral | premium | 0.9 | 200000 | yes | yes | no | no | 0 | active |  | no |
| `mistralai/mistral-medium-3-5:batch` | Mistral Medium 3.5 (batch) | Mistral | premium | 0.45 | 200000 | no | no | no | yes | 0 | active |  | no |
| `mistralai/mistral-small-2603` | Mistral Small 4 | Mistral | premium | 0.09 | 200000 | yes | yes | yes | no | 5482 | active | roleplay | no |
| `mistralai/mistral-small-2603:batch` | Mistral Small 4 (batch) | Mistral | free | 0.04 | 200000 | no | no | no | yes | 0 | active |  | yes |
| `mistralai/voxtral-small-24b-2507` | Voxtral Small 24B 2507 | Mistral | free | 0.06 | 30000 | yes | no | no | no | 2 | active |  | yes |
| `moonshotai/kimi-k2-thinking` | Kimi K2 Thinking | MoonshotAI | premium | 0.35 | 200000 | yes | no | yes | no | 30 | active |  | no |
| `moonshotai/kimi-k2.5` | Kimi K2.5 | MoonshotAI | premium | 0.27 | 200000 | yes | no | yes | no | 65 | active |  | no |
| `moonshotai/kimi-k2.6` | Kimi K2.6 | MoonshotAI | premium | 0.56 | 200000 | yes | yes | yes | no | 32 | active |  | no |
| `moonshotai/kimi-k2.7-code` | Kimi K2.7 Code | MoonshotAI | premium | 0.4 | 200000 | yes | yes | yes | no | 2 | active |  | no |
| `moonshotai/kimi-k3` | Kimi K3 | MoonshotAI | premium | 0.75 | 500000 | yes | yes | yes | no | 21 | active |  | no |
| `moonshotai/kimi-k3:batch` | Kimi K3 (batch) | MoonshotAI | premium | 1.37 | 500000 | no | no | no | yes | 0 | active |  | no |
| `~moonshotai/kimi-latest` | Kimi Latest | MoonshotAI | premium | 0.44 | 500000 | yes | yes | yes | no | 17 | active |  | no |
| `nvidia/nemotron-3-nano-30b-a3b` | Nemotron 3 Nano 30B A3B | NVIDIA | free | 0.03 | 200000 | yes | no | yes | no | 6 | active |  | yes |
| `nvidia/nemotron-3-super-120b-a12b` | Nemotron 3 Super | NVIDIA | premium | 0.05 | 200000 | yes | no | yes | no | 112 | active |  | no |
| `nvidia/nemotron-3-ultra-550b-a55b` | Nemotron 3 Ultra | NVIDIA | premium | 0.29 | 200000 | yes | no | yes | no | 18 | active |  | no |
| `nvidia/nemotron-3.5-content-safety` | Nemotron 3.5 Content Safety | NVIDIA | free | 0.1 | 120000 | no | no | yes | no | 0 | active |  | yes |
| `nvidia/nemotron-3.5-lightning` | Nemotron 3.5 Lightning | NVIDIA | free | 0.03 | 200000 | yes | no | yes | no | 31 | active |  | yes |
| `nex-agi/nex-n2.5-mini` | Nex-N2.5-Mini | Nex AGI | free | 0.01 | 200000 | no | yes | yes | no | 1 | active |  | yes |
| `nex-agi/nex-n2.5-pro` | Nex-N2.5-Pro | Nex AGI | free | 0.04 | 200000 | yes | no | yes | no | 1 | active |  | yes |
| `~openai/gpt-astra-latest` | GPT Astra Latest | OpenAI | premium | 6 | 500000 | no | no | yes | yes | 0 | active |  | no |
| `openai/gpt-chat-latest` | GPT Chat Latest | OpenAI | premium | 3.1 | 200000 | no | no | no | yes | 14 | active |  | no |
| `~openai/gpt-luna-latest` | GPT Luna Latest | OpenAI | premium | 0.06 | 500000 | no | no | no | yes | 0 | active |  | no |
| `~openai/gpt-mini-latest` | GPT Mini Latest | OpenAI | premium | 0.46 | 200000 | no | no | no | yes | 0 | active |  | no |
| `~openai/gpt-sol-latest` | GPT Sol Latest | OpenAI | premium | 1.2 | 500000 | no | no | yes | yes | 0 | active |  | no |
| `~openai/gpt-terra-latest` | GPT Terra Latest | OpenAI | premium | 1.24 | 500000 | no | no | no | yes | 0 | active |  | no |
| `openai/gpt-5-pro` | GPT-5 Pro | OpenAI | premium | 9.9 | 200000 | no | no | yes | yes | 0 | active |  | no |
| `openai/gpt-5-pro:batch` | GPT-5 Pro (batch) | OpenAI | premium | 4.95 | 200000 | no | no | yes | yes | 0 | active |  | no |
| `openai/gpt-5.1` | GPT-5.1 | OpenAI | premium | 0.83 | 200000 | yes | yes | yes | no | 2 | active |  | no |
| `openai/gpt-5.1:batch` | GPT-5.1 (batch) | OpenAI | premium | 0.41 | 200000 | no | no | no | yes | 0 | active |  | no |
| `openai/gpt-5.1-codex` | GPT-5.1-Codex | OpenAI | premium | 0.83 | 200000 | yes | yes | yes | no | 0 | active |  | no |
| `openai/gpt-5.1-codex-max` | GPT-5.1-Codex-Max | OpenAI | premium | 0.83 | 200000 | no | yes | yes | no | 0 | active |  | no |
| `openai/gpt-5.1-codex-mini` | GPT-5.1-Codex-Mini | OpenAI | premium | 0.17 | 200000 | yes | yes | yes | no | 0 | active |  | no |
| `openai/gpt-5.2` | GPT-5.2 | OpenAI | premium | 1.16 | 200000 | yes | yes | yes | no | 0 | active |  | no |
| `openai/gpt-5.2:batch` | GPT-5.2 (batch) | OpenAI | premium | 0.58 | 200000 | no | no | no | yes | 0 | active |  | no |
| `openai/gpt-5.2-chat` | GPT-5.2 Chat | OpenAI | premium | 1.16 | 120000 | no | no | no | yes | 1 | active |  | no |
| `openai/gpt-5.2-pro` | GPT-5.2 Pro | OpenAI | premium | 13.86 | 200000 | no | no | yes | yes | 0 | active |  | no |
| `openai/gpt-5.2-pro:batch` | GPT-5.2 Pro (batch) | OpenAI | premium | 6.93 | 200000 | no | no | yes | yes | 0 | active |  | no |
| `openai/gpt-5.2-codex` | GPT-5.2-Codex | OpenAI | premium | 1.16 | 200000 | yes | yes | yes | no | 0 | active |  | no |
| `openai/gpt-5.3-codex` | GPT-5.3-Codex | OpenAI | premium | 1.16 | 200000 | yes | yes | yes | no | 0 | active |  | no |
| `openai/gpt-5.4` | GPT-5.4 | OpenAI | premium | 1.55 | 500000 | yes | yes | yes | no | 13 | active |  | no |
| `openai/gpt-5.4:batch` | GPT-5.4 (batch) | OpenAI | premium | 0.78 | 500000 | no | no | no | yes | 0 | active |  | no |
| `openai/gpt-5.4-mini` | GPT-5.4 Mini | OpenAI | premium | 0.46 | 200000 | yes | yes | yes | no | 0 | active |  | no |
| `openai/gpt-5.4-mini:batch` | GPT-5.4 Mini (batch) | OpenAI | premium | 0.23 | 200000 | no | no | no | yes | 0 | active |  | no |
| `openai/gpt-5.4-nano` | GPT-5.4 Nano | OpenAI | premium | 0.12 | 200000 | yes | yes | no | no | 17 | active |  | no |
| `openai/gpt-5.4-nano:batch` | GPT-5.4 Nano (batch) | OpenAI | premium | 0.06 | 200000 | no | no | no | yes | 0 | active |  | no |
| `openai/gpt-5.4-pro` | GPT-5.4 Pro | OpenAI | premium | 18.6 | 500000 | yes | yes | yes | no | 1 | active |  | no |
| `openai/gpt-5.4-pro:batch` | GPT-5.4 Pro (batch) | OpenAI | premium | 9.3 | 500000 | no | no | yes | yes | 0 | active |  | no |
| `openai/gpt-5.5` | GPT-5.5 | OpenAI | premium | 3.1 | 500000 | yes | yes | yes | no | 1 | active |  | no |
| `openai/gpt-5.5:batch` | GPT-5.5 (batch) | OpenAI | premium | 1.55 | 500000 | no | no | no | yes | 0 | active |  | no |
| `openai/gpt-5.5-pro` | GPT-5.5 Pro | OpenAI | premium | 18.6 | 500000 | no | no | yes | yes | 1 | active |  | no |
| `openai/gpt-5.5-pro:batch` | GPT-5.5 Pro (batch) | OpenAI | premium | 9.3 | 500000 | no | no | yes | yes | 0 | active |  | no |
| `openai/gpt-5.6-luna` | GPT-5.6 Luna | OpenAI | premium | 0.12 | 500000 | yes | yes | no | no | 2 | active | intelligent | no |
| `openai/gpt-5.6-luna:batch` | GPT-5.6 Luna (batch) | OpenAI | premium | 0.06 | 500000 | no | no | no | yes | 0 | active |  | no |
| `openai/gpt-5.6-luna-pro` | GPT-5.6 Luna Pro | OpenAI | premium | 0.12 | 500000 | yes | yes | yes | no | 1 | active |  | no |
| `openai/gpt-5.6-luna-pro:batch` | GPT-5.6 Luna Pro (batch) | OpenAI | premium | 0.06 | 500000 | no | no | no | yes | 0 | active |  | no |
| `openai/gpt-5.6-sol` | GPT-5.6 Sol | OpenAI | premium | 1.2 | 500000 | yes | yes | no | no | 0 | active | intelligent | no |
| `openai/gpt-5.6-sol:batch` | GPT-5.6 Sol (batch) | OpenAI | premium | 0.6 | 500000 | no | no | no | yes | 0 | active |  | no |
| `openai/gpt-5.6-sol-pro` | GPT-5.6 Sol Pro | OpenAI | premium | 1.2 | 500000 | yes | yes | no | no | 0 | active |  | no |
| `openai/gpt-5.6-sol-pro:batch` | GPT-5.6 Sol Pro (batch) | OpenAI | premium | 0.6 | 500000 | no | no | no | yes | 0 | active |  | no |
| `openai/gpt-5.6-terra` | GPT-5.6 Terra | OpenAI | premium | 1.24 | 500000 | yes | yes | yes | no | 1 | active |  | no |
| `openai/gpt-5.6-terra:batch` | GPT-5.6 Terra (batch) | OpenAI | premium | 0.62 | 500000 | no | no | no | yes | 0 | active |  | no |
| `openai/gpt-5.6-terra-pro` | GPT-5.6 Terra Pro | OpenAI | premium | 1.24 | 500000 | yes | yes | yes | no | 0 | active |  | no |
| `openai/gpt-5.6-terra-pro:batch` | GPT-5.6 Terra Pro (batch) | OpenAI | premium | 0.62 | 500000 | no | no | no | yes | 0 | active |  | no |
| `openai/gpt-6-astra` | GPT-6 Astra | OpenAI | premium | 6 | 500000 | yes | yes | yes | no | 1 | active |  | no |
| `openai/gpt-6-astra:batch` | GPT-6 Astra (batch) | OpenAI | premium | 3 | 500000 | no | no | yes | yes | 0 | active |  | no |
| `openai/gpt-6-astra-pro` | GPT-6 Astra Pro | OpenAI | premium | 6 | 500000 | yes | yes | yes | no | 0 | active |  | no |
| `openai/gpt-6-astra-pro:batch` | GPT-6 Astra Pro (batch) | OpenAI | premium | 3 | 500000 | no | no | yes | yes | 0 | active |  | no |
| `openai/gpt-6-luna` | GPT-6 Luna | OpenAI | premium | 0.06 | 500000 | yes | yes | yes | no | 0 | active |  | no |
| `openai/gpt-6-luna:batch` | GPT-6 Luna (batch) | OpenAI | free | 0.03 | 500000 | no | no | no | yes | 0 | active |  | yes |
| `openai/gpt-6-luna-pro` | GPT-6 Luna Pro | OpenAI | premium | 0.06 | 500000 | yes | yes | yes | no | 0 | active |  | no |
| `openai/gpt-6-luna-pro:batch` | GPT-6 Luna Pro (batch) | OpenAI | free | 0.03 | 500000 | no | no | no | yes | 0 | active |  | yes |
| `openai/gpt-6-sol` | GPT-6 Sol | OpenAI | premium | 1.2 | 500000 | yes | yes | yes | no | 0 | active |  | no |
| `openai/gpt-6-sol:batch` | GPT-6 Sol (batch) | OpenAI | premium | 0.6 | 500000 | no | no | no | yes | 0 | active |  | no |
| `openai/gpt-6-sol-pro` | GPT-6 Sol Pro | OpenAI | premium | 1.2 | 500000 | yes | yes | yes | no | 0 | active |  | no |
| `openai/gpt-6-sol-pro:batch` | GPT-6 Sol Pro (batch) | OpenAI | premium | 0.6 | 500000 | no | no | no | yes | 0 | active |  | no |
| `openai/gpt-6.1-sol` | GPT-6.1 Sol | OpenAI | premium | 1.2 | 500000 | no | no | yes | yes | 0 | active |  | no |
| `openai/gpt-6.1-sol-pro` | GPT-6.1 Sol Pro | OpenAI | premium | 1.2 | 500000 | yes | no | yes | yes | 0 | active |  | no |
| `openai/gpt-oss-safeguard-20b` | gpt-oss-safeguard-20b | OpenAI | free | 0.04 | 120000 | no | no | yes | no | 0 | active |  | yes |
| `openrouter/free` | Free Models Router | Openrouter | free | 0 | 200000 | yes | no | yes | no | 11 | active |  | yes |
| `perceptron/perceptron-mk1` | Perceptron Mk1 | Perceptron | premium | 0.11 | 30000 | no | yes | yes | no | 8 | active |  | no |
| `perceptron/perceptron-mk1.5` | Perceptron Mk1.5 | Perceptron | premium | 0.11 | 30000 | yes | no | yes | no | 0 | active |  | no |
| `perplexity/sonar-pro-search` | Sonar Pro Search | Perplexity | premium | 1.8 | 200000 | no | yes | yes | no | 0 | active |  | no |
| `poolside/laguna-s-2.1` | Laguna S 2.1 | Poolside | free | 0.05 | 500000 | yes | no | yes | no | 34 | active |  | yes |
| `poolside/laguna-xs-2.1` | Laguna XS 2.1 | Poolside | free | 0.03 | 200000 | yes | no | yes | no | 20 | active |  | yes |
| `prism-ml/ternary-bonsai-2-27b` | Ternary Bonsai 2 27B | PrismML | premium | 0.05 | 200000 | yes | yes | yes | no | 0 | active |  | no |
| `qwen/qwen3-coder-next` | Qwen3 Coder Next | Qwen | premium | 0.08 | 200000 | yes | no | no | no | 3 | active |  | no |
| `qwen/qwen3-max-thinking` | Qwen3 Max Thinking | Qwen | premium | 0.47 | 200000 | yes | no | yes | no | 0 | active |  | no |
| `qwen/qwen3-vl-30b-a3b-instruct` | Qwen3 VL 30B A3B Instruct | Qwen | premium | 0.09 | 200000 | yes | yes | no | no | 0 | active |  | no |
| `qwen/qwen3-vl-30b-a3b-thinking` | Qwen3 VL 30B A3B Thinking | Qwen | premium | 0.15 | 200000 | yes | yes | yes | no | 0 | active |  | no |
| `qwen/qwen3-vl-32b-instruct` | Qwen3 VL 32B Instruct | Qwen | premium | 0.06 | 120000 | yes | yes | no | no | 0 | active |  | no |
| `qwen/qwen3-vl-8b-instruct` | Qwen3 VL 8B Instruct | Qwen | premium | 0.07 | 200000 | yes | yes | no | no | 0 | active |  | no |
| `qwen/qwen3-vl-8b-thinking` | Qwen3 VL 8B Thinking | Qwen | premium | 0.13 | 120000 | yes | yes | yes | no | 0 | active |  | no |
| `qwen/qwen3.5-397b-a17b` | Qwen3.5 397B A17B | Qwen | premium | 0.29 | 200000 | yes | yes | yes | no | 0 | active |  | no |
| `qwen/qwen3.5-plus-02-15` | Qwen3.5 Plus 2026-02-15 | Qwen | premium | 0.16 | 500000 | yes | yes | yes | no | 0 | active |  | no |
| `qwen/qwen3.5-plus-20260420` | Qwen3.5 Plus 2026-04-20 | Qwen | premium | 0.19 | 500000 | yes | yes | yes | no | 1 | active |  | no |
| `qwen/qwen3.5-122b-a10b` | Qwen3.5-122B-A10B | Qwen | premium | 0.17 | 200000 | yes | yes | yes | no | 0 | active |  | no |
| `qwen/qwen3.5-27b` | Qwen3.5-27B | Qwen | premium | 0.13 | 200000 | yes | yes | yes | no | 0 | active |  | no |
| `qwen/qwen3.5-35b-a3b` | Qwen3.5-35B-A3B | Qwen | premium | 0.1 | 200000 | yes | yes | yes | no | 21 | active |  | no |
| `qwen/qwen3.5-9b` | Qwen3.5-9B | Qwen | free | 0.05 | 200000 | no | yes | yes | no | 6 | active |  | yes |
| `qwen/qwen3.5-flash-02-23` | Qwen3.5-Flash | Qwen | free | 0.04 | 500000 | yes | yes | no | no | 204 | active |  | yes |
| `qwen/qwen3.6-27b` | Qwen3.6 27B | Qwen | premium | 0.23 | 200000 | yes | yes | yes | no | 0 | active |  | no |
| `qwen/qwen3.6-35b-a3b` | Qwen3.6 35B A3B | Qwen | premium | 0.1 | 200000 | yes | yes | yes | no | 41 | active |  | no |
| `qwen/qwen3.6-flash` | Qwen3.6 Flash | Qwen | premium | 0.12 | 500000 | yes | yes | yes | no | 16 | active |  | no |
| `qwen/qwen3.6-max-preview` | Qwen3.6 Max Preview | Qwen | premium | 0.64 | 200000 | yes | no | yes | no | 0 | active |  | no |
| `qwen/qwen3.6-plus` | Qwen3.6 Plus | Qwen | premium | 0.2 | 500000 | yes | yes | yes | no | 2 | active |  | no |
| `qwen/qwen3.7-flash` | Qwen3.7 Flash | Qwen | free | 0.02 | 500000 | yes | no | yes | no | 200 | active |  | yes |
| `qwen/qwen3.7-max` | Qwen3.7 Max | Qwen | premium | 0.83 | 500000 | yes | no | yes | no | 2 | active |  | no |
| `qwen/qwen3.7-plus` | Qwen3.7 Plus | Qwen | premium | 0.19 | 500000 | yes | yes | yes | no | 32 | active |  | no |
| `qwen/qwen3.8-2.4t-a95b` | Qwen3.8 2.4T A95B | Qwen | premium | 1.12 | 500000 | yes | no | yes | no | 0 | active |  | no |
| `qwen/qwen3.8-27b` | Qwen3.8 27B | Qwen | premium | 0.26 | 500000 | yes | yes | yes | no | 0 | active |  | no |
| `qwen/qwen3.8-flash` | Qwen3.8 Flash | Qwen | premium | 0.08 | 500000 | no | no | no | yes | 0 | active |  | no |
| `qwen/qwen3.8-max-0902` | Qwen3.8 Max (0902) | Qwen | premium | 1.12 | 500000 | yes | yes | yes | no | 0 | active |  | no |
| `qwen/qwen3.8-max-prime` | Qwen3.8 Max Prime | Qwen | premium | 2.24 | 500000 | yes | yes | yes | no | 0 | active |  | no |
| `qwen/qwen3.8-omni-flash` | Qwen3.8 Omni Flash | Qwen | premium | 0.08 | 500000 | yes | yes | yes | no | 0 | active |  | no |
| `rekaai/reka-edge` | Reka Edge | Rekaai | free | 0.05 | 8000 | yes | yes | no | no | 2 | active |  | yes |
| `relace/relace-search` | Relace Search | Relace | premium | 0.56 | 200000 | yes | no | no | no | 0 | active |  | no |
| `sakana/fugu-max` | Fugu Max | Sakana | premium | 1.12 | 500000 | yes | yes | yes | no | 0 | active |  | no |
| `sakana/fugu-ultra` | Fugu Ultra | Sakana | premium | 3.1 | 500000 | yes | yes | yes | no | 0 | active |  | no |
| `sakana/fugu-ultra-v2` | Fugu Ultra v2 | Sakana | premium | 3.1 | 500000 | yes | yes | yes | no | 1 | active |  | no |
| `sakana/sakana-namazu` | Sakana Namazu | Sakana | premium | 0.56 | 200000 | yes | yes | yes | no | 0 | active |  | no |
| `x-ai/grok-4.20` | Grok 4.20 | SpaceXAI | premium | 0.68 | 500000 | yes | yes | no | no | 50 | active |  | no |
| `x-ai/grok-4.20-multi-agent` | Grok 4.20 Multi-Agent | SpaceXAI | premium | 0.68 | 500000 | no | yes | yes | no | 2 | active |  | no |
| `x-ai/grok-4.3` | Grok 4.3 | SpaceXAI | premium | 0.68 | 500000 | yes | yes | yes | no | 10 | active |  | no |
| `x-ai/grok-4.3:batch` | Grok 4.3 (batch) | SpaceXAI | premium | 0.54 | 500000 | no | no | no | yes | 0 | active |  | no |
| `x-ai/grok-4.5` | Grok 4.5 | SpaceXAI | premium | 1.12 | 500000 | yes | no | yes | yes | 9 | active |  | no |
| `x-ai/grok-4.6` | Grok 4.6 | SpaceXAI | premium | 1.12 | 500000 | yes | yes | yes | no | 5 | active |  | no |
| `x-ai/grok-4.7` | Grok 4.7 | SpaceXAI | premium | 1.12 | 500000 | yes | yes | yes | no | 2 | active |  | no |
| `x-ai/grok-build-0.1` | Grok Build 0.1 | SpaceXAI | premium | 0.54 | 200000 | yes | yes | yes | no | 0 | active |  | no |
| `stepfun/step-3.5-flash` | Step 3.5 Flash | StepFun | free | 0.06 | 200000 | yes | no | yes | no | 99 | active |  | yes |
| `stepfun/step-3.7-flash` | Step 3.7 Flash | StepFun | premium | 0.12 | 200000 | yes | yes | yes | no | 7 | active |  | no |
| `tencent/hy-mt2-1.8b` | Hy-MT2-1.8B | Tencent | free | 0.03 | 8000 | no | no | no | no | 1 | active |  | yes |
| `tencent/hy-mt2-30b-a3b` | Hy-MT2-30B-A3B | Tencent | free | 0.04 | 8000 | no | no | no | no | 5 | active |  | yes |
| `tencent/hy-mt2-7b` | Hy-MT2-7B | Tencent | free | 0.04 | 8000 | no | no | no | no | 0 | active |  | yes |
| `tencent/hy3` | Hy3 | Tencent | premium | 0.08 | 200000 | yes | no | yes | no | 39 | active |  | no |
| `tencent/hy3-preview` | Hy3 preview | Tencent | premium | 0.1 | 200000 | yes | no | yes | no | 99 | active |  | no |
| `tencent/hy4-preview` | Hy4 preview | Tencent | premium | 0.47 | 500000 | yes | no | yes | no | 2 | active |  | no |
| `thinkingmachines/inkling` | Inkling | Thinking Machines | premium | 0.56 | 500000 | yes | yes | yes | no | 0 | active |  | no |
| `thinkingmachines/inkling-small` | Inkling Small | Thinking Machines | premium | 0.25 | 500000 | no | no | no | yes | 0 | active |  | no |
| `unbiased/pareto` | Pareto | Unbiased | premium | 1.4 | 200000 | yes | yes | no | no | 1 | active |  | no |
| `unbiased/pareto-26.10-preview` | Pareto 26.10 Preview | Unbiased | premium | 0.46 | 500000 | yes | yes | no | no | 0 | active |  | no |
| `upstage/solar-mini4` | Solar Mini 4 | Upstage | free | 0.03 | 500000 | yes | no | yes | no | 0 | active |  | yes |
| `upstage/solar-pro-3` | Solar Pro 3 | Upstage | premium | 0.09 | 120000 | no | no | yes | no | 1 | active |  | no |
| `upstage/solar-pro4` | Solar Pro 4 | Upstage | free | 0.05 | 500000 | yes | no | yes | no | 108 | active |  | yes |
| `writer/palmyra-x5` | Palmyra X5 | Writer | premium | 0.42 | 500000 | no | no | no | no | 0 | active |  | no |
| `xiaomi/mimo-v2.5` | MiMo-V2.5 | Xiaomi | free | 0.08 | 500000 | yes | yes | yes | no | 393 | active |  | yes |
| `xiaomi/mimo-v2.5-pro` | MiMo-V2.5-Pro | Xiaomi | premium | 0.23 | 500000 | yes | no | yes | no | 385 | active |  | no |
| `xiaomi/mimo-v2.6-flash` | MiMo-V2.6-Flash | Xiaomi | free | 0.08 | 500000 | no | no | yes | no | 35 | active |  | yes |
| `xiaomi/mimo-v2.6-pro` | MiMo-V2.6-Pro | Xiaomi | premium | 0.23 | 500000 | yes | yes | yes | no | 1 | active |  | no |
| `xiaomi/mimo-v2.6-pro-ultraspeed` | MiMo-V2.6-Pro-UltraSpeed | Xiaomi | premium | 2.35 | 500000 | yes | yes | yes | no | 0 | active |  | no |
| `z-ai/glm-4.6v` | GLM 4.6V | Z.ai | premium | 0.17 | 120000 | yes | yes | yes | no | 8 | active |  | no |
| `z-ai/glm-4.7` | GLM 4.7 | Z.ai | premium | 0.34 | 200000 | no | no | no | yes | 2 | active |  | no |
| `z-ai/glm-4.7-flash` | GLM 4.7 Flash | Z.ai | free | 0.04 | 200000 | yes | no | yes | no | 1284 | active |  | yes |
| `z-ai/glm-5` | GLM 5 | Z.ai | premium | 0.34 | 200000 | yes | no | yes | no | 768 | active |  | no |
| `z-ai/glm-5-turbo` | GLM 5 Turbo | Z.ai | premium | 0.68 | 200000 | yes | no | yes | no | 1 | active |  | no |
| `z-ai/glm-5.1` | GLM 5.1 | Z.ai | premium | 0.79 | 200000 | yes | no | yes | no | 382 | active |  | no |
| `z-ai/glm-5.2` | GLM 5.2 | Z.ai | premium | 0.32 | 500000 | yes | no | yes | no | 94 | active |  | no |
| `z-ai/glm-5.3` | GLM 5.3 | Z.ai | premium | 0.18 | 500000 | yes | no | yes | no | 16 | active | roleplay | no |
| `z-ai/glm-5.3:batch` | GLM 5.3 (batch) | Z.ai | premium | 0.27 | 500000 | no | no | yes | yes | 0 | active |  | no |
| `z-ai/glm-5.3-flash` | GLM 5.3 Flash | Z.ai | premium | 0.09 | 500000 | yes | yes | yes | no | 401 | active |  | no |
| `z-ai/glm-5.3-flash:batch` | GLM 5.3 Flash (batch) | Z.ai | free | 0.03 | 500000 | no | no | yes | yes | 0 | active |  | yes |
| `z-ai/glm-5.3-flashx` | GLM 5.3 FlashX | Z.ai | premium | 0.21 | 500000 | yes | yes | yes | no | 1 | active |  | no |
| `z-ai/glm-5.3-prime` | GLM 5.3 Prime | Z.ai | premium | 1.58 | 500000 | yes | no | yes | no | 0 | active |  | no |
| `z-ai/glm-5v-turbo` | GLM 5V Turbo | Z.ai | premium | 0.68 | 200000 | yes | yes | yes | no | 18 | active |  | no |
| `~z-ai/glm-flash-latest` | GLM Flash Latest | Z.ai | premium | 0.02 | 500000 | yes | no | yes | no | 2 | active |  | no |
| `~z-ai/glm-latest` | GLM Latest | Z.ai | premium | 0.26 | 500000 | yes | no | yes | no | 1 | active |  | no |
| `inclusionai/ling-3.0-flash` | Ling 3.0 Flash | inclusionAI | free | 0.01 | 200000 | yes | no | yes | no | 6881 | active | recommended | yes |
| `inclusionai/ling-3.0-flash-fin` | Ling 3.0 Flash Fin | inclusionAI | free | 0.02 | 200000 | yes | no | yes | no | 32 | active |  | yes |
| `inclusionai/ling-3.0-flash-vl` | Ling 3.0 Flash VL | inclusionAI | free | 0.01 | 200000 | yes | yes | yes | no | 17 | active |  | yes |
| `inclusionai/ling-3.1-flash` | Ling 3.1 Flash | inclusionAI | free | 0 | 200000 | no | no | no | yes | 0 | active |  | yes |
| `shapesinc/formless-v2` | Formless v2 | shapes.inc | free | 0.01 | 200000 | yes | no | yes | no | 2372 | active | recommended | yes |
| `shapes-1` | shapes-1 | shapes.inc | free | 0 | 30000 | no | no | no | yes | 16 | active |  | yes |
| `~x-ai/grok-latest` | Grok Latest | xAI | premium | 1.12 | 500000 | yes | yes | yes | no | 2 | active |  | no |
| `aion-labs/aion-rp-llama-3.1-8b` | Aion-RP 1.0 (8B) | AionLabs | premium | 0.43 | 30000 | no | no | no | no | 11 | legacy |  | no |
| `amazon/nova-lite-v1` | Nova Lite 1.0 | Amazon | free | 0.03 | 200000 | no | no | no | no | 0 | legacy |  | yes |
| `amazon/nova-micro-v1` | Nova Micro 1.0 | Amazon | free | 0.02 | 120000 | no | no | no | no | 0 | legacy |  | yes |
| `amazon/nova-pro-v1` | Nova Pro 1.0 | Amazon | premium | 0.46 | 200000 | no | no | no | no | 0 | legacy |  | no |
| `anthracite-org/magnum-v4-72b` | Magnum v4 72B | Anthracite Org | premium | 1.35 | 30000 | no | no | no | no | 0 | legacy |  | no |
| `anthropic/claude-opus-4.1` | Claude Opus 4.1 | Anthropic | premium | 9 | 200000 | no | no | no | no | 2 | legacy |  | no |
| `anthropic/claude-opus-4.1:batch` | Claude Opus 4.1 (batch) | Anthropic | premium | 4.5 | 200000 | no | no | no | no | 0 | legacy |  | no |
| `anthropic/claude-sonnet-4` | Claude Sonnet 4 | Anthropic | premium | 1.8 | 200000 | no | no | no | no | 17 | legacy |  | no |
| `anthropic/claude-sonnet-4.5` | Claude Sonnet 4.5 | Anthropic | premium | 1.8 | 500000 | yes | yes | no | no | 436 | legacy |  | no |
| `anthropic/claude-sonnet-4.5:batch` | Claude Sonnet 4.5 (batch) | Anthropic | premium | 0.9 | 500000 | no | no | no | yes | 0 | legacy |  | no |
| `baidu/ernie-4.5-vl-424b-a47b` | ERNIE 4.5 VL 424B A47B | Baidu | premium | 0.23 | 120000 | no | no | no | no | 6 | legacy |  | no |
| `bytedance/ui-tars-1.5-7b` | UI-TARS 7B | ByteDance | free | 0.05 | 120000 | no | no | no | no | 1 | legacy |  | yes |
| `cohere/command-a` | Command A | Cohere | premium | 1.45 | 200000 | no | no | no | no | 0 | legacy |  | no |
| `cohere/command-r-08-2024` | Command R (08-2024) | Cohere | premium | 0.09 | 120000 | no | no | no | no | 1 | legacy |  | no |
| `cohere/command-r-plus-08-2024` | Command R+ (08-2024) | Cohere | premium | 1.45 | 120000 | no | no | no | no | 0 | legacy |  | no |
| `cohere/command-r7b-12-2024` | Command R7B (12-2024) | Cohere | free | 0.02 | 120000 | no | no | no | no | 4 | legacy |  | yes |
| `deepseek/deepseek-chat` | DeepSeek V3 | DeepSeek | premium | 0.15 | 120000 | no | no | no | no | 46 | legacy |  | no |
| `deepseek/deepseek-chat-v3-0324` | DeepSeek V3 0324 | DeepSeek | premium | 0.17 | 120000 | no | no | no | no | 281 | legacy |  | no |
| `deepseek/deepseek-chat-v3.1` | DeepSeek V3.1 | DeepSeek | premium | 0.14 | 120000 | no | no | yes | no | 80 | legacy |  | no |
| `deepseek/deepseek-v3.1-terminus` | DeepSeek V3.1 Terminus | DeepSeek | premium | 0.16 | 120000 | yes | no | no | no | 26 | legacy |  | no |
| `deepseek/deepseek-v3.2-exp` | DeepSeek V3.2 Exp | DeepSeek | premium | 0.14 | 120000 | yes | no | no | no | 88 | legacy |  | no |
| `deepseek/deepseek-r1` | R1 | DeepSeek | premium | 0.4 | 30000 | no | no | yes | no | 0 | legacy |  | no |
| `deepseek/deepseek-r1-0528` | R1 0528 | DeepSeek | premium | 0.29 | 120000 | no | no | yes | no | 0 | legacy |  | no |
| `google/gemini-2.5-flash` | Gemini 2.5 Flash | Google | premium | 0.2 | 500000 | no | no | no | no | 6 | legacy |  | no |
| `google/gemini-2.5-flash:batch` | Gemini 2.5 Flash (batch) | Google | premium | 0.1 | 500000 | no | no | no | no | 0 | legacy |  | no |
| `google/gemini-2.5-flash-lite` | Gemini 2.5 Flash Lite | Google | free | 0.06 | 500000 | no | no | no | no | 4358 | legacy |  | yes |
| `google/gemini-2.5-flash-lite:batch` | Gemini 2.5 Flash Lite (batch) | Google | free | 0.03 | 500000 | no | no | no | no | 0 | legacy |  | yes |
| `google/gemini-2.5-pro` | Gemini 2.5 Pro | Google | premium | 0.83 | 500000 | no | no | yes | no | 40 | legacy |  | no |
| `google/gemini-2.5-pro:batch` | Gemini 2.5 Pro (batch) | Google | premium | 0.41 | 500000 | no | no | yes | no | 0 | legacy |  | no |
| `google/gemini-2.5-pro-preview` | Gemini 2.5 Pro Preview 06-05 | Google | premium | 0.83 | 500000 | no | no | yes | no | 0 | legacy |  | no |
| `google/gemma-2-27b-it` | Gemma 2 27B | Google | premium | 0.34 | 8000 | no | no | no | no | 11 | legacy |  | no |
| `google/gemma-3-12b-it` | Gemma 3 12B | Google | free | 0.03 | 120000 | no | no | no | no | 1 | legacy |  | yes |
| `google/gemma-3-27b-it` | Gemma 3 27B | Google | premium | 0.05 | 120000 | no | no | no | yes | 8479 | legacy |  | no |
| `google/gemma-3-4b-it` | Gemma 3 4B | Google | free | 0.03 | 120000 | no | no | no | no | 4 | legacy |  | yes |
| `gryphe/mythomax-l2-13b` | MythoMax 13B | Gryphe | free | 0.04 | 8000 | no | no | no | no | 137 | legacy |  | yes |
| `mancer/weaver` | Weaver (alpha) | Mancer | premium | 0.21 | 8000 | no | no | no | no | 2 | legacy |  | no |
| `meta-llama/llama-3.1-70b-instruct` | Llama 3.1 70B Instruct | Meta | premium | 0.21 | 120000 | no | no | no | no | 688 | legacy |  | no |
| `meta-llama/llama-3.1-8b-instruct` | Llama 3.1 8B Instruct | Meta | free | 0.03 | 120000 | no | no | no | no | 20 | legacy |  | yes |
| `meta-llama/llama-3.2-1b-instruct` | Llama 3.2 1B Instruct | Meta | free | 0.02 | 30000 | no | no | no | no | 4 | legacy |  | yes |
| `meta-llama/llama-3.2-3b-instruct` | Llama 3.2 3B Instruct | Meta | free | 0.03 | 120000 | no | no | no | no | 2 | legacy |  | yes |
| `meta-llama/llama-3.3-70b-instruct` | Llama 3.3 70B Instruct | Meta | premium | 0.12 | 120000 | no | no | no | no | 4361 | legacy |  | no |
| `meta-llama/llama-4-maverick` | Llama 4 Maverick | Meta | premium | 0.11 | 500000 | no | no | no | no | 167 | legacy |  | no |
| `meta-llama/llama-4-scout` | Llama 4 Scout | Meta | free | 0.06 | 500000 | no | no | no | no | 34 | legacy |  | yes |
| `meta-llama/llama-guard-4-12b` | Llama Guard 4 12B | Meta | free | 0.09 | 120000 | no | no | no | no | 6 | legacy |  | yes |
| `microsoft/phi-4` | Phi 4 | Microsoft | free | 0.04 | 8000 | no | no | no | no | 446 | legacy |  | yes |
| `microsoft/wizardlm-2-8x22b` | WizardLM-2 8x22B | Microsoft | premium | 0.32 | 30000 | no | no | no | no | 5 | legacy |  | no |
| `minimax/minimax-m1` | MiniMax M1 | MiniMax | premium | 0.32 | 500000 | no | no | no | no | 16 | legacy |  | no |
| `minimax/minimax-01` | MiniMax-01 | MiniMax | premium | 0.12 | 500000 | no | no | no | no | 1 | legacy |  | no |
| `mistralai/codestral-2508` | Codestral 2508 | Mistral | premium | 0.17 | 200000 | no | no | no | no | 0 | legacy |  | no |
| `mistralai/codestral-2508:batch` | Codestral 2508 (batch) | Mistral | premium | 0.08 | 200000 | no | no | no | no | 0 | legacy |  | no |
| `mistralai/mistral-medium-3` | Mistral Medium 3 | Mistral | premium | 0.24 | 120000 | no | no | no | no | 0 | legacy |  | no |
| `mistralai/mistral-medium-3.1` | Mistral Medium 3.1 | Mistral | premium | 0.24 | 120000 | yes | yes | no | no | 0 | legacy |  | no |
| `mistralai/mistral-medium-3.1:batch` | Mistral Medium 3.1 (batch) | Mistral | premium | 0.12 | 120000 | no | no | no | yes | 0 | legacy |  | no |
| `mistralai/mistral-nemo` | Mistral Nemo | Mistral | free | 0.01 | 120000 | no | no | no | no | 7 | legacy |  | yes |
| `mistralai/mistral-small-24b-instruct-2501` | Mistral Small 3 | Mistral | free | 0.03 | 30000 | no | no | no | no | 2 | legacy |  | yes |
| `mistralai/mistral-small-3.1-24b-instruct` | Mistral Small 3.1 24B | Mistral | premium | 0.19 | 120000 | no | no | no | no | 17 | legacy |  | no |
| `mistralai/mistral-small-3.2-24b-instruct` | Mistral Small 3.2 24B | Mistral | free | 0.05 | 200000 | no | no | no | no | 15 | legacy |  | yes |
| `mistralai/mixtral-8x22b-instruct` | Mixtral 8x22B Instruct | Mistral | premium | 1.12 | 30000 | no | no | no | no | 0 | legacy |  | no |
| `mistralai/mistral-saba` | Saba | Mistral | premium | 0.11 | 30000 | no | no | no | no | 1 | legacy |  | no |
| `mistralai/mistral-large` | Mistral Large | Mistralai | premium | 1.12 | 120000 | no | no | no | no | 0 | legacy |  | no |
| `mistralai/mistral-large-2407` | Mistral Large 2407 | Mistralai | premium | 1.12 | 120000 | no | no | no | no | 0 | legacy |  | no |
| `moonshotai/kimi-k2` | Kimi K2 0711 | MoonshotAI | premium | 0.33 | 120000 | no | no | no | no | 6 | legacy |  | no |
| `moonshotai/kimi-k2-0905` | Kimi K2 0905 | MoonshotAI | premium | 0.35 | 200000 | yes | no | no | no | 162 | legacy |  | no |
| `morph/morph-v3-fast` | Morph V3 Fast | Morph | premium | 0.42 | 30000 | no | no | no | no | 0 | legacy |  | no |
| `morph/morph-v3-large` | Morph V3 Large | Morph | premium | 0.49 | 200000 | no | no | no | no | 0 | legacy |  | no |
| `nousresearch/hermes-3-llama-3.1-405b` | Hermes 3 405B Instruct | Nous | premium | 0.52 | 120000 | no | no | no | no | 1 | legacy |  | no |
| `nousresearch/hermes-3-llama-3.1-70b` | Hermes 3 70B Instruct | Nous | premium | 0.36 | 120000 | no | no | no | no | 74 | legacy |  | no |
| `nousresearch/hermes-4-405b` | Hermes 4 405B | Nous | premium | 0.56 | 120000 | no | no | yes | no | 10 | legacy |  | no |
| `openai/gpt-3.5-turbo` | GPT-3.5 Turbo | OpenAI | premium | 0.28 | 8000 | no | no | no | no | 10 | legacy |  | no |
| `openai/gpt-3.5-turbo:batch` | GPT-3.5 Turbo (batch) | OpenAI | premium | 0.14 | 8000 | no | no | no | no | 0 | legacy |  | no |
| `openai/gpt-3.5-turbo-0613` | GPT-3.5 Turbo (older v0613) | OpenAI | premium | 0.54 | 8000 | no | no | no | no | 0 | legacy |  | no |
| `openai/gpt-3.5-turbo-16k` | GPT-3.5 Turbo 16k | OpenAI | premium | 1.58 | 8000 | no | no | no | no | 0 | legacy |  | no |
| `openai/gpt-3.5-turbo-instruct` | GPT-3.5 Turbo Instruct | OpenAI | premium | 0.79 | 8000 | no | no | no | no | 0 | legacy |  | no |
| `openai/gpt-4` | GPT-4 | OpenAI | premium | 16.2 | 8000 | no | no | no | no | 1 | legacy |  | no |
| `openai/gpt-4-turbo` | GPT-4 Turbo | OpenAI | premium | 5.6 | 120000 | no | no | no | no | 0 | legacy |  | no |
| `openai/gpt-4-turbo:batch` | GPT-4 Turbo (batch) | OpenAI | premium | 2.8 | 120000 | no | no | no | no | 0 | legacy |  | no |
| `openai/gpt-4.1` | GPT-4.1 | OpenAI | premium | 1.16 | 500000 | no | no | no | no | 3 | legacy |  | no |
| `openai/gpt-4.1:batch` | GPT-4.1 (batch) | OpenAI | premium | 0.58 | 500000 | no | no | no | no | 0 | legacy |  | no |
| `openai/gpt-4.1-mini` | GPT-4.1 Mini | OpenAI | premium | 0.23 | 500000 | no | no | no | no | 0 | legacy |  | no |
| `openai/gpt-4.1-mini:batch` | GPT-4.1 Mini (batch) | OpenAI | premium | 0.12 | 500000 | no | no | no | no | 0 | legacy |  | no |
| `openai/gpt-4.1-nano` | GPT-4.1 Nano | OpenAI | free | 0.06 | 500000 | no | no | no | no | 217 | legacy |  | yes |
| `openai/gpt-4.1-nano:batch` | GPT-4.1 Nano (batch) | OpenAI | free | 0.03 | 500000 | no | no | no | no | 0 | legacy |  | yes |
| `openai/gpt-4o` | GPT-4o | OpenAI | premium | 1.45 | 120000 | no | no | no | no | 0 | legacy |  | no |
| `openai/gpt-4o-2024-05-13` | GPT-4o (2024-05-13) | OpenAI | premium | 2.8 | 120000 | no | no | no | no | 4 | legacy |  | no |
| `openai/gpt-4o-2024-08-06` | GPT-4o (2024-08-06) | OpenAI | premium | 1.45 | 120000 | no | no | no | no | 0 | legacy |  | no |
| `openai/gpt-4o-2024-11-20` | GPT-4o (2024-11-20) | OpenAI | premium | 1.45 | 120000 | no | no | no | no | 1 | legacy |  | no |
| `openai/gpt-4o:batch` | GPT-4o (batch) | OpenAI | premium | 0.73 | 120000 | no | no | no | no | 0 | legacy |  | no |
| `openai/gpt-4o-mini` | GPT-4o-mini | OpenAI | premium | 0.09 | 120000 | no | no | no | no | 753 | legacy |  | no |
| `openai/gpt-4o-mini-2024-07-18` | GPT-4o-mini (2024-07-18) | OpenAI | premium | 0.09 | 120000 | no | no | no | no | 1 | legacy |  | no |
| `openai/gpt-4o-mini:batch` | GPT-4o-mini (batch) | OpenAI | free | 0.04 | 120000 | no | no | no | no | 0 | legacy |  | yes |
| `openai/gpt-5` | GPT-5 | OpenAI | premium | 0.83 | 200000 | yes | yes | yes | no | 0 | legacy |  | no |
| `openai/gpt-5:batch` | GPT-5 (batch) | OpenAI | premium | 0.41 | 200000 | no | no | yes | yes | 0 | legacy |  | no |
| `openai/gpt-5-mini` | GPT-5 Mini | OpenAI | premium | 0.17 | 200000 | yes | yes | yes | no | 0 | legacy |  | no |
| `openai/gpt-5-mini:batch` | GPT-5 Mini (batch) | OpenAI | premium | 0.08 | 200000 | no | no | yes | yes | 0 | legacy |  | no |
| `openai/gpt-5-nano` | GPT-5 Nano | OpenAI | free | 0.03 | 200000 | yes | yes | yes | no | 282 | legacy |  | yes |
| `openai/gpt-5-nano:batch` | GPT-5 Nano (batch) | OpenAI | free | 0.02 | 200000 | no | no | yes | yes | 0 | legacy |  | yes |
| `openai/gpt-oss-120b` | gpt-oss-120b | OpenAI | free | 0.02 | 120000 | yes | no | yes | no | 5 | legacy |  | yes |
| `openai/gpt-oss-120b:batch` | gpt-oss-120b (batch) | OpenAI | free | 0.02 | 120000 | no | no | yes | no | 0 | legacy |  | yes |
| `openai/gpt-oss-20b` | gpt-oss-20b | OpenAI | free | 0.01 | 120000 | no | no | yes | no | 0 | legacy |  | yes |
| `openai/gpt-oss-20b:batch` | gpt-oss-20b (batch) | OpenAI | free | 0.01 | 120000 | no | no | yes | no | 0 | legacy |  | yes |
| `openai/o1` | o1 | OpenAI | premium | 8.7 | 200000 | no | no | no | no | 0 | legacy |  | no |
| `openai/o1-pro` | o1-pro | OpenAI | premium | 87 | 200000 | no | no | no | no | 0 | legacy |  | no |
| `openai/o3` | o3 | OpenAI | premium | 1.16 | 200000 | no | no | no | no | 0 | legacy |  | no |
| `openai/o3:batch` | o3 (batch) | OpenAI | premium | 0.58 | 200000 | no | no | no | no | 0 | legacy |  | no |
| `openai/o3-mini` | o3 Mini | OpenAI | premium | 0.64 | 200000 | no | no | no | no | 0 | legacy |  | no |
| `openai/o3-mini:batch` | o3 Mini (batch) | OpenAI | premium | 0.32 | 200000 | no | no | no | no | 0 | legacy |  | no |
| `openai/o3-mini-high` | o3 Mini High | OpenAI | premium | 0.64 | 200000 | no | no | yes | no | 0 | legacy |  | no |
| `openai/o3-pro` | o3 Pro | OpenAI | premium | 11.6 | 200000 | no | no | no | no | 0 | legacy |  | no |
| `openai/o4-mini` | o4 Mini | OpenAI | premium | 0.64 | 200000 | no | no | no | no | 0 | legacy |  | no |
| `openai/o4-mini:batch` | o4 Mini (batch) | OpenAI | premium | 0.32 | 200000 | no | no | no | no | 0 | legacy |  | no |
| `openai/o4-mini-high` | o4 Mini High | OpenAI | premium | 0.64 | 200000 | no | no | yes | no | 0 | legacy |  | no |
| `perplexity/sonar` | Sonar | Perplexity | premium | 0.52 | 120000 | no | no | no | no | 0 | legacy |  | no |
| `perplexity/sonar-deep-research` | Sonar Deep Research | Perplexity | premium | 1.16 | 120000 | no | no | no | no | 0 | legacy |  | no |
| `perplexity/sonar-pro` | Sonar Pro | Perplexity | premium | 1.8 | 200000 | no | no | no | no | 0 | legacy |  | no |
| `perplexity/sonar-reasoning-pro` | Sonar Reasoning Pro | Perplexity | premium | 1.16 | 120000 | no | no | no | no | 1 | legacy |  | no |
| `qwen/qwen-plus-2025-07-28` | Qwen Plus 0728 | Qwen | premium | 0.15 | 500000 | yes | no | no | no | 0 | legacy |  | no |
| `qwen/qwen-plus` | Qwen-Plus | Qwen | premium | 0.15 | 500000 | no | no | no | no | 4 | legacy |  | no |
| `qwen/qwen-2.5-72b-instruct` | Qwen2.5 72B Instruct | Qwen | premium | 0.19 | 30000 | no | no | no | no | 28 | legacy |  | no |
| `qwen/qwen-2.5-7b-instruct` | Qwen2.5 7B Instruct | Qwen | free | 0.05 | 30000 | no | no | no | no | 0 | legacy |  | yes |
| `qwen/qwen-2.5-coder-32b-instruct` | Qwen2.5 Coder 32B Instruct | Qwen | premium | 0.35 | 30000 | no | no | no | no | 0 | legacy |  | no |
| `qwen/qwen2.5-vl-72b-instruct` | Qwen2.5 VL 72B Instruct | Qwen | premium | 0.42 | 120000 | no | no | no | no | 1 | legacy |  | no |
| `qwen/qwen3-14b` | Qwen3 14B | Qwen | free | 0.06 | 120000 | no | no | no | no | 1 | legacy |  | yes |
| `qwen/qwen3-235b-a22b` | Qwen3 235B A22B | Qwen | premium | 0.26 | 120000 | no | no | no | no | 0 | legacy |  | no |
| `qwen/qwen3-235b-a22b-2507` | Qwen3 235B A22B Instruct 2507 | Qwen | premium | 0.06 | 200000 | no | no | no | no | 9 | legacy |  | no |
| `qwen/qwen3-235b-a22b-thinking-2507` | Qwen3 235B A22B Thinking 2507 | Qwen | premium | 0.16 | 120000 | no | no | yes | no | 0 | legacy |  | no |
| `qwen/qwen3-30b-a3b` | Qwen3 30B A3B | Qwen | premium | 0.07 | 120000 | no | no | no | no | 1 | legacy |  | no |
| `qwen/qwen3-30b-a3b-instruct-2507` | Qwen3 30B A3B Instruct 2507 | Qwen | free | 0.06 | 200000 | no | no | no | no | 1 | legacy |  | yes |
| `qwen/qwen3-30b-a3b-thinking-2507` | Qwen3 30B A3B Thinking 2507 | Qwen | premium | 0.15 | 30000 | yes | no | yes | no | 0 | legacy |  | no |
| `qwen/qwen3-32b` | Qwen3 32B | Qwen | free | 0.05 | 120000 | no | no | no | no | 2 | legacy |  | yes |
| `qwen/qwen3-8b` | Qwen3 8B | Qwen | premium | 0.07 | 120000 | no | no | no | no | 1 | legacy |  | no |
| `qwen/qwen3-coder-30b-a3b-instruct` | Qwen3 Coder 30B A3B Instruct | Qwen | free | 0.04 | 200000 | no | no | no | no | 5 | legacy |  | yes |
| `qwen/qwen3-coder` | Qwen3 Coder 480B A35B | Qwen | premium | 0.17 | 200000 | no | no | no | no | 0 | legacy |  | no |
| `qwen/qwen3-coder-flash` | Qwen3 Coder Flash | Qwen | premium | 0.12 | 500000 | yes | no | no | no | 0 | legacy |  | no |
| `qwen/qwen3-coder-plus` | Qwen3 Coder Plus | Qwen | premium | 0.39 | 500000 | yes | no | no | no | 0 | legacy |  | no |
| `qwen/qwen3-max` | Qwen3 Max | Qwen | premium | 0.47 | 200000 | yes | no | no | no | 0 | legacy |  | no |
| `qwen/qwen3-next-80b-a3b-instruct` | Qwen3 Next 80B A3B Instruct | Qwen | premium | 0.07 | 200000 | yes | no | no | yes | 0 | legacy |  | no |
| `qwen/qwen3-next-80b-a3b-thinking` | Qwen3 Next 80B A3B Thinking | Qwen | premium | 0.1 | 200000 | yes | no | yes | no | 0 | legacy |  | no |
| `qwen/qwen3-vl-235b-a22b-instruct` | Qwen3 VL 235B A22B Instruct | Qwen | premium | 0.14 | 200000 | yes | yes | no | no | 2 | legacy |  | no |
| `qwen/qwen3-vl-235b-a22b-thinking` | Qwen3 VL 235B A22B Thinking | Qwen | premium | 0.28 | 120000 | yes | yes | yes | no | 0 | legacy |  | no |
| `rekaai/reka-flash-3` | Reka Flash 3 | Rekaai | free | 0.05 | 30000 | no | no | yes | no | 1 | legacy |  | yes |
| `relace/relace-apply-3` | Relace Apply 3 | Relace | premium | 0.45 | 200000 | no | no | no | yes | 0 | legacy |  | no |
| `sao10k/l3-lunaris-8b` | Llama 3 8B Lunaris | Sao10K | free | 0.02 | 8000 | no | no | no | no | 1258 | legacy |  | yes |
| `sao10k/l3.1-euryale-70b` | Llama 3.1 Euryale 70B v2.2 | Sao10K | premium | 0.44 | 120000 | no | no | no | no | 0 | legacy |  | no |
| `sao10k/l3.3-euryale-70b` | Llama 3.3 Euryale 70B | Sao10K | premium | 0.34 | 120000 | no | no | no | no | 15 | legacy |  | no |
| `tencent/hunyuan-a13b-instruct` | Hunyuan A13B Instruct | Tencent | premium | 0.08 | 120000 | no | no | no | no | 0 | legacy |  | no |
| `thedrummer/cydonia-24b-v4.1` | Cydonia 24B V4.1 | TheDrummer | premium | 0.16 | 120000 | no | no | no | yes | 51 | legacy |  | no |
| `thedrummer/skyfall-36b-v2` | Skyfall 36B V2 | TheDrummer | premium | 0.29 | 30000 | no | no | no | no | 2 | legacy |  | no |
| `thedrummer/unslopnemo-12b` | UnslopNemo 12B | TheDrummer | premium | 0.21 | 500000 | no | no | no | no | 12 | legacy |  | no |
| `undi95/remm-slerp-l2-13b` | ReMM SLERP 13B | Undi95 | premium | 0.19 | 8000 | no | no | no | no | 21 | legacy |  | no |
| `cognitivecomputations/dolphin-mistral-24b-venice-edition` | Uncensored | Venice | premium | 0.12 | 120000 | no | no | no | no | 12 | legacy |  | no |
| `z-ai/glm-4.5` | GLM 4.5 | Z.ai | premium | 0.34 | 120000 | no | no | no | no | 0 | legacy |  | no |
| `z-ai/glm-4.5-air` | GLM 4.5 Air | Z.ai | premium | 0.08 | 120000 | no | no | no | no | 6 | legacy |  | no |
| `z-ai/glm-4.5v` | GLM 4.5V | Z.ai | premium | 0.34 | 30000 | yes | yes | yes | no | 0 | legacy |  | no |
| `z-ai/glm-4.6` | GLM 4.6 | Z.ai | premium | 0.25 | 200000 | yes | no | yes | no | 15 | legacy |  | no |

---

Public catalog metadata from shapes.inc, snapshotted for local reference. Engine names, ids, and descriptions belong to their publishers / shapes.inc. This file does not relicense that copy.
