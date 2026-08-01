# Task for Antigravity Agent: Connect Mail, Finish Testing, Push to GitHub

Paste this into a new Antigravity task in the same project (`D:\rk\girlfriend-day-website`).
This covers three things: wiring up a mail tool so future tasks can actually send email,
one last full regression pass, and pushing the project to GitHub.

---

## Part 1 — Connect a mail tool

You reported earlier that no mail-sending tool is connected in this environment. Before
doing anything else:

1. Check whatever your MCP/tool-connector settings screen is called in this Antigravity
   install (usually under Settings → Connectors, Integrations, or MCP Servers).
2. If a Gmail or generic SMTP/email MCP server is available to add, connect it and
   authenticate with the account I'll use for sending (I'll complete any OAuth prompt
   myself when it appears — don't try to guess or enter credentials on my behalf).
3. If nothing like that is available in this Antigravity build, stop and tell me plainly
   that mail can't be connected here rather than improvising a workaround (e.g. don't try
   to shell out to a raw SMTP script with hardcoded credentials — I haven't given you any,
   and I don't want them stored in this project).
4. Once connected, send a short test email to **noa660219@gmail.com** with subject
   `"Antigravity mail test"` and a one-line body, just to confirm it actually works before
   relying on it for the real completion notifications later.

## Part 2 — Final regression pass

Before pushing anything public, re-run the full click-through one more time (envelope →
question → NO-button dodge → YES → certificate → bouquet → phone-mirror → photo timeline
→ reasons → hug → closing → kiss button → the new "Tum Se Hi" song link) and confirm:

- Zero console errors (the one expected/harmless Google Fonts block in sandboxed
  environments aside).
- The song link-out and the ambient play/pause button both still work independently.
- Mobile viewport (~390px) and `prefers-reduced-motion` still both pass as before.

Only proceed to Part 3 if this pass is clean. If anything's broken, fix it with the
smallest targeted edit and re-test before continuing.

## Part 3 — Push to GitHub

The target repository is **https://github.com/cshfigma216-tech/g2.git** (empty repo,
shown in the "quick setup" screen — no README/LICENSE/.gitignore added yet).

1. In the project root (`D:\rk\girlfriend-day-website`), initialize git if it isn't
   already:
   ```
   git init
   git branch -M main
   ```
2. Add a `.gitignore` with at least:
   ```
   .DS_Store
   Thumbs.db
   node_modules/
   ```
3. Add a short `README.md` describing the project in 3-4 lines (what it is: an
   interactive single-file "Girlfriend Day" web experience — envelope, proposal, bouquet,
   phone-mirror mockup, photo timeline, reasons cards, closing — and how to run it locally,
   e.g. `python -m http.server 8000`).
4. Stage and commit:
   ```
   git add .
   git commit -m "Initial commit: girlfriend day interactive website"
   ```
5. Connect the remote and push:
   ```
   git remote add origin https://github.com/cshfigma216-tech/g2.git
   git push -u origin main
   ```
6. If the push is rejected because the remote already has commits (e.g. GitHub
   auto-created something), don't force-push — stop and tell me what happened so I can
   decide how to reconcile it.
7. Confirm the push succeeded by checking the remote (e.g. `git log origin/main` or
   equivalent) and report the final repo URL back to me.

## Guardrails

- Don't commit any real credentials, API keys, or OAuth tokens into the repo — if the
  mail connector setup in Part 1 generates any local credential files, make sure they're
  in `.gitignore` before you ever run `git add .`.
- Don't make this repo public/private decision yourself if it's ambiguous — if the repo
  visibility isn't already set from the screenshot's context, ask me first.
- Keep the site itself untouched in this task — Parts 1–3 are infra/process only, no
  further edits to `index.html` unless Part 2 turns up a real bug.

## Done when

- Mail tool is connected and the test email arrived at noa660219@gmail.com (or you've told
  me plainly it isn't possible in this environment).
- Full regression pass reported clean.
- The repo at https://github.com/cshfigma216-tech/g2.git shows the pushed commit, and
  you've confirmed the URL back to me.
