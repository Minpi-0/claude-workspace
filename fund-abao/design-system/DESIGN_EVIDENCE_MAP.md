# Design Evidence Map

Use this file to trace design decisions back to source evidence.

## Source Inventory

Evidence tier ranks the source's authority: `1` production Figma/component library, `2` production screenshots, `3` native simulator/emulator/device captures, `4` rendered project UI, `5` native preview/screenshot-test captures, `6` prototype code, `7` descriptive prompt. When a new source's tier outranks the tiers behind existing decisions, run the Late-Arriving Authoritative Source Pass instead of treating it as supplementary evidence.

| Source ID | Type | Evidence tier | Path / URL / Node | Source fingerprint | Screen or state | Notes | Confidence |
|---|---|---|---|---|---|---|---|
| S1 | Figma page raster（Figma 頁面點陣圖） | 2 | https://www.figma.com/design/T4Ddywb8e4bzFQDXEzU57z/ node `2:4` 首頁 1 | figma:T4Ddywb8e4bzFQDXEzU57z#2:4 · sha256:883e0e89320f3a790ffb561d17ae10528fbba8ad08a277ad756f71d641b0265e | 首頁 desktop 1440×3268 | `assets/rendered-captures/home-desktop-1440.png`；頁面為整張點陣圖，無圖層／Variables | High（視覺）／Medium（量測） |
| S2 | Figma page raster | 2 | node `3:3` 基金公司 1 | figma:T4Ddywb8e4bzFQDXEzU57z#3:3 · sha256:78d051aec867bd2476fb3bca607e0fba1a8ebed7d3e1de78bb557043d9b33aba | 基金公司總覽 1440×1850 | `fund-companies-desktop-1440.png` | High／Medium |
| S3 | Figma page raster | 2 | node `3:7` 新手入門 1 | figma:T4Ddywb8e4bzFQDXEzU57z#3:7 · sha256:38b36c813bb4edd3f90057bb9282801720d9d6e6e6a93d127900c1d1a4cc338d | 新手入門分類頁 1440×1557 | `beginner-desktop-1440.png` | High／Medium |
| S4 | Figma page raster | 2 | node `3:12` 追求成長 2 | figma:T4Ddywb8e4bzFQDXEzU57z#3:12 · sha256:9c1dd695ab32144e4d70e04d6a12f91540eae95e6a331340d5f6ec051d7085da | 追求成長分類頁（縮圖 422×2400，原 1440×8192） | `growth-category-overview-422w.png`；低解析，僅用於色票與版型；多數卡片圖片為空白佔位 | Medium |
| S5 | Figma page raster | 2 | node `3:9` 穩健配息 1 | figma:T4Ddywb8e4bzFQDXEzU57z#3:9 · sha256:8b07961d09449a29246363b83bf14a303dc23c6584f094b619b359b1f1cf1e54 | 穩健配息分類頁（縮圖） | `steady-dividend-overview-422w.png` | Medium |
| S6 | Figma brand brief（描述性需求文件） | 7 | node `3:23` 品牌視覺設計需求 | figma:T4Ddywb8e4bzFQDXEzU57z#3:23 | 需求文字＋品牌個性表 | 非視覺證據；用於品牌個性與交付項目 | High（內容）／不可作 token 來源 |
| S7 | Figma app screenshots（App 截圖） | 2 | nodes `3:13`–`3:18` IMG_1184–1189（390×844） | figma:T4Ddywb8e4bzFQDXEzU57z#page:abo-app-screens | 6 張 iOS 截圖 | **尚未逐張分析**（本輪範圍排除），僅檢視縮圖 | Low |
| S8 | Figma logo / IP raster（Logo 與 IP 圖） | 2 | nodes `3:19` logo、`3:26`、`3:27` IP 圖 | figma:T4Ddywb8e4bzFQDXEzU57z#page:abo-brand-assets | logo 127×130；IP 角色截圖 | **尚未分析**；僅從首頁輪播看到 6 種角色造型 | Low |
| S9 | Figma page raster | 2 | nodes `3:6` 多元配置、`3:8` 海外佈局、`3:5` 基金學堂、`3:4` 學堂內頁 | figma:T4Ddywb8e4bzFQDXEzU57z#3:6, #3:8, #3:5, #3:4 | 其餘頁面 | **本輪未擷取**，列為 planned 來源 | Low |

## Source Duplicate Review

