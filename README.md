# Dyslexia Steps — agent plugin

Phonics and sight word lists by grade from Dyslexia Steps: CVC words, word families, Dolch sight words, digraphs and vowel patterns, plus word lists in German, Spanish, French, Dutch and Brazilian Portuguese, with the source of every grade placement.

For any agent that speaks MCP or reads Agent Skills. Configuration only: one hosted MCP
server and one skill.

| | |
|---|---|
| MCP server | `https://mcp.dyslexiasteps.com/mcp` (Streamable HTTP, no sign-in, no key) |
| Skill | [`skills/phonics-word-lists`](skills/phonics-word-lists/SKILL.md) |
| Tools | 6, all read-only |
| Format | Agent Plugins v1 (`plugin.json` + `mcp.json` + `skills/`), plus Claude Code (`.claude-plugin/`, `.mcp.json`) |

## Install

```bash
# Skill only, for Claude Code, Cursor, Codex and 40+ other agents (skills.sh)
npx skills add Dyslexia-Steps/dyslexiasteps-agent-plugin

# Hermes Agent (skill + MCP server)
hermes plugins install Dyslexia-Steps/dyslexiasteps-agent-plugin
hermes plugins enable dyslexiasteps

# Claude Code, MCP server only
claude mcp add --transport http dyslexiasteps https://mcp.dyslexiasteps.com/mcp
```

Any other MCP client: add `https://mcp.dyslexiasteps.com/mcp` as a remote HTTP server.

## Tools

| Tool | What it returns |
|---|---|
| `list_word_lists` | Lists by language, grade (pre-k to grade 3) or section |
| `get_word_list` | Every word of one list, groups, grade range, page URL |
| `get_words_for_grade` | All English words for a grade, deduplicated |
| `find_words` | Words that start with, end with or contain a pattern |
| `get_placement_basis` | Where each grade placement comes from |
| `get_citation` | License, citation text, CSV/JSON downloads |

A grade is a typical guide, not a rule, and a list is practice material, not an assessment of any child.

## Disclosure

- Hosted-only connector with no local code. Every tool call, with its arguments, goes to
  `mcp.dyslexiasteps.com`. No account, key or personal data is needed or stored.
- All tools are read-only. No shell commands, no background processes, no telemetry
  from this package.
- The tool set is served by the remote server at runtime, so it is not covered by a pinned commit.

## License

Package: MIT. Word list compilation: CC BY 4.0; the Dolch words are public domain.
Source of the server: [dyslexiasteps-mcp](https://github.com/Dyslexia-Steps/dyslexiasteps-mcp).
Website: [dyslexiasteps.com](https://dyslexiasteps.com) · Docs: [docs.dyslexiasteps.com](https://docs.dyslexiasteps.com).
