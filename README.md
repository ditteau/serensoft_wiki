# Serensoft Wiki

Internal knowledge base for the Serensoft team — architecture, runbooks,
standards, and decisions for the Ditteau engagement.

---

## Quick Links

| I want to… | Start here |
|---|---|
| Onboard a new client school | [New Client Runbook](runbooks/new-client-onboarding.md) |
| Set up a school in Snowflake | [Snowflake New School Setup](runbooks/snowflake-new-school.md) |
| Understand the platform architecture | [Architecture Overview](architecture/overview.md) |
| Write or review a dbt model | [dbt Conventions](engineering-standards/dbt-conventions.md) |
| Log an architectural decision | [ADR Template](decisions/adr-template.md) |
| Look up a source system | [Source Systems → Jenzabar CX](source-systems/jenzabar-cx.md) |
| Review FERPA rules | [FERPA Quick Reference](governance/ferpa.md) |

---

## Active Clients

| School | SIS | schooltag | Status |
|---|---|---|---|
| Merrimack College | Jenzabar CX | `merrimack` | Archive go-live ~Apr 10, 2026 |
| Saint Anselm College | Workday Student + JCX legacy | `anselm` | Active |
| Springfield College | Ellucian Banner | `springfield` | Onboarding; SOC 2 in progress |
| Endicott College | Jenzabar CX | — | In pipeline |
| Demeau (demo) | — | `demeau` | Sales demo / testing |

---

## Team

| Handle | Name | Primary Area | Email | Slack |
|---|---|---|---|---|
| LVP | Laurie | Architecture & Strategic Planning | [laurie@serensoft.com](mailto:laurie@serensoft.com) | [DM](slack://user?team=T0YH9MKJR&id=U113UC6AZ) |
| WDT | Will | Systems & Security | [will@serensoft.com](mailto:will@serensoft.com) | [DM](slack://user?team=T0YH9MKJR&id=U0YGZ6BQU) |
| KKM | Kelly | Data Governance & Quality | [kelly@serensoft.com](mailto:kelly@serensoft.com) | [DM](slack://user?team=T0YH9MKJR&id=U02Q1KU9E3B) |
| RDT | Richard | Client Relations & Marketing | [rdt@serensoft.com](mailto:rdt@serensoft.com) | [DM](slack://user?team=T0YH9MKJR&id=U0YH9E2SK) |

---

## About this wiki

- **Source:** [github.com/ditteau/serensoft-wiki](https://github.com/ditteau/serensoft-wiki)
- Maintained by the whole team — found an error or gap? Open a PR.
- For questions about a specific area, ping the handle listed in the relevant doc.

---

## How-To: Working with Google Docs in this wiki

### Link to a Google Doc

The simplest and most reliable approach. Works for any doc regardless of sharing
settings — the reader just needs to have access to the doc itself.

Grab the URL from your browser while the doc is open (the full `/edit` URL is fine),
then use standard markdown link syntax:

```markdown
See the [Data Governance Charter](https://docs.google.com/document/d/YOUR_DOC_ID/edit)
for the full policy background.
```

**When to use this:** Living documents, meeting notes, anything that changes
regularly. A link is always current; an embed can feel stale.

---

### Embed a Google Doc inline (iframe)

Docsify allows raw HTML inside `.md` files, so you can drop a Google Doc directly
into a wiki page. This is handy for stable reference documents you want readable
without leaving the wiki.

**Step 1 — Get the embed URL**

Take the doc's normal URL and change `/edit` to `/preview`:

```
Before: https://docs.google.com/document/d/YOUR_DOC_ID/edit
After:  https://docs.google.com/document/d/YOUR_DOC_ID/preview
```

**Step 2 — Paste the iframe into your `.md` file**

```html
<iframe
  src="https://docs.google.com/document/d/YOUR_DOC_ID/preview"
  width="100%"
  height="600px"
  frameborder="0">
</iframe>
```

Adjust `height` to taste — `600px` works well for most reference docs; go higher
for longer ones you want fully visible without scrolling the iframe.

> ⚠️ **The doc must be shared as "Anyone with the link can view."** If it's
> restricted to specific people, wiki readers without access will see a blank
> white box — no error message, just silence. That's a confusing failure mode.
> Double-check sharing settings before embedding.

**When to use this:** Stable reference material — charters, policy docs, signed
agreements — where you want the content readable in context. Not a good fit for
docs that change often, since the embed doesn't signal when the source was last
updated.

---

### Embed a Google Sheet

Same pattern as a Doc — change `/edit` to `/preview` in the URL, then iframe it.
For sheets with multiple tabs, you can target a specific tab by appending
`&rm=minimal` to clean up the toolbar:

```html
<iframe
  src="https://docs.google.com/spreadsheets/d/YOUR_SHEET_ID/preview?rm=minimal"
  width="100%"
  height="500px"
  frameborder="0">
</iframe>
```

---

### Quick decision guide

| Situation | Use |
|---|---|
| Doc changes frequently (meeting notes, drafts) | Link |
| Doc is stable reference material | Embed |
| You want it findable via wiki search | Write it natively as `.md` |
| You're not sure of the sharing settings | Link — safer default |