Use this table when two screenshots, graphic/brand exports, Figma nodes, routes, or other exports are exact duplicates or visually/functionally very close. Record the decision before counting both as separate evidence.

| Candidate source | Duplicate of | Match type | Fingerprint / normalized key | Suggested action | Developer decision | Rationale |
|---|---|---|---|---|---|---|
| S4 追求成長 `3:12` | S5 穩健配息 `3:9`（及 `3:6`、`3:8` 同模板頁） | 版型高度相似（同一分類頁模板，僅色調與內容不同） | figma:T4Ddywb8e4bzFQDXEzU57z#3:12 ↔ figma:T4Ddywb8e4bzFQDXEzU57z#3:9 | keep distinct for color evidence / reuse existing source for layout evidence | keep distinct（暫定，provisional；待開發者確認） | 色票證據各自獨立（藍 vs 綠）；版型證據只計一次，避免重複基金卡片灌水信心 |
| S3 新手入門 `3:7` | S4 追求成長 `3:12` | 分類頁頭部與卡片結構相似，但配色不同（琥珀 vs 藍） | figma:T4Ddywb8e4bzFQDXEzU57z#3:7 ↔ figma:T4Ddywb8e4bzFQDXEzU57z#3:12 | keep distinct | keep distinct（暫定，provisional；待開發者確認） | 兩頁 CTA 與色條顏色不同，是本輪發現的重要不一致，需保留為獨立證據 |

## Vibe Project Scope Review（本輪不適用：來源為 Figma 點陣圖，非程式專案）

Use this table when the input is an AI-generated or vibe-coded project. Record whether project evidence is rendered, screenshot, storybook, token-used, component-used, demo-only, unused, dead-code, capture-blocked, auth-blocked, contradictory, or out-of-scope before it influences confidence.

| Source | Classification | Visible in rendered UI | Token/component used | Keep / ignore decision | Rationale |
|---|---|---|---|---|---|

## Native App Project Review

Use this table when the input is a native iOS or Android app project. Record whether native evidence is native-capture, native-preview, screenshot-test, native-token-used, native-component-used, native-source-only, native-capture-blocked, native-contradictory, out-of-scope, or explicitly kept/ignored before it influences confidence.

| Source | Classification | Visible in native capture / screenshot / preview | Token / component / resource used | Keep / ignore decision | Rationale |
|---|---|---|---|---|---|

## Route / State Manifest

Use this table when extracting from a project folder with runnable routes or Storybook stories.

| Route or story | Viewport | State | Render command | Screenshot path | Source files | Capture status | Keep / ignore | Notes |
|---|---|---|---|---|---|---|---|---|

## Native Screen / State Manifest

Use this table when extracting from native iOS or Android screens, previews, screenshot tests, simulators, emulators, or supplied app captures.

| Platform | Screen or component | Source entrypoint | Device / viewport | State | Render/capture command | Screenshot path | Source files | Capture status | Keep / ignore | Notes |
|---|---|---|---|---|---|---|---|---|---|---|

## Rendered UI Capture Attempts

Record every browser capture attempt for runnable projects, including blocked captures.

| Capture ID | Route or story | Viewport | State | URL | Screenshot path | DOM/CSS inspected | Source files linked | Status | Confidence impact |
|---|---|---|---|---|---|---|---|---|---|

## Native UI Capture Attempts

Record every native capture attempt for simulator, emulator, device, preview, screenshot-test, or demo/gallery output, including blocked captures.

| Capture ID | Platform | Screen/component | Device | OS/API | Orientation | State | Command | Screenshot path | Source files linked | Status | Confidence impact |
|---|---|---|---|---|---|---|---|---|---|---|---|

## Evidence

