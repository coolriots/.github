# Feature Extraction Template

# ✅ **Feature Extraction Template for FastAPI Repositories**

## 📁 Repo Name: `______`

## 👤 Filled by: `______`

## 📅 Date: `______`

---

## 1. 🌐 Deployment Domains

| Environment | URL |
| --- | --- |
| Dev | `https://_____.coolriots.ai` |
| Staging | `https://_____.coolriots.ai` |
| Production | `https://_____.coolriots.ai` |

---

## 2. 📘 OpenAPI Documentation URLs

| Mode | OpenAPI Docs URL |
| --- | --- |
| Config | `/projecto/config/api/v1/docs` |
| Execute | `/projecto/execute/api/v1/docs` |

---

## 3. 🚀 List of Available API & WebSocket Endpoints

| Endpoint Path | Method | Description |
| --- | --- | --- |
| `/projecto/config/api/v1/instructions/experiment` | POST | Experiment with different LLM models |
| `/projecto/config/api/v1/instructions/predict` | POST | Perform prediction with selected LLM |
| ... | ... | ... |

> (Add all endpoints for this repo: REST + WebSocket if applicable)
> 

---

## 4. 🔍 Detailed API Feature Extraction

### ✳️ Endpoint: `/projecto/config/api/v1/instructions/experiment`

**Type:** REST API

**Method:** `POST`

**📄 Description:**

This API allows users to experiment with different LLMs (from IBM, Groq, SambaNova, etc.) by providing model ID, prompt, parameters, and related inputs. It helps validate which models and configurations yield the best results.

---

### 📦 Parameters Breakdown

| Location | Name | Type | Dependency | Range Type | Allowed Values / Notes |
| --- | --- | --- | --- | --- | --- |
| Query | `model_type` | string | Independent | Finite | `["IBM", "Groq", "SambaNova"]` |
| Body | `modelId` | string | Dependent on `model_type` | Finite | Examples below |
| Body | `parameters.min_new_tokens` | int | Independent | Infinite | e.g. 10, 100, 1000 |
| Body | `parameters.temperature` | float | Independent | Infinite | e.g. 0.1, 0.5, 1.0, 1.5 |
| Body | `prompt` | string | Independent | Infinite | Free text |
| Body | `project_id` | string | Independent | Finite (optional) | Example project IDs |

---

### 🎯 Value Examples

### If `model_type = IBM`:

- `modelId` ∈
    - `"ibm/granite-3-2-8b-instruct"`
    - `"meta-llama/llama-3-70b-instruct"`

### If `model_type = Groq`:

- `modelId` ∈
    - `"llama2-70b-chat"`
    - `"gemma2-9b-it"`

### If `model_type = SambaNova`:

- `modelId` ∈
    - `"sn-gpt-13b"`
    - `"sn-llama-3-8b"`

---

## 5. 🧪 Test Cases & Postman Collection

### 🔧 Payload Schema (Base Example)

```json
{
  "modelId": "ibm/granite-3-2-8b-instruct",
  "parameters": {
    "min_new_tokens": 100,
    "temperature": 0.7
  },
  "prompt": "Explain Newton's third law.",
  "query": "",
  "region": "jp-tok",
  "image_urls": [],
  "url": "https://example.com",
  "apikey": "xxxxxx",
  "project_id": "proj_123"
}

```

---

### ✅ Use Cases

| Use Case # | model_type | modelId | Parameters | Notes |
| --- | --- | --- | --- | --- |
| 1 | IBM | `ibm/granite-3-2-8b-instruct` | `min_new_tokens: 100`, `temperature: 0.7` | Normal case |
| 2 | IBM | `meta-llama/llama-3-70b-instruct` | `min_new_tokens: 300`, `temperature: 0.5` | Test edge `min_new_tokens` |
| 3 | Groq | `gemma2-9b-it` | `min_new_tokens: 1000`, `temperature: 1.2` | High temp, Groq model |
| 4 | SambaNova | `sn-gpt-13b` | `min_new_tokens: 10`, `temperature: 0.1` | Low temp, short generation |
| 5 | IBM | `ibm/granite-3-2-8b-instruct` | Missing `project_id` | Negative test |

> Add all combinations that cover:
> 
> - Every `model_type`
> - All `modelId` options
> - Edge values for infinite parameters

---

### 📎 Postman Collection Link

➡️ `[Insert link to the saved collection here]`

---

### 🔒 **Step 6: Promised Non-Functional Requirements (Per Endpoint)**

This section outlines the key operational guarantees expected from the API, which will be validated through monitoring, testing, and auditing. Each endpoint should have this section filled out carefully.

### 📌 Example — Endpoint: `/projecto/config/api/v1/instructions/experiment`

1. **Security**
    - Requires a valid API secret key via the `x-api-key` header.
    - Enforces org/suborg-level access control (RBAC).
2. **Performance**
    - Supports up to **500 concurrent requests**.
    - 95th percentile latency should be **≤ 2 seconds**.
    - Average throughput goal: **> 100 RPS sustained**.
3. **Rate Limits**
    - User-level throttle: **100 requests/second**.
    - Global limit: **10,000 requests/hour**.
    - Cooldown: **30 seconds** after burst threshold breach.
4. **Availability**
    - Target uptime SLA: **99.9% monthly**.
    - Graceful degradation in case of model failures (fallback responses or retry).
5. **Data Integrity**
    - All inputs must pass JSON Schema validation.
    - Required fields: `modelId`, `parameters`, `prompt`, etc.
    - Returns `422` on invalid input with descriptive messages.
6. **Observability & Logging**
    - Logs must include:
        - `request_id`, `user_id`, `org_id`, `latency`, `modelId`
    - Timeout, error, and abnormal status codes should trigger:
        - Internal alerts
        - Error traces in centralized logging (e.g., Sentry, Loki)

---

## 🔁 Repeat This Section for Each Endpoint in the Repo
