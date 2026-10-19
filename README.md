# 六帖問對

以《白氏六帖事類集》前言與卷第一（正文＋校勘表）為語料庫的檢索問答工具。

線上使用：https://lunlun48.github.io/baishi-liutie-rag/

## 運作方式

- **檢索**：完全在使用者的瀏覽器內完成（二字詞 BM25，並對「風第十三」這類門類名稱加權）。免費、不需任何 token、不必事先建立索引。
- **回答**：預設只列出檢索到的原文段落（命中字詞會標示）。若在「⚙ 設定」填入自己的 Claude API Key，會改由 Claude 根據這些段落整理成回答，並標明出處。
- 檢索以字詞比對為主，提問時帶入原文用字、典故原句或門類名稱，命中會更準。

目前僅收錄前言＋卷一（正文 66 段＋校勘表 30 條），卷二至卷三十尚待數位化。

## 金鑰與隱私

- Claude API Key 只存在使用者自己瀏覽器的 localStorage（可在設定取消「記住金鑰」，或一鍵清除），**不會寫入原始碼或這個 repo**。
- 只有在使用 Claude 整理回答時，提問與檢索到的原文段落才會直接從瀏覽器送到 api.anthropic.com；僅列原文模式不會連線到任何外部服務。

## 為什麼不用 Hugging Face / 內建共用 token

早期版本用 Hugging Face Inference Providers 做向量化與生成，後來放棄：

1. 把共用 token 寫進公開 repo 行不通——GitHub 與 Hugging Face 的 secret-scanning 機制會讓該 token 在 push 後很快失效。
2. Hugging Face 帳號的 Inference 額度用完後，所有請求都會回 HTTP 402，需要儲值或訂閱 PRO。

因此改為本機檢索，生成則由使用者自備 Claude API Key。**請勿把任何真實金鑰 commit 進這個 repo。**
