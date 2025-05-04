# 成大課程：基於 LangChain 的 RAG 與 Function Calling (Tools) 開發教學

## 安裝
### UV 執行檔案安裝
```bash=
# On macOS and Linux.
curl -LsSf https://astral.sh/uv/install.sh | sh

# On Windows.
powershell -c "irm https://astral.sh/uv/install.ps1 | iex"
```
### UV 環境安裝

```bash=
# On macOS and Linux.
mdir -p $HOME/uv
cd $HOME/uv
uv venv langchaing --python 3.11 && source langchaing/bin/activate && uv pip install --upgrade pip

# On Windows
powershell
mkdir -p D:\uv
cd D:\uv
uv venv langchaing --python 3.11 && langchaing\Scripts\activate && uv pip install --upgrade pip
```
### notebook 安裝
```bash=
# On macOS and Linux.
cd $HOME/uv
source langchaing/bin/activate 
uv pip install jupyterlab ipywidgets jupyterlab_widgets

# On Windows
powershell
cd D:\uv
langchaing\Scripts\activate
uv pip install jupyterlab ipywidgets jupyterlab_widgets
```


## jupyter notebook 教學
### 啟動 notebook
```bash=
# On macOS and Linux.
cd $HOME/uv
source langchaing/bin/activate 
jupyter lab


# On Windows
powershell
cd D:\uv
langchaing\Scripts\activate
jupyter lab
```

### notebook 相關指令
```python=
# ! 執行程式符號
!ls

!uv pip install

# %cd 實體切換目錄
%cd 

# 執行連續程式符號
%%bash
...
```

## LLM 課程教學

### 範例一: LLMs
- https://python.langchain.com/docs/introduction/

#### 程式碼
- 01-llms.ipynb

#### 📝 作業
1.  **模型選擇：**
    * 選擇兩個不同的 LLM 模型來完成以下任務。
    * 請勿使用 notebook 中已使用的 `meta/llama-4-maverick-17b-128e-instruct` 模型。
2.  **聊天任務：**
    * 設計一個模擬客戶服務諮詢的多輪對話，目標是解決客戶關於產品退貨的問題。
    * 對話至少包含 5 輪，並包含以下元素：
        * 客戶提出退貨原因
        * 客服詢問詳細資訊 (例如：訂單編號、產品狀況)
        * 客服說明退貨流程與注意事項
        * 客戶追問相關問題
        * 客服總結並提供協助
3.  **模型比較與分析：**
    * 使用選擇的兩個模型分別執行上述多輪對話。
    * 比較兩個模型的輸出，並分析其在以下方面的差異：
        * **準確性：** 是否正確理解客戶問題並提供正確資訊？
        * **流暢度：** 語言是否自然、符合客服人員的說話方式？
        * **相關性：** 回答是否切題、符合對話上下文？
        * **效率：** 回應速度如何？
    * 使用表格或簡短報告總結比較結果，並說明哪個模型更適合用於客戶服務情境，以及原因。

**評分標準：**
* 模型選擇與設定 (20%)
* 多輪對話設計 (30%)
* 模型輸出與比較 (30%)
* 分析與結論 (20%)



### 範例二: Chatbot
- https://python.langchain.com/docs/tutorials/chatbot/ 

#### 程式碼
- 02-chatbot.ipynb


#### 📝 作業
**擴展聊天機器人功能**
1.  **基本功能：**
    * 在 notebook 中，我們創建了一個基本的聊天機器人，它可以記住用戶的名字並在同一 session 中使用它。
    * 你的任務是擴展這個聊天機器人，讓它可以記住多個使用者的資訊，並且在不同的 session 中也能夠正確辨識使用者。
2.  **情境設定：**
    * 將聊天機器人設定為一個線上書店的客服機器人。
    * 除了基本的問候和回答問題外，聊天機器人還需要能夠處理以下功能：
        * 查詢書籍資訊（例如：書名、作者、價格、庫存）。
        * 提供書籍推薦。
        * 處理訂單查詢（例如：訂單狀態、物流資訊）。


