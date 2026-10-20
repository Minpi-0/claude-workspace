# fund-company-card（基金公司卡片）

## Purpose

讓使用者從投信公司切入找基金：顯示公司簡稱、法人全名、基金檔數與系列數，點擊進入該公司頁。

## Evidence

| Evidence ID | Source | Region | Notes |
|---|---|---|---|
| E11 | S2 | 基金公司總覽 3 欄卡片（x=150–1290, y=449–1452） | 頭圖＋文字區；卡片寬約 365、欄距 22、高約 320 |
| E11 | S1 | 首頁「依基金公司找基金」4 欄精簡卡 | 無頭圖，僅文字（精簡版，待決定是否為 variant） |

## Component Fingerprint

| Dimension | Description |
|---|---|
| Purpose / behavior / composition role | 內容入口卡片（導向公司頁） |
| Anatomy | 頭圖（上，約 365×182）／公司簡稱（粗體）／法人全名（灰藍小字）／統計（金色「N 檔基金・M 個系列」） |
| Variants / states / modes | full（有頭圖，3 欄）／compact（無頭圖，4 欄，待 Similarity Review 決定） |
| Token contract summary | surface-bright、corner-md、on-background、text-tertiary、text-link |
| Layout / density | 白底、圓角約 12px、文字區左右內距約 24px |
| Visual reference | `../assets/component-review/fund-company-card-full-overview.png`、`../assets/component-review/fund-company-card-compact-home.png` |
| Native platform mapping | not applicable |
| Similar components reviewed | fund-card（結構相近：頭圖＋文字，但資訊不同） → 見 Inventory Similarity Review |

## Anatomy

1. Media：深藍黑底財經插圖（目前為 AI 風格圖，待圖像風格決策）
2. Name：18px 粗體，深藍黑
3. Legal name：14px，灰藍
4. Stats：14px，金色，以「・」分隔

## Variants

- `full`：總覽頁（S2）
- `compact`：首頁（S1）— **blocked pending developer decision**

## States

| State | 說明 |
|---|---|
| Default | 如稿 |
| Hover / pressed / focus-visible | 稿中未見（not evidenced） |
| Disabled / loading / error | not applicable（目前無證據） |

## Token Contract

| Component token | Maps to system token | Purpose | State / mode |
|---|---|---|---|
| `--md-comp-fund-company-card-container-color` | `--md-sys-color-surface-bright` | 卡片底 | default |
| `--md-comp-fund-company-card-corner` | `--md-sys-shape-corner-md` | 圓角 | default |
| `--md-comp-fund-company-card-name-text-color` | `--md-sys-color-on-background` | 名稱 | default |
| `--md-comp-fund-company-card-name-text-size` | `--md-sys-typescale-title-small-size` | 名稱字級 | default |
| `--md-comp-fund-company-card-legal-name-text-color` | `--md-sys-color-text-tertiary` | 法人全名 | default |
| `--md-comp-fund-company-card-legal-name-text-size` | `--md-sys-typescale-label-size` | 法人全名字級 | default |
| `--md-comp-fund-company-card-stats-text-color` | `--md-sys-color-text-link` | 統計 | default |
| `--md-comp-fund-company-card-stats-text-size` | `--md-sys-typescale-label-size` | 統計字級 | default |
| `--md-comp-fund-company-card-grid-gap` | `--md-sys-spacing-gap-grid` | 欄距 22 | default |

## Layout Rules

- 總覽頁 3 欄，內容寬 1140，欄距 22；最後一列靠左，不置中。
- 文字順序固定：名稱 → 法人全名 → 統計；法人全名可能等於簡稱（如「兆豐投信」），此時照常顯示。

## Content Rules

統計格式「85 檔基金・16 個系列」；數字不加粗過度強調，維持金色。

## Accessibility Rules

- 金色統計文字（#8A5A0F 系列）在米白底對比需於實作時驗證 ≥ 4.5:1。
- 整張卡片作為單一連結，頭圖 alt 為空（裝飾性）。

## Do / Don't

- Do：同頁所有公司卡片使用同一種頭圖比例。
- Don't：不要在卡片內加入第二個按鈕；不要使用暗示排名的標示（品牌個性：中立、不推銷）。

## Implementation Notes

頭圖圖片風格尚未定案，spec 只規範比例與位置，不規範圖片內容。
