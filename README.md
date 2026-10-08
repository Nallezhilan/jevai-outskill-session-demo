# Jev vs Frontier LLM Demo

A live workshop demo comparing **Jev** (a structured decision engine) against a **frontier LLM** on the same support-email classification task.

This Next.js application runs side-by-side evaluations to show how the two systems differ in speed, cost, accuracy, and confidence calibration—all on identical inputs.

---

## 🎯 What this project does

Support email classification is a simple, measurable task. By sending the same synthetic emails through both models with the same prompt and answer options, the project highlights differences in:

- speed
- cost
- accuracy
- calibration
- output format compliance
- failure modes

The app compares:
- **Jev** – a typed, probability-based decision model
- **Frontier LLM** – via OpenRouter/OpenAI-compatible API

---

## 📊 Interactive demos

The app includes six demo modes:

- **Race** – compare both models head-to-head on 500 emails
- **Confidence** – inspect uncertainty and what software should do with it
- **Stress** – paste one email and see both answers side by side
- **Calibration** – test whether a model’s confidence maps to actual correctness
- **Dataset** – browse the synthetic support-email corpus and gold labels
- **Health check** – verify both APIs are healthy before a live run

---

## 🛠️ Tech stack

- Next.js 16
- React 19
- TypeScript
- Vitest
- OpenRouter API
- YAML configuration
- JSONL datasets

---

## 📁 Project structure

```text
.
├── app/
│   ├── api/
│   │   ├── classify/
│   │   ├── health/
│   │   ├── race/
│   │   └── stress/
│   ├── calibration/
│   ├── confidence/
│   ├── dataset/
│   ├── health/
│   ├── race/
│   ├── stress/
│   ├── globals.css
│   ├── icon.svg
│   ├── layout.tsx
│   └── page.tsx
├── components/
├── config/
│   ├── llm.yaml
│   ├── pricing.yaml
│   ├── run.yaml
│   ├── task.yaml
│   └── tiers.yaml
├── data/
│   ├── confidence_trio.jsonl
│   ├── emails.jsonl
│   └── hard_cases.jsonl
├── lib/
│   ├── config.ts
│   ├── decision.ts
│   ├── jsonl.ts
│   ├── models/
│   ├── race.ts
│   ├── calls.ts
│   └── tiers.ts
├── scripts/
│   ├── make_dataset.ts
│   ├── review.ts
│   ├── smoke.ts
│   └── parity/
├── tests/
├── .env.example
├── .gitignore
├── AGENTS.md
├── next.config.ts
├── package.json
├── tsconfig.json
├── vitest.config.ts
└── README.md
```

---

## 🚀 Quick start

### 1. Install dependencies

```bash
npm install
```

### 2. Configure environment

```bash
cp .env.example .env
```

Then fill in your keys in `.env`:

```env
TYPESAFE_API_KEY=
OPENROUTER_API_KEY=
```

### 3. Run the app

```bash
npm run dev
```

Open:

```text
http://localhost:4100
```

---

## 🧪 Available scripts

```bash
npm run dev
npm run build
npm run start
npm test
npm run smoke
npm run dataset
npm run review
```

Details:

- `npm run dev` – start the Next.js dev server
- `npm run build` – build the production app
- `npm run start` – run the production build
- `npm test` – run tests with Vitest
- `npm run smoke` – send one email to one or both models
- `npm run dataset` – generate or refresh the dataset
- `npm run review` – manually review gold labels interactively

---

## ⚙️ Configuration

The project reads YAML config from `config/`:

- `task.yaml` – the classification question + labels
- `llm.yaml` – LLM provider and model selection
- `run.yaml` – concurrency, timeout, retry config
- `pricing.yaml` – pricing metadata for model cost calculations
- `tiers.yaml` – tier metadata used by the app

---

## 📦 Data files

The repository includes synthetic support-email datasets in `data/`:

- `data/emails.jsonl` – main dataset
- `data/hard_cases.jsonl` – difficult examples
- `data/confidence_trio.jsonl` – confidence-focused examples

---

## 🔐 Required environment variables

| Variable | Purpose |
|----------|---------|
| `TYPESAFE_API_KEY` | API key for Jev / TypeSafe |
| `OPENROUTER_API_KEY` | API key for the frontier LLM |

---

## 🧠 What the app compares

The app intentionally uses the same task and answer format for both systems, so differences in output are easier to compare:

- accuracy on a labeled dataset
- latency and throughput
- cost per request
- confidence calibration
- agreement/disagreement between systems

---

## 🏁 Notes

- This repo is designed for a workshop/demo environment, not production deployment
- Pricing metadata should be refreshed periodically
- The app warns when pricing configuration is stale

---

## 📄 License

MIT

---

## 🔗 Useful links

- [Next.js](https://nextjs.org/)
- [OpenRouter](https://openrouter.ai/)
- [TypeSafe AI](https://typesafe.ai/)