**評估標準：**
* 程式碼是否能夠正確區分和辨識不同使用者？ (30%)
* 使用者資訊是否能夠持久化儲存，並在不同 session 中正確載入？ (30%)
* 聊天機器人是否能夠完成指定的情境任務（查詢書籍、提供推薦、處理訂單）？ (40%)




### 範例三: Agent
- https://python.langchain.com/docs/tutorials/agents/ 
- https://python.langchain.com/docs/integrations/tools/

#### 程式碼
- 03-agent.ipynb

#### 📝 作業
1.  **Agent 建立與 API 整合：**
    * 使用 Langchain 建立一個 Agent，並整合至少一個外部 API。
    * 建議可考慮的 API 包括：
        * 台灣高鐵 Open API：查詢時刻表、票價、剩餘座位等。
        * 中央氣象局 Open API：查詢天氣預報、觀測資料等。
        * Google Maps Platform API：查詢地點資訊、導航路線等。
        * 金融監督管理委員會 Open API：查詢股票資訊、匯率資訊等。
    * 你也可以選擇其他你感興趣的 API，但請在報告中說明其功能和應用情境。
2.  **Agent 行為設計：**
    * Agent 應分析使用者意圖，判斷是否需要呼叫外部 API 才能回答問題。
    * 如果使用者詢問的資訊可以透過 API 取得，則 Agent 必須使用 API。
    * 如果無法透過 API 取得，則 Agent 應嘗試使用 LLM 回答。
    * Agent 應向使用者說明其使用的工具（API 或 LLM）以及原因。
3.  **範例互動：**
    * **範例輸入 1：**「請問明天早上從台北到左營的高鐵有哪些車次？」
    * **範例輸出 1：**「我查詢了台灣高鐵 API，明天早上從台北到左營的高鐵車次有以下幾班：...」
    * **範例輸入 2：**「台北 101 有多高？」
    * **範例輸出 2：**「台北 101 的高度是 508 公尺。」（此資訊可能透過 LLM 或 Google Maps API 取得）
4.  **進階功能（選做）：**
    * 整合多個 API，回答更複雜的問題。
    * 加入錯誤處理機制，提升 Agent 的健壯性。
    * 讓 Agent 能夠處理需要多輪對話才能完成的任務。
    * 設計一個簡單的使用者介面，讓使用者可以更方便地與 Agent 互動。

**評估標準：**
* Agent 是否能夠成功整合外部 API？ (40%)
* Agent 是否能夠根據使用者意圖正確判斷是否使用 API？ (40%)
* Agent 的回答是否準確、完整、符合使用者需求？ (20%)


### 範例四: embedding
- https://python.langchain.com/docs/integrations/text_embedding/

#### 程式碼
- 04-embedding.ipynb


#### 📝 作業

**目標：**
* 分析 embedding 模型在不同語境下的表現
* 比較語意相近但字面不同的例子
* 比較不同 embedding 模型在相同任務上的表現 (可選擇)

**內容：**
1.  **設計句子對：**
    * 設計十組句子對，每組包含以下至少兩種語意關係的組合：
        * **同義：** 「他很開心」 vs 「他感到愉快」
        * **近義：** 「這輛車很新」 vs 「這輛車是全新的」
        * **反義：** 「他很高」 vs 「他很矮」
        * **上位/下位詞：** 「狗是一種動物」 vs 「黃金獵犬是一種狗」
        * **因果關係：** 「因為下雨，所以路很濕」 vs 「路很濕是因為下雨」
        * (鼓勵加入複雜句或多義詞)
    * 確保每組句子對中，至少有一對是語意相近，另一對是語意相異。
2.  **計算相似度：**
    * 選擇一個或多個 embedding 模型 (例如： notebook 中提到的或其他你感興趣的模型)。
    * 使用選擇的 embedding 模型計算每組句子對之間的相似度。
    * 建議使用餘弦相似度 (Cosine Similarity) 作為計算方法。
