# 六帖問對

以《白氏六帖事類集》前言與卷第一（正文＋校勘表）為語料庫的檢索增強問答（RAG）工具。

- 向量化：BAAI/bge-m3（Hugging Face Inference Providers）
- 生成：DeepSeek-V3（可切換 Qwen2.5-72B / Llama-3.3-70B）
- 所有 API 呼叫皆由使用者瀏覽器直接發出

線上使用：啟用 GitHub Pages 後於 `https://lunlun48.github.io/baishi-liutie-rag/` 開啟。

目前僅收錄前言＋卷一（正文 66 段＋校勘表 30 條），卷二至卷三十尚待數位化。

## ⚠️ Token 說明

`index.html` 內建了一組共用的 Hugging Face Token（供本專案團隊直接使用，開啟即可問答，無需自行申請）。

**這代表 Token 是公開的**——任何人只要查看這個 repo 或網站原始碼都看得到它，理論上可能被拿去消耗額度或做其他 Inference 呼叫。因此：

- 這組 Token 應僅具備 Inference（推論）權限，不應有其他帳號操作權限。
- 若額度異常或懷疑外流，請至 [huggingface.co → Settings → Access Tokens](https://huggingface.co/settings/tokens) 撤銷並更換，然後更新 `index.html` 中 `DEFAULT_TOKEN` 常數並重新 commit/push。
- 使用者也可在網站「⚙ 設定」→「使用自己的 Hugging Face Token（進階）」自行填入個人 Token 取代內建的共用值。
