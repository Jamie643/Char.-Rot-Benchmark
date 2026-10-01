# 📱 iOS Shortcut Automation Setup

This directory contains the mobile configuration instructions for running the **Char-Rot Benchmark** directly on iOS devices using Apple Shortcuts and the OpenRouter API.

---

## 🛠 Setup & Instructions

1. **Open Apple Shortcuts** on your iPhone or iPad.
2. Create a new shortcut named **`Char-Rot Loop`**.
3. Replicate the execution logic:
   * **Variables:** Set `API_KEY`, `Target_Prompt`, `Antagonist_Prompt`, and `Last_Attack`.
   * **Loop:** Add a `Repeat (5 times)` block.
   * **API Calls:** Use `Get Contents of URL` set to `POST` pointing to `https://openrouter.ai/api/v1/chat/completions`.
4. **Key Indexing Rule (Critical):**
   * Apple Shortcuts uses **1-based array indexing**.
   * When parsing the JSON response using **Get Value from Dictionary**, set the keypath to:
     ```text
     choices.1.message.content
     ```
   * *Note:* Querying `choices.0` will fail with an `Item 0 not found` error on iOS.

---

## 📄 Included Configurations
* **`benchmark-loop.shortcut`**: Importable binary workflow (optional).
* **`ios_config.json`**: Pre-formatted system prompt dictionary for mobile payload inspection.