3.  **分析與評估：**
    * 分析模型的語意理解能力：
        * 模型是否能有效分辨語意相近與語意相異的句子對？
        * 模型對於不同語意關係的處理能力是否有差異？
        * 模型在處理複雜句或多義詞時的表現如何？
    * 使用以下指標評估模型表現：
        * **準確度：** 模型是否能正確區分語意相近和語意相異的句子對？ (可自行定義判斷標準)
        * **排序能力：** 如果將所有句子對依相似度排序，語意更相近的句子對是否排在更前面？
    * (如果選擇多個 embedding 模型) 比較不同模型之間的差異。

**評分標準：**
* 句子對設計的完整性與多樣性 (40%)
* 相似度計算的正確性 (30%)
* 分析與評估的深度 (30%)
* 報告的清晰度與完整性 (20%)

### 範例五: retrievers
- https://python.langchain.com/docs/integrations/retrievers/

#### 程式碼
05-retrievers.ipynb

#### 📝 作業

**擴展檢索鏈 (Retrieval Chain)**
Notebook 中創建了一個基本的檢索鏈，將 ArxivRetriever 和 LLM 連接起來回答問題。
1.  **基本功能：**
    * 在 notebook 的基礎上，擴展檢索鏈的功能，使其更加實用。
2.  **擴展方向（選擇至少兩項）：**
    * **文件篩選：** 讓使用者可以根據作者、日期、關鍵字等條件篩選文獻。
    * **摘要生成：** 自動總結檢索到的文獻內容。
    * **多源檢索：** 整合多個 Retriever，從不同來源檢索資訊 (例如 Arxiv、Web、自訂資料庫)。
    * **結果排序：** 根據相關性對檢索結果進行排序和評分。
    * **複雜查詢處理：** 處理包含多個關鍵字和條件的查詢。

**評估標準：**
* 檢索鏈是否能夠正確檢索並呈現相關文獻？ (50%)
* 擴展功能是否能夠有效提升檢索的實用性？ (50%)


### 範例六: vector db
- https://python.langchain.com/docs/integrations/vectorstores/chroma/

#### 程式碼
- 06-vector_db.ipynb

#### 📝 作業
Chroma 可以與 LLM 結合，創建更強大的應用程式。

**作業：**
1.  **設計一個問答系統：**
    * 該系統使用 Chroma 或其他向量資料庫 (可選擇) 來檢索相關文檔，然後使用 LLM 來回答用戶的問題。
2.  **選擇文檔來源：**
    * 選擇一個適合問答系統的文檔來源，例如：
        * 網頁文章
        * 產品說明書
        * 法律文件
        * 學術論文
    * 請在報告中說明你選擇的文檔來源及其適用情境。
3.  **實作向量資料庫操作：**
    * 實作以下向量資料庫操作：
        * **新增文檔：** 將選擇的文檔轉換為 embedding 並存入向量資料庫。
        * **相似度搜尋：** 根據使用者查詢，從向量資料庫中檢索相關文檔。
        * **結果排序：** 根據相關性對檢索結果進行排序。
4.  **回答使用者問題：**
    * 系統能夠根據檢索到的文檔，回答使用者提出的問題。

**評估標準：**
* 系統是否能夠正確回答使用者提出的問題？ (50%)
* 系統是否能夠找到所有相關的文檔？ (50%)


### 範例七: rerank
- https://python.langchain.com/docs/integrations/document_transformers/rankllm-reranker/

#### 程式碼

- 07-rereank.ipynb

#### 📝 作業
**使用 Rerank 提升問答系統**

Notebook 中創建了一個基本的問答系統，使用 Chroma 檢索相關文檔並使用 LLM 回答問題。

**作業：**
1.  **擴展問答系統：**
    * 在 notebook 的基礎上，加入 Rerank 功能，提升系統回答問題的準確性。
2.  **選擇文檔來源：**
    * 選擇一個適合問答系統的文檔來源，例如：
        * 網頁文章
        * 產品說明書
        * 法律文件
        * 學術論文
    * 請在報告中說明你選擇的文檔來源及其適用情境。
