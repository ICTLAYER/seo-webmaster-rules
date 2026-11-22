# SEO Webmaster Rules

Use this agent skill to audit a website, review a link profile, or revise a page before publication. Each finding connects a specific piece of evidence to a numbered rule, a recommended change, and a way to verify the result.

## SEO Basic Rules

The [SEO Basic Rules](references/full-ranking-factors.md) cover 77 historical SEO factors in six groups. The factor IDs and signed ratings let editors and developers trace a recommendation back to its source. The ratings express the original checklist’s priorities. Adding them together cannot predict a page’s search position.

| Factor IDs | Topic | Example review question |
| --- | --- | --- |
| 1–16 | Keywords | Do the title, headings, and opening paragraph make the page’s topic clear to a reader? |
| 17–34 | Internal, inbound, and outbound links | Does each internal link describe its destination? Which links can the site owner change? |
| 35–38 | Meta tags | Does the meta description accurately summarize this page? |
| 39–51 | Content | What original information does this page add, and does it answer the visitor’s question? |
| 52–58 | Scripts and media | Can visitors read the main content and understand informative images and videos? |
| 59–77 | Domains, URLs, and site management | Do intended landing pages load, appear in the sitemap, and remain reachable after redirects? |

The [review instructions](SKILL.md) explain how to apply historical rules to a current audit. For example, factor 3 records a keyword-density target. A reviewer checks whether the copy explains the topic clearly and flags repetition that makes it harder to read. The skill also considers content quality, mobile usability, and Core Web Vitals when evidence is available. See Google’s guidance on [helpful content](https://developers.google.com/search/docs/fundamentals/creating-helpful-content) and [Core Web Vitals](https://developers.google.com/search/docs/appearance/core-web-vitals).

## Install in a project

From your target project, run the Skills CLI and choose your agent when prompted.

```sh
npx skills add ICTLAYER/seo-webmaster-rules
```

For a project-local Codex installation, run `npx skills add ICTLAYER/seo-webmaster-rules --skill seo-webmaster-rules --agent codex -y`.

### Manual installation

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

## Request a review

Provide the audience, the page or site section, and the evidence you want reviewed. For a copy review, paste the draft or HTML. For a technical audit, attach the relevant crawl export, sitemap, or performance report. The review identifies which findings the evidence supports and what still needs checking.

- **Product page** — “Review this title, description and image markup for a teak dining table. Give revised copy and cite the relevant factors.”
- **Technical audit** — “Use this crawl export and sitemap to find intended landing pages that crawlers cannot reach. Give a verification step for each fix.”
- **Link review** — “Review these referring domains and outbound links. Distinguish observed problems from checks that need more evidence.”

## Contribute

Open a pull request describing the problem, the affected factor IDs and an example of the expected review. For transcription fixes, include the corresponding source wording and rating. Preserve numbering 1–77 and the six source groups. For changes to modern advice or tool setup, cite the relevant official documentation. Test both an ordinary SEO request and a request for a prohibited tactic.

## Credits

Project credit goes to [ICT Layer](https://www.ictlayer.com/).

## License

See the [MIT License](LICENSE).
