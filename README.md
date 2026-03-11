# Atlas Intelligence Programme

Canonical source of truth for the Atlas Strategic Consultants intelligence programme.

This repo is read by Claude (Anthropic) across all projects and surfaces via `web_fetch` against raw GitHub URLs. It replaces the previous approach of duplicating programme content across multiple Project Instructions fields and User Preferences.

## Structure

| File | Purpose |
|------|---------|
| `programme.md` | Master index — identity, rules, pillar summaries, active projects. This is the primary file Claude fetches. |
| `pillar1.md` | Pillar 1 full detail — Global Knowledge Repositories |
| `pillar2.md` | Pillar 2 full detail — Quantitative Trading and Algorithmic Markets |
| `pillar3.md` | Pillar 3 full detail — Penetration Testing and OSINT |
| `pillar4.md` | Pillar 4 full detail — AI-Driven Mathematical Problem Solving |
| `pillar5.md` | Pillar 5 full detail — AI Reliability and Trustworthiness |
| `pillar6.md` | Pillar 6 full detail — Geospatial Intelligence and Global Monitoring |

## How it works

1. User Preferences (global across all Claude surfaces) contains a compact directive pointing to this repo
2. On first relevant message in any session, Claude fetches `programme.md` via raw GitHub URL
3. If deeper pillar context is needed, Claude fetches the specific `pillarN.md` file
4. Full .docx formatted briefs remain in Google Drive → Pillars/ as archival copies

## Updating

Edit files in this repo. Push. Every future Claude session reads the updated version. No need to update Project Instructions fields or User Preferences.

## Owner

Gary Stewart, Lead Consultant, Atlas Strategic Consultants, Caves Beach NSW.
