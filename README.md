# 六帖問對

以《白氏六帖事類集》前言與卷第一（正文＋校勘表）為語料庫的檢索增強問答（RAG）工具。

- 向量化：BAAI/bge-m3（Hugging Face Inference Providers）
- 生成：DeepSeek-V3（可切換 Qwen2.5-72B / Llama-3.3-70B）
- 所有 API 呼叫皆由使用者瀏覽器直接發出；Hugging Face API Token 僅存於瀏覽器 localStorage

線上使用：啟用 GitHub Pages 後於 `https://lunlun48.github.io/baishi-liutie-rag/` 開啟。

目前僅收錄前言＋卷一（正文 66 段＋校勘表 30 條），卷二至卷三十尚待數位化。

## Token 說明

第一次開啟網站會跳出設定視窗，需自行輸入 Hugging Face Access Token（至 huggingface.co →
Settings → Access Tokens 建立一組具 Inference 權限的 Token）。Token 只存在使用者自己瀏覽器的
localStorage，不會寫入原始碼或 repo。

**曾經嘗試過的做法（已放棄）**：把共用 token 直接寫死在 `index.html` 裡，讓所有人開啟即可用、不用
自行輸入。結果行不通——GitHub 與 Hugging Face 有 secret-scanning 合作機制，只要偵測到公開 repo
裡出現 Hugging Face token，即使手動允許 push 通過，Hugging Face 端仍會在幾分鐘內自動撤銷該
token（連續驗證過三組 token，皆在 push 後迅速失效）。因此**不要**把任何真實 token 寫進這個 repo。
