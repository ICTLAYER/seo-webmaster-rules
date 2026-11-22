# SEO Webmaster Rules

Use this Agent Skill to review a page, draft, link profile or site against the 77 factors in `SEO.docx`. Findings retain the original factor IDs and ratings, so an editor can trace each recommendation back to its source. The skill prioritizes actionable +3 and +2 opportunities and gives sustainable alternatives when a request involves a -2 or -3 technique.

The [reference](references/full-ranking-factors.md) preserves the historical descriptions, including outdated advice. The [instructions](SKILL.md) explain how to apply them today. For example, factor 3 records an old keyword-density target. A reviewer checks whether the copy conveys its topic naturally. E-E-A-T, helpful content, user experience and Core Web Vitals inform the review without receiving invented scores. [Google’s helpful content guidance](https://developers.google.com/search/docs/fundamentals/creating-helpful-content) · [Core Web Vitals](https://developers.google.com/search/docs/appearance/core-web-vitals)

## Install in a project

Copy the entire `seo-webmaster-rules` folder into the destination for your tool. Open the target project and start a new agent session. Keep `references/` beside `SKILL.md` so the relative link resolves. The package uses the [Agent Skills format](https://agentskills.io/specification) and requires no scripts or credentials.

| Tool | Project destination | Use |
| --- | --- | --- |
| [Cursor](https://cursor.com/docs/skills) | `.cursor/skills/` | Ask Agent for an SEO audit. |
| [Claude Code](https://code.claude.com/docs/en/skills) | `.claude/skills/` | Invoke `/seo-webmaster-rules`. |
| [Antigravity](https://antigravity.google/docs/skills) | `.agents/skills/` | Ask for a content SEO review. |
| [Codex](https://developers.openai.com/codex/skills) | `.agents/skills/` | Explicitly request `$seo-webmaster-rules`. |
| [Grok Build](https://docs.x.ai/build/features/skills-plugins-marketplaces) | `.grok/skills/` | Invoke `/seo-webmaster-rules`. |
| [Continue](https://github.com/continuedev/continue) | Project root, for manual context | Attach `seo-webmaster-rules/SKILL.md` and `seo-webmaster-rules/references/full-ranking-factors.md` to the chat. Ask Continue to apply the instructions to the supplied evidence. |

For example, run these commands from the target project in PowerShell for Codex or Antigravity. Set the source path to your downloaded skill folder.

```powershell
$source = 'C:\Downloads\seo-webmaster-rules'
New-Item -ItemType Directory -Force .agents/skills | Out-Null
Copy-Item -LiteralPath $source -Destination .agents/skills/ -Recurse
```

Confirm that `.agents/skills/seo-webmaster-rules/SKILL.md` exists. To check discovery and reference access together, ask “Use seo-webmaster-rules. Explain the difference between factors 29 and 32.” Expect the answer to identify unsolicited inbound links (0) and deliberate outbound links to link farms (-3).

## Use the skill

- **Product page** — “Review this title, description and image markup for a teak dining table. Give revised copy and cite the relevant factors.”
- **Technical audit** — “Use this crawl export and sitemap to find intended landing pages that crawlers cannot reach. Give a verification step for each fix.”
- **Link review** — “Review these referring domains and outbound links. Distinguish observed problems from checks that need more evidence.”

## Contribute

Open a pull request describing the problem, the affected factor IDs and an example of the expected review. For transcription fixes, include the corresponding source wording and rating. Preserve numbering 1–77 and the six source groups. For changes to modern advice or tool setup, cite the relevant official documentation. Test both an ordinary SEO request and a request for a prohibited tactic.

## License

See the [MIT License](LICENSE).
