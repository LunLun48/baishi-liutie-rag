# 六帖問對

以《白氏六帖事類集》前言與卷第一、卷第三至卷第七（正文、總目，以及卷一、六、七的校勘表）為語料庫的檢索問答工具。

線上使用：https://lunlun48.github.io/baishi-liutie-rag/

## 運作方式

- **檢索**：完全在使用者的瀏覽器內完成（二字詞 BM25，並對「風第十三」這類門類名稱加權）。免費、不需任何 token、不必事先建立索引。
- **回答**：預設只列出檢索到的原文段落（命中字詞會標示）。若在「⚙ 設定」選擇服務並填入自己的金鑰，會改由該模型根據這些段落整理成回答，並標明出處。可選 **Gemini（Google）**、**Groq**、**OpenRouter**、**Mistral**（皆有免費額度）、**DeepSeek**（付費，價格低）或 **Claude（Anthropic，付費）**；設定裡的「載入可用模型」會用你的金鑰向該服務查最新模型清單。每個人用自己申請的金鑰。
- 檢索以字詞比對為主，提問時帶入原文用字、典故原句或門類名稱，命中會更準。

## 收錄範圍

| 卷次 | 內容 | 印刷頁標記 | 校勘表 |
|---|---|---|---|
| 前言、卷一 | 正文＋總目 | 有 | 30 條 |
| 卷三、卷四 | 正文＋總目（docx 稿） | 無 | — |
| 卷五 | 正文＋目次（txt 稿） | 無 | — |
| 卷六、卷七 | 正文＋總目（錄文 txt） | 有 | 10／22 條 |

卷二與卷八至卷三十尚待數位化。卷六的錄文稿仍有大量存疑字（團隊自己的覆核清單列出部分葉面存疑率高達 41%），部分門類標題為辨識推測，檢索結果僅供參考，請以書影為準。

## 金鑰與隱私

- 金鑰只存在使用者自己瀏覽器的 localStorage（可在設定取消「記住金鑰」，或一鍵清除），**不會寫入原始碼或這個 repo**。
- 只有在使用模型整理回答時，提問與檢索到的原文段落才會直接從瀏覽器送到所選服務（api.anthropic.com／generativelanguage.googleapis.com／api.groq.com／openrouter.ai／api.mistral.ai／api.deepseek.com）；僅列原文模式不會連線到任何外部服務。
- 免費額度有每分鐘／每日次數上限；依 Google 條款，Gemini 免費額度下的輸入內容可能被用於改進其產品。

## 為什麼不用 Hugging Face / 內建共用 token

早期版本用 Hugging Face Inference Providers 做向量化與生成，後來放棄：

1. 把共用 token 寫進公開 repo 行不通——GitHub 與 Hugging Face 的 secret-scanning 機制會讓該 token 在 push 後很快失效。
2. Hugging Face 帳號的 Inference 額度用完後，所有請求都會回 HTTP 402，需要儲值或訂閱 PRO。

因此改為本機檢索，生成則由使用者自備金鑰（Gemini／Groq／OpenRouter／Mistral 有免費額度，Claude 為付費）。**請勿把任何真實金鑰 commit 進這個 repo。**

舊的 Hugging Face 向量檢索版（使用者自備 token）保留在 git 歷史，commit `80fba7c`。
