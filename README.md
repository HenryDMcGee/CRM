# Internship CRM

My recruiting CRM for Summer 2027 MBA product management internships. It tracks applications, networking contacts, follow-ups and live recruiting email in one page.

Release 1 is the CRM exactly as it runs today: a single-page app hosted as a claude.ai artifact, at [claude.ai/artifact/6JLKstwRaKPuGY47LfshiD](https://claude.ai/artifact/6JLKstwRaKPuGY47LfshiD).

## What it does

| Tab | What's on it |
| --- | --- |
| Overview | Six tiles (applications, in interview, applied, rejected, contacts, follow-ups), the open next steps across the pipeline, and a follow-up queue of contacts ordered by who has waited longest |
| Applications | A pipeline-by-stage chart and a searchable, sortable table of every role |
| Network | Contacts-by-company and outreach-cadence charts, plus an editable contacts grid (AG Grid) with add, remove and LinkedIn autofill |
| Live activity | Application emails from Gmail, LinkedIn notifications, and recruiting mail from my UT Outlook inbox, matched to the pipeline and contacts where possible |

Other details:

- Statuses run Researching, Watching, Networking, Materials ready, Applied, Interview, Offer, Rejected.
- Grid edits save as you go. Dates are checked as YYYY-MM-DD, removing a contact asks for confirmation first, and new rows are checked for duplicate names.
- Light and dark themes follow the system setting.

## How it runs

`index.html` is the whole app: markup, styles and script. It depends on:

- **d3 7.8.5** and **AG Grid Community 33.3.2** from public CDNs
- **The claude.ai artifact runtime**, which provides:
  - the page's database, with `contacts` and `applications` collections
  - the Gmail and Microsoft 365 connectors for the live activity feeds
  - the Crustdata connector for LinkedIn autofill (profile URL → name, title, company), with the Claude desktop app's browser or a profile screenshot as fallbacks

Because of that runtime, opening `index.html` straight from disk shows the layout without data. It runs fully inside claude.ai.

## Data

**No CRM data is in this repo.** Contacts and applications hold recruiter emails and personal notes, and they live only in the artifact's database. The repo holds code only.

| Collection | Fields |
| --- | --- |
| contacts | name, email, phone, linkedin, title, company, website, how_met, todo, last_contact, format, followup, notes, created |
| applications | company, role, location, status, applied, updated, next_step, notes |

## Roadmap

The deployment plan moves the CRM to my own stack, deployed on Cloudflare the same way as internship-watch:

1. **Foundation:** D1 schema, REST API, seed migration, CI
2. **Frontend port:** one codebase that runs as the artifact or the site
3. **Ship and secure:** crm.mcgeehenry.com behind Cloudflare Access
4. **Email feeds:** Gmail and Outlook workers on an hourly cache
5. **Enrichment and Claude loop:** LinkedIn lookup and chat-driven updates

See [CHANGELOG.md](CHANGELOG.md) for releases.
