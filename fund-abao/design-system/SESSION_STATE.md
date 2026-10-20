# Design System Session State

Update this file at every checkpoint.

## Current Stage

- Stage: Checkpoint — baseline extraction complete（現況基準線萃取完成，等待開發者決定）
- Last updated: 2026-10-20
- AI tool / model: Claude Code (cloud session)
- Report Language: zh-Hant (繁體中文)

## Completed Outputs

- [x] DESIGN_EVIDENCE_MAP.md
- [x] INTEGRATION_REVIEW.md（本輪不適用）
- [x] DESIGN_PRINCIPLES.md
- [x] DESIGN_ELEMENTS.md
- [x] TOKEN_ARCHITECTURE.md
- [x] COMPONENT_INVENTORY.md
- [x] design-system/components/*.md component token specs
- [x] INTERACTION_STATES.md
- [x] PAGE_COMPOSITION_RULES.md
- [x] ANTI_AI_STYLE_RULES.md
- [x] tokens/tokens-ref.css
- [x] tokens/tokens-sys.css
- [x] tokens/tokens-comp.css
- [ ] docs/design-system/index.html
- [ ] docs/design-system/review.html

## Key Design Decisions

| Decision | Evidence | Files updated |
|---|---|---|
| 範圍：Figma 首頁、公司總覽、新手入門、追求成長、穩健配息（共 5 頁）；其餘 4 頁與 App 截圖、logo／IP 圖列為 planned | S1–S5、S7–S9 | DESIGN_EVIDENCE_MAP.md |
| Figma 檔無 Variables、頁面為整張點陣圖 → 全部 token 標 `measured`，品牌定調前視為「現況基準線」 | `get_variable_defs` 回傳空；`get_design_context` 僅回傳單張圖片 | TOKEN_ARCHITECTURE.md、tokens/*.css |
| 近似色／近似字級一律暫定 `keep distinct`，不在品牌定調前合併 | 使用者同意（先萃取、後定配色） | TOKEN_ARCHITECTURE.md |
| 抽出 2 個元件規格（site-header、fund-company-card）；button／fund-card 等因相似度待決，不建 spec | Similarity Review | COMPONENT_INVENTORY.md、components/*.md |

## Token Layers Changed

- Reference: 新增 warm／gold／slate／navy／blue／green 色階、字級、間距、圓角（全為 measured）
- System: 新增 background／surface／primary／secondary／category 等語意色與 typescale、layout、shape
- Component: site-header、fund-company-card 共 17 個 token

## Source Duplicate Review

- Duplicate source candidates found: 2（分類頁模板重複）
- Developer decisions recorded in `DESIGN_EVIDENCE_MAP.md`: 2 筆，皆為暫定 keep distinct，待開發者確認
- Source fingerprints recorded: 9 筆（5 筆含 sha256）

## Vibe Project Intake

- Applies: 否（來源為 Figma 點陣圖，非程式專案）
- Route/state manifest:
- Rendered UI capture pass:
- App / Storybook command:
- Local URL:
- Rendered routes or stories covered:
- Screenshots captured or supplied:
- Capture assets path:
- Capture blockers:
- DOM/CSS inspection result:
- Keep/ignore decisions recorded in `DESIGN_EVIDENCE_MAP.md`:
- Demo-only / unused / dead-code / capture-blocked / auth-blocked / contradictory sources found:
- Confidence impact:

## Native App Intake

- Applies:
- Platforms/frameworks:
- App targets/modules inspected:
- Native design-system modules found:
- Native screen/state manifest:
- Native UI Capture Pass:
- Capture commands:
- Devices / OS/API levels covered:
- Screens, previews, screenshot tests, or supplied captures covered:
- Capture assets path:
- Capture blockers:
- Native token/resource files inspected:
- Native component usage verification:
- Keep/ignore decisions recorded in `DESIGN_EVIDENCE_MAP.md`:
- Native source-only / capture-blocked / contradictory sources found:
- Confidence impact:

## Token Review

- Near token candidates found: 8 筆（audit 標出）＋4 組額外觀察
- Developer decisions recorded in `TOKEN_ARCHITECTURE.md`: 8 筆暫定 keep distinct，**全部待開發者確認**

## Component Similarity Review

- Similar component candidates found: 4
- Developer decisions recorded in `COMPONENT_INVENTORY.md`: 4 筆皆為 blocked（待開發者決定）
- Visual comparison assets: `assets/component-review/`（8 張來源截圖裁切）

## Collaboration Review

- Active branches / PRs:
- Integrator / reviewer:
- Integration decisions recorded in `INTEGRATION_REVIEW.md`:
- Blocked items:
- Final integration result:

## Open Questions

1. 主按鈕色：首頁金色 #C8901F 與新手入門頁琥珀 #F5A525，要保留哪一個（或兩者語意區分）？
2. 近似色（#FCF8F1／#FAF7F1、#1F2936／#182330 及三組灰藍）是否合併？建議在品牌配色定案後一併決定。
3. 卡片頭圖的暗色科幻風格是否要保留？IP 中的紅色福神造型是否淘汰？
4. 未分析來源：多元配置、海外佈局、基金學堂、學堂內頁、App 截圖（6 張）、logo 與 IP 原圖（見 S7–S9）。
5. 字體：Figma 為點陣圖，無法確認實際字體與字級，需設計師提供。
6. 分類頁大量卡片頭圖為空白佔位：是未完成稿還是載入狀態？

## Verification

- Source audit mode: strict
- Source audit result: passed (strict)
- Token audit mode: strict
- Token audit result: passed (strict)；8 筆 near-token 決定皆為暫定
- Component audit mode: strict
- Component audit result: passed (strict)；4 筆 similarity 皆 blocked 待決

## Generated Documentation

- HTML docs: docs/design-system/index.html
- HTML docs UI locale: zh-Hant
- Review queue: docs/design-system/review.html

## Recommended Next Prompt

「品牌配色已定案為 …；請依此建立 Figma Variables，並用 design-system-extractor 跑 Late-Arriving Authoritative Source Pass 校準 fund-abao/tokens，並回覆 Token Recalibration 表。」
