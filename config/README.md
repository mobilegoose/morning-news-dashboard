# Journal watch configuration

These files support the scheduled Morning News Dashboard publisher.

- `journal-watch.json` defines verified sources, access rules, staged retrieval, and article output.
- `medical-topics.json` defines priority topics, aliases, research/treatment signals, policy terms, scoring, and accuracy rules.
- `cal-conditions.txt` contains the current official SSA Compassionate Allowances condition names.
- `journal-seen.json` stores identifiers of articles already published so they are not repeated.

The automation prompt is the foundational instruction. It requires this workflow and points to these versioned files. The files hold long, changeable data so the prompt stays readable and token-efficient.

## Daily process

1. Use a rolling 72-hour PubMed record/entry-date window plus the latest/RSS pages for sources not promptly indexed.
2. Collect metadata only.
3. Deduplicate and score.
4. Read abstracts for no more than 15 candidates and full text for no more than 7.
5. Publish no more than 3 detailed articles plus 2 compact items, and omit the section when nothing qualifies.
6. Update `journal-seen.json` with published PMID, DOI, canonical URL, title, and date.

## Maintenance

- SSA's official list is canonical: https://www.ssa.gov/compassionateallowances/conditions.htm
- Recheck the CAL list monthly or after an SSA announcement.
- Recheck journal URLs and access status quarterly.
- Keep machine instructions in JSON. Keep explanatory prose here.