3.  **實作 Rerank：**
    * 實作 Rerank 功能，對向量資料庫檢索到的文檔進行重新排序。
    * 可以選擇以下 Rerank 方法：
        * 自訂 Rerank 演算法
    * 請在報告中說明你選擇的 Rerank 方法及其原因。
4.  **回答使用者問題：**
    * 系統能夠根據 Rerank 後的文檔，回答使用者提出的問題。

**評估標準：**
* 系統是否能夠正確回答使用者提出的問題？ (40%)
* Rerank 是否能夠提升檢索結果的相關性？ (30%)
* Rerank 對系統效率的影響？ (30%)



### 範例八: rag
- https://python.langchain.com/docs/tutorials/rag/
- 
#### 程式碼

- 08-rag.ipynb

#### 📝 作業一：核心概念理解（30分）

請簡要回答下列問題

1. 請說明什麼是 RAG（Retrieval-Augmented Generation）？它與傳統的生成式語言模型有什麼不同？
2. 在 RAG 架構中，`Retriever` 和 `Generator` 各自的角色是什麼？它們如何互相配合？
3. 請說明 Embedding 的作用，以及為何要對文本進行向量化？

---

#### 🧑‍💻 作業二：實作練習（30分）

請根據課堂提供的 notebook《08-rag.ipynb》完成以下項目：

1. 嘗試將預設的資料集替換為你自己提供的任意一篇文章（可以是新聞、報導、科普等）。
2. 重新跑過向量嵌入（embedding）、建立向量庫（Vector Store），並透過 RAG Pipeline 提出三個問題，觀察答案是否合理。
3. 將你的文章及三個問答結果，整理為一個簡單的 Markdown 報告提交（附上截圖或輸出文字）。

---

#### 💡 作業三：應用場景發想（40分）

請構思一個你認為適合使用 RAG 技術的應用情境，並回答以下問題：

1. 你的應用要解決什麼問題？目標使用者是誰？
2. 為什麼使用 RAG 比純 LLM 或資料庫查詢更有優勢？
3. 在此情境中，你可能會蒐集什麼樣的資料做為知識庫？
4. 比較不同LLM模型在此議題的能力比較



### 範例九 MCP server
- 參考 https://github.com/langchain-ai/langchain-mcp-adapters

#### Tool
Tool 是為了 function calling 所設計的通訊協議。它的重點在於，把原本寫在每個 LLM Client 裡的「怎麼呼叫工具」這段邏輯，抽離成一個獨立的通訊協議。這樣開發者只需要專注在工具本身的實作，不需要再管怎麼塞給每個模型怎麼用。

為了更清楚理解這件事，我們來看看原本的 function calling 過程：

![image](https://hackmd-prod-images.s3-ap-northeast-1.amazonaws.com/uploads/upload_e70ec25a10598154f83eb5e594f077f7.png?AWSAccessKeyId=AKIA3XSAAW6AWSKNINWO&Expires=1746368676&Signature=RslGVV6yqit8lHYItyfjxodC4to%3D)


#### MCP 到底是什麼
最近 MCP 超級火，都被吹到天上去了，有人說 MCP 是 AI 領域的「USB-C 標準」，甚至有人預測它將引領下一個 AI 應用時代的到來。不過，乍看之下，MCP 不就跟原本的 function calling 幹的是同一件事嗎?

其實不然，MCP 不是想取代 function calling，MCP 實際上是把 Tool Execution 的部份從原本 function calling 的流程中抽離出來，並統一了接口。 另外，不只是 Tool，MCP 總共提出了三個核心概念：Tool、Resource、Prompt，目的是把 AI Agent 常見的操作邏輯抽象成一套標準化的介面。
![image](https://hackmd-prod-images.s3-ap-northeast-1.amazonaws.com/uploads/upload_732160e36e7b1b8bb410c7845a365541.png?AWSAccessKeyId=AKIA3XSAAW6AWSKNINWO&Expires=1746368706&Signature=Z5fybnR%2BOgw0ufiGXJZczOL0eYI%3D)
