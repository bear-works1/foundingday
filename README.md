# 🚀 Founder Blueprint

A kid-friendly web app for a **Founders Day workshop**. Students build a company
step by step — brand, product/service, customer, competition, money model,
marketing, sales pitch, and next steps — with an **AI mentor** giving feedback
along the way. Finishing a step earns confetti and level-ups, and everything
exports as a one-page **business plan** PDF. A **teacher dashboard** shows every
student's progress live.

## Files
- `index.html` — the student app
- `dashboard.html` — the teacher dashboard

## Backend (already set up)
This app is wired to a Supabase project called **Founder-Blueprint**:
- **Table** `blueprints` — stores each student's answers, AI feedback, and progress
- **Edge Function** `ai` — safely proxies the Anthropic (Claude) API

The app already contains the project URL and the **publishable (anon) key**, which
is safe to expose — it only allows access to the `blueprints` table.

## ⚙️ One step to switch the AI on
Add your Anthropic API key as a Supabase **secret** named `ANTHROPIC_API_KEY`:

- **Dashboard:** Supabase → your project → *Edge Functions* → *Secrets* → add
  `ANTHROPIC_API_KEY` = your key
- **or CLI:** `supabase secrets set ANTHROPIC_API_KEY=sk-ant-...`

Then set a **monthly spending limit** in the Anthropic Console (Billing → Limits)
so a classroom can't run up a bill. Until the key is added, the AI politely says
it isn't switched on yet — everything else still works.

Your API key is **never** stored in these files — only as a Supabase secret.

## ▶️ Run it
- **Locally:** just open `index.html` in a browser.
- **Hosted (recommended):** enable **GitHub Pages** — repo *Settings → Pages →
  Deploy from a branch → `main` / `root`*. The app will live at
  `https://<user>.github.io/<repo>/` and the dashboard at `.../dashboard.html`.

## 🧑‍🏫 Using it in class
1. Pick a **class code** (e.g. `FOUNDERS7`) and share it with students.
2. Students open the app, enter the class code + their name, and start building.
3. You open `dashboard.html`, enter the same class code, and watch progress live
   (it auto-refreshes; click any student to see their full blueprint + AI chats).

## 🔒 Notes on privacy
- Business ideas are non-sensitive; anyone with the class code can view that
  class's blueprints. That's fine for a classroom. Add Supabase Auth later if you
  want stricter access.
- Keep student names to first name + last initial.

## License
MIT — see `LICENSE`.
