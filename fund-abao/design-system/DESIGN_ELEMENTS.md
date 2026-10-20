# Design Elements

## Color System

| Role | Recommended value | Usage | Evidence / rationale |
|---|---|---|---|
| background | warm-96 #FAF7F1 | 頁面底（首頁 hero） | E1 |
| surface | warm-97 #FCF8F1 | 卡片、導覽列 | E1 |
| surface-band | warm-95 #F7F0E2 | 首頁區塊帶、頁尾 | E1 |
| outline | warm-90 #E7DCC6 | 導覽列／區塊分隔線 | E1 |
| primary | gold-55 #C8901F | logo、主 CTA、頁尾欄標題 | E2 |
| secondary（暫定） | gold-65 #F5A525 | 新手入門頁 CTA 與色條；**與 primary 是否合併待決定** | E3 |
| text-link | gold-35 #8A5A0F | 頁尾、金色連結文字 | E3 |
| on-background | slate-12 #182330 | 標題 | E4 |
| text-secondary / tertiary | slate-35 #4B5563 / slate-45 #5B6B7E | 說明文字、副標 | E4 |
| inverse | navy-16 #102B42 | 深色按鈕（閱讀完整指南） | E4 |
| category growth / steady | blue-95 #E6F0FB／blue-40 #1C64AE；green-95 #E1F8F3／green-40 #007A64 | 分類頁背景與動作色；多元配置、海外佈局未取樣 | E5 |

Document palette families with `100` as the lightest step and `0` as the darkest step. Note any close colors that need a merge/keep-distinct decision in `TOKEN_ARCHITECTURE.md`.

## Typography

| Role | Font / weight / size guidance | Usage | Evidence / rationale |
|---|---|---|---|
| display | Noto Sans TC 900 / 48px | 分類頁 H1 | E6（字高 47px，估算） |
| headline | Noto Sans TC 900 / 36px | 首頁主標 | E6（字高 35px，估算） |
| title-large | Noto Sans TC 700 / 28px | 區塊標題（今日精選基金…） | E6 |
| title-medium / small | Noto Sans TC 700 / 20px、18px | 卡片標題（基金卡 20px，公司卡 18px，**建議收斂**） | E6 |
| body | Noto Sans TC 400 / 16px | 說明文字 | E6（推估） |
| label / metadata | Noto Sans TC 500–700 / 14px、12px | 統計、RR chip、版權說明 | E6 |

字體為視覺判斷（Noto Sans TC 風格），Figma 為點陣圖，**無法讀取實際字體名稱**，須由設計師確認。

## Typographic Composition / Text Lockups

Document recurring text groupings separately from atomic typography. Include slot order, hierarchy, scale relationship, spacing, alignment, max line length, line-break behavior, color pairing, and language/script behavior.

| Pattern | Slots | Composition rule | Evidence / rationale | Component candidate |
|---|---|---|---|---|
| 分類頁頭 | breadcrumb → badge → H1 → 副標 | 左對齊，內容寬 1140 起算於 x=150；右側為「這類基金適合」面板 | E5 | category-hero（planned） |
| 區塊標題 | 標題＋灰藍說明句 | 28px 標題、其下一行說明 | E6 | section-heading（planned） |
| 公司卡片文字 | 名稱／法人全名／統計 | 18px 粗體、14px 灰藍、14px 金色統計（以「・」分隔） | E11 | fund-company-card |
| 精選主題 | 金色小標「本週主題」→ 大標 → 內文 → 深色按鈕 | 左對齊，大標約 28px | E6 | topic-feature（planned） |

## Shape And Corners

| Role | Value | Usage | Evidence / rationale |
|---|---|---|---|
| corner-sm | 8px | 按鈕 | E8（目測，Low） |
| corner-md | 12px | 卡片 | E8（目測，Low） |
| corner-full | 999px | 搜尋框、chip、快問快答 pill | E8 |

## Spacing And Density

| Role | Value | Usage | Evidence / rationale |
|---|---|---|---|
| layout-viewport | 1440px | 桌面畫布 | E7 |
| content-width | 1140px（左右留白 150px） | 主內容寬 | E7 |
| gap-grid | 22px | 三欄卡片欄距（實測；與 24px 接近，待確認） | E7 |
| header-height | 60px | 導覽列 | E7 |
| gap-sm / gap-md | 8px / 16px | 元素間距（推估，Low） | E7 |

Record close spacing, sizing, type, radius, opacity, or motion values that need developer confirmation before becoming separate reference tokens.

## Elevation And Depth

| Role | Value | Usage | Evidence / rationale |
|---|---|---|---|
| 卡片陰影 | 極淡的暖色陰影（僅觀察到，未量測數值，**不建立 token**） | 卡片、輸入框 | E1,E2（目測）；陰影數值需設計師提供 |

## Iconography And Imagery

Document icon style, media style, illustration/photo rules, and accessibility expectations.

### 圖像觀察（本輪僅記錄，不寫成規範）

- 基金／公司卡片頭圖：深藍黑底＋金色光的 AI 生成財經插圖，風格偏「暗色科幻」；首頁精選基金偏冷藍、新手入門頁出現青藍色（E9）。與品牌個性「親切、不冷冰冰」有落差。
- 空狀態：追求成長、穩健配息頁大量卡片頭圖為空白佔位（S4、S5），屬於**未完成稿**，不可當作設計規範。
- IP 角色：首頁輪播 6 種 3D 公仔造型（E10），包含紅色福神造型，與「不賭博感」有衝突。
- 圖示：僅觀察到搜尋、箭頭、時鐘等細線條圖示；樣式未量測。
