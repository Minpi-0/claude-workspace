# Token Architecture（Token 架構）

> **Baseline 狀態**：本套 tokens 全為 `measured`（Figma 檔無 Variables、頁面為點陣圖，以像素取樣量測）。它描述「現況」，**不是已核准的品牌規範**；品牌配色定案後須走 Late-Arriving Authoritative Source Pass 重新校準。

Document the token layers, prefixes, naming model, and audit rules for this package.

## Prefixes

| Layer | Prefix | Responsibility |
|---|---|---|
| Reference | `--md-ref-*` | Raw values only |
| System | `--md-sys-*` | Shared semantic roles |
| Component | `--md-comp-*` | Component and region slots |

## Inheritance

```txt
component token -> system token -> reference value
```

## Reference Color Scale

Use numeric palette steps from light to dark:

```txt
100 -> 0
```

- `100` is the lightest visible step in a palette family.
- `0` is the darkest visible step in a palette family.
- Higher numbers must be visually lighter than lower numbers in the same family.
- Semantic color names belong in `sys`, not `ref`.

## Layer Rules

| Layer | Allowed | Forbidden |
|---|---|---|
| Reference | raw color steps, sizes, weights, radius, opacity | semantic roles, component names |
| System | shared roles, foreground/background pairs, spacing roles | component anatomy |
| Component | component slots and states | raw values, direct reference values |

## Near Token Decisions

Use this table when candidate reference tokens are visually or numerically close. Stop and confirm with the developer before finalizing unresolved rows.

Provenance is `authored` (Figma Variable/style, design-system export, source-code token — no measurement error) or `measured` (screenshot sampling, pixel measurement). `measured` vs `measured` may merge through normal review; when either side is `authored`, default to keep distinct and never round the authored value away; `authored` vs `authored` always requires an explicit developer decision.

| Candidate A | Provenance A | Candidate B | Provenance B | Difference | Decision (`merge` / `keep distinct`) | Rationale | Confirmed by |
|---|---|---|---|---|---|---|---|
| `--md-ref-color-warm-98` #FEF7E8 | measured | `--md-ref-color-warm-95` #F7F0E2 | measured | ΔE 2.46 | keep distinct（保留區分） | 新手入門頁底色 vs 首頁區塊帶色，為不同頁面的不同區域；品牌定調前不合併（provisional） | pending developer（待開發者確認） |
| `--md-ref-color-warm-97` #FCF8F1 | measured | `--md-ref-color-warm-96` #FAF7F1 | measured | ΔE 0.74 | keep distinct（保留區分） | 卡片／導覽列表面 vs 首頁 hero 背景；差異可能只是量測雜訊，**建議品牌定調後合併**（provisional） | pending developer（待開發者確認） |
| `--md-ref-color-slate-15` #1F2936 | measured | `--md-ref-color-slate-12` #182330 | measured | ΔE 2.96 | keep distinct（保留區分） | 卡片標題 vs 首頁標題文字；近似深藍黑，**建議合併為單一標題色**（provisional） | pending developer（待開發者確認） |
| `--md-ref-size-12` 12px | measured | `--md-ref-size-14` 14px | measured | 2px | keep distinct（保留區分） | metadata 與 label 字級，皆為字高估算（±2px），Low confidence | pending developer（待開發者確認） |
| `--md-ref-size-14` 14px | measured | `--md-ref-size-16` 16px | measured | 2px | keep distinct（保留區分） | label 與 body 字級，字高估算 | pending developer（待開發者確認） |
| `--md-ref-size-16` 16px | measured | `--md-ref-size-18` 18px | measured | 2px | keep distinct（保留區分） | body 與 title-small（公司卡片名稱 h=17）字級 | pending developer（待開發者確認） |
| `--md-ref-size-18` 18px | measured | `--md-ref-size-20` 20px | measured | 2px | keep distinct（保留區分） | 公司卡片名稱（h=17）與基金卡片標題（h=19）；建議收斂為單一標題字級 | pending developer（待開發者確認） |
| `--md-ref-size-20` 20px | measured | `--md-ref-size-22` 22px | measured | 2px | keep distinct（保留區分） | 22 為卡片格線間距（實測 22），20 為字級，不同 token family，不應合併 | pending developer（待開發者確認） |

### 未被 audit 標出、但觀察到的近似色（供討論）

| 群組 | 觀察到的值 | 備註 |
|---|---|---|
| 次要文字灰藍 | #5B6B7E（新手入門 hero 副標）、#536475（首頁副標）、#4B5563（卡片說明） | 三種灰藍用在同一角色（次要文字），強烈建議合併成一個 |
| 深藍 | #102B42（深色按鈕）、#13243A（頁尾品牌字）、#182330（標題） | 三種近似深藍，建議收斂 |
| 金色 | #C8901F（logo／CTA／頁尾標題）、#F5A525（新手入門頁 CTA 與頂部色條）、#8A5A0F（金色連結文字） | #C8901F 與 #F5A525 是**不同色相明度**，同為「主要按鈕」卻不一致 → 品牌定調時需決定主 CTA 色 |
| 淡金背景 | #FEF1CF、#FDEFC4、#F7E5BE | 皆為新手入門頁 hero／chip，hero 為 #FEF5E3→#F7E5BE 漸層 |

## Accessibility Remap Decisions

Use this table when an authored value fails an accessibility requirement (for example WCAG AA contrast) and the shipped value must differ. Keep the authored value as its own `ref` token, map the `sys` role to the accessible value, and add an `a11y-remap` CSS comment linking the two. Downstream parity tooling reads these rows to classify the difference as `required-adaptation` instead of drift.

| Decision ID | Authored value (ref token) | Authored contrast | Accessible value (ref token) | Accessible contrast | Affected sys/comp tokens | Rationale | Confirmed by |
|---|---|---|---|---|---|---|---|

## Token Recalibration

Use this table when a higher-tier authoritative source (for example production Figma with Variables) arrives after tokens were finalized from lower-tier evidence. List every affected token, recommend `merge` (measured collapses into the authored value), `keep distinct`, or `re-authorize` (replace the token value with the authored value), and get developer adjudication before applying changes.

| Token | Current value (provenance) | Authoritative value (source) | Delta | Recommendation | Developer decision | Follow-up |
|---|---|---|---|---|---|---|

## Native Unit And Source Mapping

Use this table for native iOS/Android projects when source values use platform units or platform token/resource files.

| Canonical token | Native source token/resource | Platform/unit | Source file | Evidence screen/capture | Mapping or conversion note |
|---|---|---|---|---|---|

## Required Audit

- No component token references a reference token directly.
- No system token name includes component anatomy.
- No reference token name includes semantic roles.
- Reference color steps follow `100` lightest to `0` darkest.
- Near reference colors and numbers have a documented merge or keep-distinct decision that records both provenances; pairs involving an `authored` value default to keep distinct.
- Accessibility remaps keep the authored value as a `ref` token and carry an `a11y-remap` record; the shipped `sys` mapping points at the accessible value.
- Every background-like system color has a matching foreground pair.
- For vibe-coded projects, values found only in unused CSS, demo-only components, dead code, or blocked captures are not promoted to tokens unless a keep decision is recorded in `DESIGN_EVIDENCE_MAP.md`.
- For native app projects, values found only in source-only views, unused previews, blocked captures, or unverified resources are not promoted to tokens unless a keep decision is recorded in `DESIGN_EVIDENCE_MAP.md`.
