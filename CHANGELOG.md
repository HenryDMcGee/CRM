# Changelog

## Unreleased

- LinkedIn autofill now looks people up with Crustdata first (name, current title and company from just the profile URL, in any browser tab; 1 Crustdata credit per profile found). A name that was only guessed from the URL is replaced with the real one. The Claude desktop app's browser and the screenshot option remain as fallbacks.
- LinkedIn autofill now works in any browser tab. When the page can't open LinkedIn itself (outside the Claude desktop app), it asks for a screenshot of the profile and Claude reads the name, title and company from it. Skipping still fills the name from the URL.

## Release 1 (v1.0.0) — October 28, 2026

The first release: the CRM as it runs today as a claude.ai artifact.

- Overview tab with pipeline and network tiles, an open next-steps list, and a network follow-up queue
- Applications tab with a pipeline-by-stage chart and a searchable, sortable table
- Network tab with contacts-by-company and outreach-cadence charts and an editable AG Grid of contacts (add, remove with confirmation, duplicate check, YYYY-MM-DD date check)
- LinkedIn autofill for a contact's name, title and company from their profile URL
- Live activity tab pulling application emails from Gmail, LinkedIn notifications, and UT Outlook recruiting mail, matched to the pipeline and contacts
- Light and dark themes
- No CRM data is included in the repo
