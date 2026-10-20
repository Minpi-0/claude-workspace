# site-header（網站導覽列）

## Purpose

全站頂部導覽：品牌 logo、8 個主要入口、基金搜尋。所有頁面共用（首頁、分類頁、公司頁皆同）。

## Evidence

| Evidence ID | Source | Region | Notes |
|---|---|---|---|
| E12 | S1,S2,S3 | 頂部 0–68px | logo 左、導覽居中、搜尋右；底部邊線 #E7DCC6 |
| E1 | S1,S2,S3 | 背景 | 背景 #FCF8F1（surface） |

## Component Fingerprint

| Dimension | Description |
|---|---|
| Purpose / behavior / composition role | 全域導覽＋搜尋入口 |
| Anatomy | logo（金色圓角方塊＋白色 A＋「基金A寶」粗體）／導覽項×8（首頁、新手入門、追求成長、穩健配息、多元配置、海外佈局、基金公司、基金學堂）／搜尋框 |
| Variants / states / modes | 桌面 1440 版本；手機版未見於稿（App 截圖未分析） |
| Token contract summary | surface、outline、on-background、surface-bright、corner-full、header-height |
| Layout / density | 高 60px；搜尋框 256×40；導覽項欄寬過窄造成雙行換行 |
| Visual reference | `../assets/component-review/site-header-desktop.png` |
| Native platform mapping | not applicable（App 導覽另行萃取） |
| Similar components reviewed | 無（唯一導覽列） |

## Anatomy

1. Brand lockup：logo 圖示 ＋ 品牌字
2. Primary nav：8 個文字連結，14px、粗體、深藍黑
3. Search field：全圓角、白底、細線圖示＋佔位字「搜尋基金」（灰藍）

## Variants

- 桌面（1440）：如稿。
- 窄版／手機：**稿中未見**，不推測。

## States

| State | 說明 |
|---|---|
| Default | 如稿 |
| Hover / pressed / focus-visible | 稿中未見，標示 not evidenced，待設計師補 |
| Active（目前頁） | 稿中未見明顯強調，待確認 |
| Disabled / loading / error | not applicable |

## Token Contract

| Component token | Maps to system token | Purpose | State / mode |
|---|---|---|---|
| `--md-comp-site-header-container-color` | `--md-sys-color-surface` | 背景 | default |
| `--md-comp-site-header-bottom-border-color` | `--md-sys-color-outline` | 底線 | default |
| `--md-comp-site-header-height` | `--md-sys-spacing-region-header-height` | 高度 60 | default |
| `--md-comp-site-header-nav-text-color` | `--md-sys-color-on-background` | 導覽文字 | default |
| `--md-comp-site-header-nav-text-size` | `--md-sys-typescale-label-size` | 導覽文字 14px | default |
| `--md-comp-site-header-search-container-color` | `--md-sys-color-surface-bright` | 搜尋框底 | default |
| `--md-comp-site-header-search-placeholder-color` | `--md-sys-color-on-surface-bright` | 佔位字 | default |
| `--md-comp-site-header-search-corner` | `--md-sys-shape-corner-full` | 全圓角 | default |

## Layout Rules

- 導覽列左右內距約 40px；logo 靠左、搜尋框靠右（距右約 40px）。
- 導覽項需有足夠寬度顯示單行，**稿中「首／頁」「新手入／門」被換行為已知瑕疵，不得複製**。

## Content Rules

導覽項名稱簡短（2–4 字）；搜尋佔位字用動詞＋名詞（「搜尋基金」）。

## Accessibility Rules

- 佔位字 #B8C2C8 在白底對比約 1.9:1，低於 WCAG AA（僅作佔位提示，輸入文字需另用 `on-surface` 色）。
- 搜尋框需有可見標籤或 aria-label。

## Do / Don't

- Do：導覽單行、與頁面其餘文字同字體。
- Don't：不要讓導覽文字換行；不要把搜尋框改成非全圓角（與 pill/chip 語言一致）。

## Implementation Notes

僅依視覺量測；實際 padding、字重數值待設計師確認。
