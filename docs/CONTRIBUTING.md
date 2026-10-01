# 🤝 Contributing to Char-Rot-Benchmark

Thank you for your interest in contributing to the **Persona Resilience (Char-Rot) Benchmark**! This project thrives on community contributions, whether you are adding new test models, refining adversary tactics, or improving evaluating scripts.

---

## 🚀 How You Can Contribute

### 1. Adding New Models to `config/models.json`
You can help expand our evaluation suite across different providers and model families available on OpenRouter.

* Open `config/models.json`.
* Add a new model entry following this schema:
  ```json
  {
    "id": "provider/model-name:free",
    "alias": "Model-Alias",
    "max_tokens": 500,
    "temperature": 0.7
  }
  
