# Page Composition Rules

Document how pages should be assembled from foundations and components.

## Viewport And App Shell

- 桌面畫布 1440；內容寬 1140，左右各 150px（E7）。
- 頂部固定為 site-header（高 60），底部為 site-footer（含金融免責聲明）。
- 手機／App 版型：**本輪未分析 App 截圖（S7），不寫規則**。

## Layout Rhythm

- 頁面由「全幅色帶」垂直堆疊：hero（background）→ 區塊帶（surface-band）→ 內容（background）→ 頁尾（surface-band），色帶交替以建立節奏（E1）。
- 區塊標題 28px 置於內容寬左緣，其下為一行灰藍說明句，再接卡片。

## Section Rules

- 首頁順序：快問快答 hero → 本週主題 → 今日精選基金 → 今日精選文章 → 依基金公司找基金 → 頁尾（S1）。
- 分類頁順序：麵包屑 → badge＋H1＋副標＋適合對象面板（hero）→ 基金卡片三欄格線 → 相關公司／系列 → 頁尾（S3–S5）。

## Typographic Composition Rules

Document how recurring text lockups are placed within pages, graphics, cards, editorial surfaces, or marketing compositions. Include alignment, width, rhythm, relationship to media, and responsive wrapping.

## Lists And Rows

## Cards And Surfaces

- 卡片皆為單層（不巢狀）、圓角約 12px、淡陰影；同列卡片等高。
- 白色（warm-100）僅用於輸入框、公司卡片、chip 等「可互動／高亮」層。

## Navigation Regions

- 全站共用單一 site-header；頁尾含「開始」「常用分類」「依基金公司」三欄連結。

## Responsive Behavior

- 稿中僅有 1440 桌面版；窄版斷點與行為 **not evidenced**，待設計師提供。

## Composition Patterns

| Pattern | Evidence | Layout rule | Components | Tokens |
|---|---|---|---|---|
| 分類頁骨架 | E5 | breadcrumb → hero（badge/H1/副標/適合面板）→ 3 欄卡片 → 相關資訊 | category-hero、fund-card | category-* |
| 首頁區塊 | E6 | 標題＋說明句＋卡片格線；4 欄文章、3 欄基金、4 欄公司 | fund-card、article-card、fund-company-card | gap-grid |
