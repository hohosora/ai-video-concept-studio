# AI Video Concept Studio — GPT 貼回協作優化 v1.1

## 已有想法的流程
1. 寫下想法，複製指令到 ChatGPT。
2. ChatGPT 精簡回覆，最後輸出明確標示的「貼回小幫手」內容。
3. 複製整份 ChatGPT 回答回到網站；系統辨識中文故事及英文畫面描述，先顯示結果，再選畫風和影片比例。兩者可以獨立手動修改。

## 相容性
支援新版「貼回小幫手」區塊與舊版標題（故事摘要、故事構思、英文畫面描述、英文鏡頭描述、畫面重點等），兼容部分 Markdown 及編號標題。舊版儲存在瀏覽器的合併內容會遷移至分開的文字欄位。若無法識別標記，保留文字供使用者檢查。

未改動「還沒想法」的六題問卷、畫風及比例選擇、Google Flow／Kling、影片片段管理、文字大小、手機版及 Motion Creator Studio。

## 使用限制
本站以複製／貼上方式與 ChatGPT 協作，**沒有直接串接 OpenAI API**；想法和提示詞儲存在本機瀏覽器。GitHub Pages 從 `main` 分支根目錄部署。

## Google Analytics 4（GA4）

評估 ID：`G-NS0DQELX5F`。Google tag 安裝在 `index.html` 的 `<head>`；`page_view` 由 GA4 自動記錄。其餘由網站在使用者實際操作時發送：

| 事件名稱 | 觸發條件 |
| --- | --- |
| `creation_mode_selected` | 選擇「我有想法」／「還沒想法」（`mode`） |
| `gpt_instruction_copied` | 成功複製 GPT 指令 |
| `chatgpt_opened` | 點擊開啟 ChatGPT |
| `gpt_reply_imported` | 直接貼入完整 GPT 回答（`format_recognized`、`has_english`） |
| `video_style_selected` | 選擇一個畫風（`style_id`） |
| `video_prompt_saved` | 儲存一份影片提示詞（`creation_mode`、`video_format`、`style_id`） |
| `video_prompt_copied` | 成功複製英文／中文影片提示詞（`source`、`language`） |
| `video_platform_selected` | 切換選擇 Google Flow／Kling（`platform`） |
| `generation_platform_opened` | 點擊前往 Google Flow／Kling（`platform`） |
| `video_download_marked` | 手動勾選已下載片段（**非自動驗證真實下載**） |
| `editor_studio_opened` | 點擊 Motion Creator Studio 的外部連結 |
| `project_completed` | 手動按下完成確認（**非自動驗證輸出檔案**） |

僅傳送功能名稱和固定類別選項，不會將使用者撰寫的故事、英文提示詞、影片內容、GPT 回答等文字加入分析事件；複製失敗不計入成功複製事件。網站頁尾已提供 GA4 統計說明。

### 驗證

部署生效後：開啟網站，登入 Google Analytics 4 的「報表 → 即時」，打開網站並觸發幾個操作；觀察 `page_view` 和各事件是否出現。GA4 的事件報告可能有延遲，請不要將剛安裝時顯示的 0 視為整合失敗。自訂參數如果要做 GA4 的自訂維度報表，需在 GA 管理介面另外註冊。
