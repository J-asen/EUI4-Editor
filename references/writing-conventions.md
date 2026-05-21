# Writing Conventions

## Standard Document Shape

Use this structure unless the latest existing main document shows a newer pattern:

```markdown
EUI Design System

<br>

# 场景中文名

开篇说明这个页面模板是什么、解决什么问题、通常服务于什么任务。

---

<br>

## 如何设计

## 推荐组合

<br>

---

<br>

## 信息结构 / 关系说明 / 页面结构
## 模板分组章节

<br>

---

<br>

## 与其他场景的关系

<br>

---

<br>

## Do & Don’t
```

Keep the section names close to the scenario language. Examples: `页面空间结构`, `导航方式`, `内容布局`, `容器类型`, `子记录维护方式`, `审批页面类型`, `选择页面类型`, `操作结果状态`, `异常与不可用状态`.

Use the title-introduction divider directly after the opening intro, without a leading `<br>`:

```markdown
---

<br>
```

For other major section groups, the divider block must be:

```markdown
<br>

---

<br>
```

Do not place a divider between `## 如何设计` and `## 推荐组合`; they are a continuous explanatory pair. If a document has other closely related explanatory sections, keep them continuous unless the latest family document clearly separates them.

## Template Block Layout

Use HTML for template blocks so Markdown preview keeps a stable left-text/right-image layout.

```html
### X01 - 模板名称

<table width="100%">
  <tr>
    <td width="60%" valign="top">
      <p>简介。说明模板是什么，承载什么用户任务。</p>
      <p><strong>何时使用</strong></p>
      <p>说明触发条件、典型场景和选择判断。</p>
      <p><strong>使用建议</strong></p>
      <ul>
        <li>建议一。</li>
        <li>建议二。</li>
        <li>建议三。</li>
      </ul>
    </td>
    <td width="40%" valign="top">
      <img src="./images/{scenario}/图片名.png" alt="模板名称" width="100%">
    </td>
  </tr>
</table>
```

Do not place Markdown tables or bare Markdown paragraphs inside an HTML `<td>`. If a table must appear inside an HTML section, write it as HTML with `<table>`, `<thead>`, `<tbody>`, `<tr>`, `<th>`, and `<td>`.

When multiple template blocks appear consecutively, insert one standalone `<br>` between blocks so the rendered preview has enough breathing room:

```markdown
</table>

<br>

### X02 - 模板名称
```

Do not let a completed template table flow directly into the next template heading. The sequence `</table>` followed by `###` without an intervening `<br>` is invalid for generated template introductions.

## Naming and Numbering

Prefer short single-letter prefixes in template titles. Use the latest existing document if it differs.

- `list-page`: page structure `Lxx`, table/body variants `Txx`.
- `form-page`: structure `Lxx`, navigation `Nxx`, layout `Pxx`.
- `detail-page`: use the established current document naming and visual-style terminology.
- `dialog`: `Dxx`.
- `subform`: `Sxx`.
- `audit-page`: `Axx`.
- `select-page`: `Xxx` to avoid conflict with subform `Sxx`.
- `state-page`: keep source grouping, `Rxx` for results before `Exx` for exception/unavailable states when requested.

Use titles such as `X01 - 数据表式`, not unnumbered headings.

## Image Rules

- Copy scenario images into `页面模板介绍-v0.0.7/images/{scenario}/`.
- Reference copied images, not source images.
- Use short relative paths in Markdown.
- Confirm each referenced image exists.
- Do not leave broken links, placeholder images, or remote temporary image URLs.

## Versioning Rules

- Root output versioning is mandatory: each scenario keeps only its latest Markdown version in `页面模板介绍-v0.0.7`.
- Historical versions must be stored in `页面模板介绍-v0.0.7/历史版本`.
- Do not overwrite an existing root document when revising. Create the next version instead, such as `form-page-v2.md`, `form-page-v3.md`, and so on.
- When creating a revised version, read the current root latest version first, create the next version in the root, validate it, then move only the previous root version for that same scenario into `历史版本`.
- If `历史版本` does not exist, create it. If a same-name file already exists in `历史版本`, stop and ask the user; do not overwrite, rename silently, or delete anything.
- Never batch move or batch clean old files. Version archiving must operate on one exact previous root file for the scenario being revised.
- Preserve historical versions. Do not modify, delete, or move files already inside `历史版本` unless the user explicitly asks to restore or reorganize them.
- If the user says a current version has been promoted to the root, read that root version before continuing and use its version number to calculate the next version.

## Terminology Rules

- Generated user-facing docs must use `EUI4`.
- Do not write `EUI FlowKit` in generated template introductions.
- For form/detail visual styles, use the user-confirmed names if relevant: `现代分组式` and `经典表格式`.
- Explain relationships in reader terms: editing/read-only state, parent/child records, candidate/selected objects, result/recovery path.

## Forbidden Internal Content

Remove or translate these into user-facing guidance:

- AI scheduling or agent dispatch language.
- `执行脚本` sections.
- `D2D`, `D2C`, production handoff internals.
- `checklist`, `输出合同`, internal contracts.
- Raw data/interface models unless the user explicitly asks for implementation documentation.
- Sensitive technical internals such as database names, service names, permission codes, stack traces, or hidden role rules.

## Scenario-Specific Emphasis

- `list-page`: separate page-space structure from list body variants; explain scan, filter, table/card/tree use.
- `form-page`: describe edit-state object pages; structure, navigation, layout, and visual style can be reused by detail pages.
- `detail-page`: describe read-only state of the same object-page family; compare with form pages without implying a separate architecture.
- `dialog`: define as a temporary task container, not an independent page type; connect content back to form/detail/list/select/state.
- `subform`: define as multi-child-record capture/maintenance; clarify parent object, batch, source task, or submission context.
- `audit-page`: define as business content + process context + approval actions; distinguish flow and split-screen review needs.
- `select-page`: define as candidate selection + confirmation + parent-task backfill; distinguish from data management lists.
- `state-page`: define as result or blocking state; introduce operation results before exception/unavailable states when requested.

## Validation Checklist

Before finishing, check:

- The new document exists at the requested path.
- Image files were copied and every `src="..."` path resolves.
- Template headings match the required count and order.
- Consecutive template blocks have one standalone `<br>` between the previous `</table>` and the next `###` heading.
- The doc uses `EUI4`, not `EUI FlowKit`.
- Forbidden internal terms do not appear.
- Existing unrelated documents were not modified.
- The output root contains only the latest version for the scenario being revised.
- The previous root version, if there was one, was archived under `历史版本` without overwriting any historical file.
- The final response names the created/updated files and any validation limitation.