| Evidence ID | Source ID | Region | Observed pattern | Design decision | Affected output | Confidence |
|---|---|---|---|---|---|---|
| E1 | S1,S2,S3 | 頁面底色、卡片、導覽列 | 暖米色系：區塊帶 #F7F0E2、卡片／導覽 #FCF8F1、hero #FAF7F1；新手入門頁底 #FEF7E8；邊線 #E7DCC6；白色僅用於搜尋框與 chip | 以暖米色為品牌基底，白色作為「輸入／高亮」層 | tokens-ref warm-*；sys background/surface/surface-band/outline | Medium（#FCF8F1 與 #FAF7F1 ΔE 0.74，可能是同一色） |
| E2 | S1,S2,S3 | logo 圖示、首頁主 CTA「開始測驗」、頁尾標題 | 金色 #C8901F（logo 圖示底、CTA 底、頁尾欄標題） | 金色 #C8901F 為品牌主色 | ref gold-55；sys primary | High（重複量測） |
| E3 | S3 | 新手入門頁「看介紹」按鈕、badge、卡片頂部色條 | 琥珀色 #F5A525，與首頁 CTA 金色 #C8901F **不同** | 同為主要動作卻用兩種橘金；列為不一致，待品牌決定 | ref gold-65；sys secondary | High（觀察）／決策待定 |
| E4 | S1,S2 | 標題、卡片標題、次要文字 | 標題 #182330、卡片標題 #1F2936、深色按鈕 #102B42、頁尾品牌字 #13243A；次要文字 #5B6B7E／#536475／#4B5563 | 現況用了多組相近深藍／灰藍；建議收斂 | ref slate-*、navy-*；sys on-background/on-surface/text-secondary/text-tertiary | Medium（文字色由抗鋸齒像素取最頻色，可能有 ±2 誤差） |
| E5 | S4,S5 | 分類頁頂部漸層、頁底色、按鈕 | 追求成長：底 #E6F0FB、頂 #D8E9F8、按鈕 #1C64AE；穩健配息：底 #E1F8F3、頂 #BBEDDF、按鈕 #007A64 | 每個分類有專屬色調（底色＋動作色）；多元配置、海外佈局未取樣 | ref blue-*、green-*；sys category-growth-*、category-steady-* | Medium（縮圖取樣）；新手入門為琥珀 |
| E6 | S1,S2,S3 | 標題／內文字級 | 字高：hero H1 47px、首頁 H1 35px、首頁區塊標題 27px、卡片標題 17–19px、卡片 meta 14px | 字級階層約 48／36／28／20／18／14（估算，±2px）；字體為思源黑體系（Noto Sans TC）視覺判斷 | ref size-*、typeface；sys typescale-* | Low（由字高估算，非設計稿數值） |
| E7 | S1,S2,S3 | 版面容器 | 1440 畫布；內容左右各 150px → 內容寬 1140；三欄卡片寬約 365、欄距 22；導覽列高 60；搜尋框 256×40、全圓角 | 內容寬 1140、三欄格線、導覽列 60 | ref size-1140/1440/22/60；sys layout-*、spacing-* | Medium |
| E8 | S1,S2,S3 | 卡片圓角 | 卡片圓角視覺約 12px、按鈕約 8px、搜尋框／chip 全圓角 | radius 8／12／full | ref radius-*；sys shape-corner-* | Low（目測） |
| E9 | S1,S2,S3,S4 | 基金／公司卡片圖片 | 深藍黑底＋金色光的 AI 風格財經插圖（城市、金庫、地球、山）；首頁精選基金為冷藍色調；新手入門頁出現青藍色圖 | 圖像風格偏「暗色科幻」，與「親切、不冷冰冰」品牌個性有落差；同站色調不一致 | DESIGN_ELEMENTS Imagery；ANTI_AI_STYLE_RULES | High（觀察） |
| E10 | S1 | 首頁快問快答輪播 | 6 種 3D 公仔 IP 造型（綠衣、深色上衣、紅色福神、藍帽、藍背景男生…），白色圓角框、彩色背景各異 | IP 風格大致統一為 3D 卡通，但配色與主題（福神）不一致 | COMPONENT_INVENTORY ip-avatar-carousel | Medium |
| E11 | S1,S2 | 公司卡片（圖＋名稱＋法人名＋統計） | 圖上方、名稱粗體深藍、法人全名灰藍、統計金色文字；白底卡片；3 欄 | 公司卡片規格 | components/fund-company-card.md | High |
| E12 | S1,S2,S3 | 導覽列 | logo 左、8 個導覽項居中（窄欄位造成 2 字換行，如「首/頁」「新手入/門」）、搜尋框右；底部邊線 #E7DCC6 | 導覽列規格；**導覽項換行是瑕疵** | components/site-header.md | High |
| E13 | S6 | 品牌個性表 | 親切好懂／專業可靠／中立透明／有點聰明的小驚喜；不要輕浮、冷冰冰、推銷感、賭博感 | 作為 principles 的依據；與暗色科幻圖像、福神 IP 有衝突 | DESIGN_PRINCIPLES | High（內容） |
