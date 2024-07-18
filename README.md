# [台灣縣市氣象資訊](http://13.213.240.133:8001/)
### 這是一個氣象網站，提供即時及當週天氣資訊，輕鬆掌握天氣概況

### 目錄
- [主要功能](#主要功能)
- [系統架構](#系統架構)
- [使用技術](#使用技術)
- [團隊分工](#團隊分工)

---

### 主要功能
- 依照使用者所在位置，即時呈現當地天氣資訊
- 點擊溫度圖示，依各地氣溫高低呈現不同色塊
- 點擊地圖各縣市，切換至指定區域的天氣資訊
![功能展示1]()

---

### 系統架構
- 透過 Git Flow 方式開發，確保各版本控制
- 採用前後端分離方式開發
    - 前端使用 HTML、CSS、JavaScript
    - 後端使用 Python FastAPI ，並採用 MVC 模式設計
- 專案部署於 AWS EC2

---

### 使用技術
- 串接中央氣象署開放資料平臺之資料擷取 API
- 串接 Discord API，結合 Discord Webhook 自動發佈訊息到 Discord Channel
- 串接 Google Geolocation API，定位使用者位置顯示對應天氣資訊

---

### 團隊分工
#### 組長：楊松蒲
- Host 專案，掌握進度
- 開啟 GitHub Repository，建立基礎專案程式
- 根據分工結果，調整專案檔案結構
- 將網站部署於 AWS EC2
#### 前端：陳安琪、游語軒、趙姿晴
- 與後端溝通 API 回傳的資料格式
- 渲染台灣即時氣象資訊內容及資料視覺化
- 搜尋設計框
#### 後端：楊松蒲、許珮萱
- 與前端協調 API 回傳的資料格式
- 串接中央氣象署 API，取得所需資料並彙整提供予前端
- 使用 FastAPI 框架建構網站後端

---

### 前端-陳安琪
氣象網站主要負責項目包含:

1. 搜尋框設計
- 建立下拉選單及搜尋框兩種方式查找該縣市氣象數據
- 建立mapping處理搜尋名稱對應到統一名稱，減少API串接查詢錯誤問題，如 `{台北: 臺北市, 臺北: 臺北市}`
2. 數據串接與處理
- 使用fetch API串接後端指定數據位置，如`/weather/week/${location}`
- 解析並轉換數據格式，建立所需物件以及前端渲染顯示格式，如 `日期+時間段：7/17(晚)`
3. 數據圖表渲染
- 使用API串接後端指定數據位置，如`/weather/week/${location}`

### 前端-游語軒
氣象網站主要負責項目包含:

- 互動式地圖實現
    - 建立兩種方式查詢縣市氣象數據
    - 實現地圖動畫效果
- 數據獲取與展示
    - 使用 Fetch API 串接後端指定數據
        - 例如：`/weather/humidity`（濕度數據）
        - 例如：`/weather/temperature`（溫度數據）
- 數據可視化
    - 建立數據與顏色的映射機制
        - 如：`{ value: 70, color: [40, 133, 0] }`
    - 根據映射結果進行地圖渲染
- 用戶體驗優化
    - 實現滾動動畫效果
- 團隊協作
    - 參與前端工作分配
- 使用Chart.js JavaScript Library生成雨量直條圖(Bar Chart)及早晚溫度曲線圖(Line Chart)
