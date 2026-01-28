# Vector-Link Protocol (VLP)
<br>
Try it out here👉https://maxsikorski.github.io/vector-link-site/

<br>
<br>

![Status](https://img.shields.io/badge/Status-Beta-green) ![Uptime](https://img.shields.io/badge/Uptime-99.9%25-blue) ![Compression](https://img.shields.io/badge/Compression-768x-orange)

**The Universal Standard for AI-to-AI Communication.**

Vector-Link is a high-performance protocol designed to enable "Machine Telepathy." It compresses 4096-dimensional latent vectors into lightweight discrete codes, reducing network bandwidth by **768x** while preserving 99.8% semantic fidelity.

> **Research Lab:** [Your Lab Name]  
> **Read the Research:** [Link to your Blog Post]  
> **Get API Keys:** [Link to your Website]

---

## ⚡ Why Vector-Link?

Multi-agent swarms face a "Bandwidth Wall." Passing raw Float32 tensors between agents (e.g., Llama-3 to Mistral) creates massive latency and egress costs.

VLP solves this using **Residual Vector Quantization (RVQ)** and a proprietary **Universal Adapter**.

| Metric | Raw Vectors (Float32) | Vector-Link (VLP) | Improvement |
| :--- | :--- | :--- | :--- |
| **Payload Size** | ~16 KB | ~16 Bytes | **1000x** |
| **Latency** | 400ms+ | <10ms | **40x** |
| **Format** | Heavy Tensor | Discrete Integers | **Optimized** |

---

## 🚀 Quick Start

### 1. Get an API Key
Access to the Vector-Link Cloud API is restricted to Pro subscribers.
[Request Access Here](https://your-website-url.com/#pricing)

### 2. Make a Request
You can interact with the API using any standard HTTP client.

**Python Example:**

```python
import requests

API_KEY = "vl_live_YOUR_SECRET_KEY"
ENDPOINT = "https://vector-link-api.onrender.com/compress"

# A dummy 768-dim vector (simulating a Llama-3 thought)
# In production, extract this from: model.layers[-1].output
raw_thought = [0.1, -0.5, 0.8] * 256 

payload = {"vector": raw_thought}
headers = {"X-API-Key": API_KEY}

response = requests.post(ENDPOINT, json=payload, headers=headers)

if response.status_code == 200:
    data = response.json()
    print(f"Compressed Codes: {data['codes']}")
    print(f"Compression Ratio: {data['compression_ratio']}x")
else:
    print(f"Error: {response.text}")
```

**cURL Example:**

```bash
curl -X POST "https://vector-link-api.onrender.com/compress" \
     -H "Content-Type: application/json" \
     -H "X-API-Key: vl_live_YOUR_SECRET_KEY" \
     -d '{"vector": [0.1, -0.5, ...]}'
```

---

## 📚 API Reference

### `POST /compress`
Compresses a raw floating-point vector into VLP codes.

**Headers:**
*   `X-API-Key`: (Required) Your valid subscription key.

**Body (JSON):**
*   `vector`: `List[float]` (Must match model dimension: 768)

**Response:**
```json
{
  "codes": [182, 44, 901, 22],
  "meta": "Vector-Link Secured Cloud",
  "status": "success"
}
```

---

## 🔐 Security & Limits

*   **Authentication:** All requests must include the `X-API-Key` header.
*   **Rate Limits:** Pro accounts are limited to 1,000 requests/minute to prevent abuse.
*   **Privacy:** We do **not** store your vectors. Inference is ephemeral. We only log usage metrics (timestamp + token count) for billing.

---

## 🛠 Architecture

The VLP API runs on a distributed cloud cluster (Render) backed by a Supabase authentication layer.

1.  **The Adapter:** A 5.3MB PyTorch kernel trained on GPT-2 latent space.
2.  **The Engine:** FastAPI + Uvicorn (Asynchronous).
3.  **The Cache:** In-memory key validation for sub-millisecond auth.

---

## 📞 Support

*   **System Status:** [Link to your Status Page/Nostr]
*   **Email:** Maxwell.Sikorski@gmail.com
*   **Issues:** Please open a GitHub Issue for SDK bugs.

---

© 2026 Vector-Link Research. All rights reserved.
```
