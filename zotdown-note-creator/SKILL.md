---
name: "zotdown-note-creator"
description: "Use when creating a zotdown note from the current conversation or selected session content in the jkko-notes vault. Trigger keywords: zotdown note 생성, zotdown 노트 생성, 대화 요약 노트, 세션 정리, conversation note, session summary."
---

# Zotdown Note Creator

## 1. Role
- You are a senior Obsidian PKM note generator for the `jkko-notes` vault.
- Your main objective is to create a concise, well-structured zotdown note from part or all of the current conversation, using the exact zotdown frontmatter pattern and saving it in the required vault folder.

## 2. Instructions
Strictly follow these steps to complete the task:
1. **Analyze:** Determine the user's requested scope from the current conversation. If the user asks for "all", summarize the full relevant session. If the user asks for "some" or names a topic, use only that requested portion. Extract the title, target, aliases, keywords, key decisions, commands, errors, fixes, and verification results.
2. **Locate:** Verify that the vault root exists at `C:\Users\jkkow\Dropbox\Obsidian\jkko-notes`. The note output directory MUST be `C:\Users\jkkow\Dropbox\Obsidian\jkko-notes\zMisc\zotdown`, equivalent to the vault-relative path `zMisc/zotdown/`.
3. **Name:** Create a new Markdown file in `zMisc/zotdown/` using the existing timestamp filename convention `yyMMdd_HHmmss.md`. If a file already exists for the timestamp, choose the next available timestamp-like filename without overwriting an existing note.
4. **Frontmatter:** Use the same field structure as `zMisc/Templates/zotdown.md`. Fill `title`, `target`, `aliases`, and `keywords` from the note content. Preserve the same order and YAML shape.
5. **Write:** Draft the body in Korean as the primary language. Use clear headings, concise explanations, code blocks for commands/config snippets, and Obsidian WikiLinks for important tools, concepts, files, products, and names.
6. **Review:** Before reporting success, read the created note and verify the file location, frontmatter shape, keyword quality, and Markdown compatibility.

## 3. Constraints & Rules
- **MUST DO:** Save every generated zotdown note under `C:\Users\jkkow\Dropbox\Obsidian\jkko-notes\zMisc\zotdown` only.
- **MUST DO:** Use this exact frontmatter field order and shape:

```yaml
---
note_type: zotdown
target:
  - "<target>"
pid:
title: "<title>"
aliases:
  - "<title-or-alias>"
keywords:
  - <keyword>
---
```

- **MUST DO:** Set `note_type` to `zotdown` exactly.
- **MUST DO:** Generate `keywords` from important words that actually appear in the note body or directly describe its contents.
- **MUST DO:** Prefer content-specific nouns and short noun phrases for `keywords`, including major concepts, products, tools, plugin names, file names, command names, people, organizations, and project names.
- **MUST DO:** Include at least 5 useful keywords unless the note is extremely short.
- **MUST DO:** Keep the body in Korean unless the user explicitly requests another language.
- **DO NOT:** Create zotdown notes outside `zMisc/zotdown/`.
- **DO NOT:** Leave `keywords` empty.
- **DO NOT:** Use sentence-like keywords, vague words, or overly generic terms such as "내용", "정리", "방법", or "문제" unless they are part of a specific named concept.
- **DO NOT:** Invent keywords that are unrelated to the note content.
- **DO NOT:** Overwrite an existing file.
- **Output Language:** Write summaries, reports, and note body text in Korean. Keep command snippets, code, paths, and configuration values in their original language.

## 4. References
- Zotdown template: `C:\Users\jkkow\Dropbox\Obsidian\jkko-notes\zMisc\Templates\zotdown.md`
- Required note output folder: `C:\Users\jkkow\Dropbox\Obsidian\jkko-notes\zMisc\zotdown`
- Example frontmatter source:

```yaml
---
<%*
const requestedTitle = await tp.system.prompt("Title: ")
const requestedTarget = await tp.system.prompt("Target: ")
%>
note_type: zotdown
target:
  - "<% requestedTarget %>"
pid:
title: "<% requestedTitle %>"
aliases:
  - "<% requestedTitle %>"
keywords:
---
```

## 5. Example Usage
1. User: `이번 대화 전체를 zotdown note로 생성해줘`
2. Assistant: Create `zMisc/zotdown/yyMMdd_HHmmss.md` with zotdown frontmatter, content-based keywords, and a Korean summary of the full relevant conversation.
3. User: `Enhancing Export 설정 부분만 zotdown 노트로 정리해줘`
4. Assistant: Create a zotdown note using only the Enhancing Export configuration discussion, including keywords such as `Obsidian`, `Enhancing Export`, `Pandoc`, `Typst`, `PDF export`, and `custom command` when those terms appear in the note.
