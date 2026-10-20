# Changelog

## 1.8.0

- Replace the control cluster with an app bar. **보기 · 편집 · 검토** is one mode switch; exactly one mode is pressed (`aria-pressed`). **검토** is the former **변경 사항** and is no longer hidden in a menu.
- Show the save state in the bar at all times: 변경 없음, 저장 안 됨, 저장 중…, 저장됨 · time, 사본 다운로드함, 저장 실패. A download is never shown as 저장됨, because it does not overwrite the original file. Failures stay until the next successful save or until dismissed with ×.
- Saving keeps edit mode. The saved file still opens in view mode with a clean status.
- Ask before leaving the page only when the browser backup has also failed and unsaved changes exist.
- Move 다른 이름으로 저장, 배포용 HTML 저장, HTML에 편집기 추가, 히스토리 and 인쇄 into a ⋯ menu at every width, with arrow, Home/End, Tab and Escape keys.
- In desktop view mode the bar floats and does not push the document. In edit and review modes it docks at the top with the toolbar or the comparison bar below it, so the two no longer overlap.
- Escape closes one layer at a time (history, menu, panel, review) and returns focus to the control that opened it. Escape in a text field, a select or the document text being edited leaves panels and review mode open and keeps the focus there. The history dialog traps Tab focus.
- At 560px and below the save state moves to a second row. Small UI text is at least 12px.
- Add `DocEditor.mode()` and `DocEditor.saveStatus()`.

## 1.7.0

- Add block deletion. **블록 선택** outlines the block at the caret and widens to the parent on a second press; **블록 삭제** removes it, with 되돌리기 in a toast and Ctrl/Cmd+Z right after the deletion.
- Deleting from a table cell removes the row, since dropping a single cell breaks the column alignment.
- The engine detaches the node instead of using the browser's delete, which merges blocks and strips the surviving block's class, and cannot remove a table row.

## 1.6.1

- Fix: documents converted by `tools/add-editor.html` from HTML without an existing `#doc-content` dropped every key press. The `display:contents` wrapper generates no box, so the editing root could not take focus (issue #1).
- The engine now gives the editing root a box only while editing, and restores `display:contents` for view mode, saved files, and read-only exports. Roots that are intentionally `flex` or `grid` are left untouched.
- Add real key input regression checks to `tests/attach-editor.js`. Assigning `textContent` cannot catch this class of bug.

## 1.6.0

- Add anchored notes with replies and resolution, stored in the file (`#doc-notes`) and shown in a side panel.
- Add change comparison against saved versions, the last save, or an HTML file, with per-change revert.
- Ask for an author name once per browser; record save provenance and history authors.
- Assign a document ID on the first save, record backup provenance, warn on mismatched backups, and keep the current body in history before restoring.
- Add `assets/doc-diff.js` (engine order: attach, diff, editor) and two UI blocks (`doc-notes-panel`, `doc-changes-bar`).

## 1.5.0

- Attach the editor to existing HTML and download an editable copy.
- Include a standalone attachment tool, duplicate-ID checks, and charset decoding.
- Provide a portable Agent Skills entrypoint and English/Korean documentation.

## 1.4.0

- Export read-only HTML without editor UI, history, or backup identity.
- Retain document content, styles, scripts, and inserted table presentation.

## 1.3.0

- Add a responsive toolbar, mobile more menu, and collapsible inspector.

## 1.2.0

- Remember supported file handles by document origin/path using IndexedDB.

## 1.1.0

- Add the option to dismiss a restore prompt and replace the backup with the current body.
- Improve autosave, history, and shared template generation.
