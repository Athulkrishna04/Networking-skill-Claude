# Networking - a LinkedIn networking skill for Claude

A value-first playbook that turns Claude into a LinkedIn networking partner. It researches the people you want to reach, drafts personalized connection requests, DMs, and InMail, builds full outreach campaigns, and runs the follow-up, thank-you, and nurture sequences that compound cold outreach into warm introductions.

Built for three overlapping goals — **landing a role, general professional networking, and growing a personal brand** — it adapts its tone and its "ask" to whichever one you're working on.

---

## Why this exists

Great networking isn't luck or extroversion — it's a repeatable process built on one idea: **lead with value.** The people you want to reach are busy and ruthlessly filter their inbox, so every message has to cross an "I'll pay attention to you" threshold. This skill encodes the whole loop for doing that on LinkedIn: research → outreach → conversation → warm intro → nurture → build your own value.

---

## What's inside

```
networking/
├── SKILL.md                     # core: the value principle, 4 modes, the end-to-end loop,
│                                #   LinkedIn limits (300-char notes, DM/InMail), quality bar
└── references/
    ├── message-templates.md     # copy library: connection notes, DMs, cold InMail,
    │                            #   ask-for-intro, follow-ups, thank-yous, nurture, re-engagement
    └── playbook.md              # strategy: value framework, target tiers, research checklist,
                                 #   cadence, warm-intro engine, nurturing system, tracker, tone
```

The skill uses **progressive disclosure**: Claude loads only the `SKILL.md` summary by default and pulls in a reference file only when a task needs it, so it stays fast and focused.

---

## The four modes (they chain together)

| Mode | You ask for… | Claude does… |
|------|--------------|--------------|
| **A. Research + angle** | "Who is this person / what's my in?" | Profiles the target and surfaces 1–2 concrete personalization angles |
| **B. Draft a message** | "Write a connection note / DM / InMail" | Drafts a personalized, punchy, value-led message inside LinkedIn's limits |
| **C. Outreach plan** | "Build my networking campaign" | Maps targets into tiers, sets a cadence, lays out the sequence + a tracker |
| **D. Follow-up & nurture** | "They replied / we talked / it went cold" | Drafts follow-ups, thank-you notes, touchpoints, and the warm-intro ask |

Ask broadly ("help me network to land a BI role") and it runs the full loop, producing a plan with sample messages inside.

---

## Installation

> Skills **don't sync across surfaces** — if you want this on claude.ai *and* Claude Code *and* the API, add it to each separately.

### 1) claude.ai (web, desktop & mobile)

**Requirements:** a paid plan (Pro, Max, Team, or Enterprise) with **Code execution** turned on. Custom skills are per-user (not shared org-wide).

1. Download `networking.skill` from this repo (it's a zip archive of the `networking/` folder).
2. In Claude, open **Settings → Capabilities** (labeled **Features** in some versions) → **Upload skill**, and select the file. If the uploader only accepts `.zip`, rename `networking.skill` to `networking.zip` first.
3. Done. The skill is tied to **your account**, so it follows you across web, desktop, and the mobile app once uploaded, and works in both Claude Chat and Cowork.

*Shortcut:* if you open the `.skill` file inside a Claude chat, the file card shows a **Save skill** button that installs it directly.

Official steps: https://support.claude.com/en/articles/12512180-using-skills-in-claude

### 2) Claude Code (filesystem-based, no upload)

1. Clone this repo (or download the `networking/` folder).
2. Copy the folder into your skills directory:
   - **Personal** (all projects): `~/.claude/skills/networking/`
   - **Project-scoped** (shared with a repo when others clone it): `.claude/skills/networking/`
3. Start a new Claude Code session and run `/skills` to confirm it loaded. Invoke it with `/networking`, or just let Claude load it automatically when the task fits.

One-liner (personal install, run from the repo root):

```bash
mkdir -p ~/.claude/skills && cp -r networking ~/.claude/skills/
```

Official docs: https://code.claude.com/docs/en/skills

### 3) Claude API (Developer Platform)

Upload the skill as a zip via the Skills API (`/v1/skills`), then reference it by `skill_id` in the `container` parameter alongside the code execution tool. Requires beta headers: `skills-2025-10-02`, `code-execution-2025-08-25`, `files-api-2025-04-14`.

Official guide: https://platform.claude.com/docs/en/build-with-claude/skills-guide

### Security note

Install skills only from sources you trust, and skim the files first. This skill is **text-only** — no scripts, no code execution, no network calls — so a quick read of `SKILL.md` and the two reference files tells you everything it does.

---

## How to use it — 10 prompts that unlock its full potential

Each prompt targets a different capability. Replace the `[bracketed]` parts with your real details. They also chain: research a person, draft the message, build the campaign, then follow up.

1. **Find your angle (research).**
   *"Here's a hiring manager's LinkedIn profile: [paste bio or link]. What's my strongest personalization angle, and which value type should I lead with — financial, social, or emotional?"*

2. **Connection request, two angles (message).**
   *"Draft a LinkedIn connection request to [Name], a data-analytics recruiter at [Company]. Give me two angles, both under 300 characters."*

3. **Cold InMail that earns the open (message).**
   *"Write a cold InMail to a BI team lead at [Company] I'm not connected to. The first line has to hook them — no 'I hope this finds you well.'"*

4. **Full two-week campaign (plan).**
   *"Build me a 2-week LinkedIn outreach plan to land a [role] at product companies in [city/remote], with target tiers, a day-by-day cadence, sample messages, and a tracker."*

5. **Reach the decision-maker via warm intro (plan + message).**
   *"I've spoken with two analysts on [Company]'s team. Help me reach their hiring manager with a warm-intro-style message that references those conversations."*

6. **Follow-up that adds value, not noise (nurture).**
   *"This recruiter hasn't replied to my connection request from a week ago. Write a follow-up that adds value instead of just bumping the thread."*

7. **Thank-you + the ask for an introduction (nurture).**
   *"I just had a great 20-minute call with a senior analyst who offered to help. Write my thank-you note and a light ask for a warm introduction."*

8. **Keep your network warm (nurture).**
   *"Give me three no-ask touchpoint messages I can send over the next few months to stay on key contacts' radar without asking for anything."*

9. **Give-first brand building (brand).**
   *"Draft a genuine comment plus a no-ask DM to a data creator whose post on [topic] I admired, to start a real relationship — no pitch."*

10. **Audit and fix what's not working (coaching).**
    *"I sent 15 connection requests and got only one reply. Audit my approach and tell me exactly what to change."*

**Power move:** run them in sequence for one target — prompt 1 → 2 → (after they reply) 7 → 8 — and you've taken someone from stranger to warm relationship on a repeatable track.

---

## Tips for the best results

- **Feed it real details.** Paste the person's role, a recent post, or a mutual connection. The skill is only as specific as the input you give it.
- **Ask for variants** on important messages ("give me two angles") and pick the one that fits.
- **Say your goal.** "Job search," "peer networking," or "brand" changes the tone and the ask.
- **You send, not the bot.** The skill drafts; you review and send manually. That keeps you in control and protects your account — LinkedIn restricts automation, and bulk auto-connecting or auto-messaging risks getting an account limited.

---

## Credits

Distilled into a reusable Claude skill from a value-first networking framework (network = net worth: lead with value, personalized cold outreach, warm introductions, playing the long game, and building your own value). The implementation, templates, and playbook are original.

## License

Released under the MIT License — see [LICENSE](LICENSE). Use it, fork it, improve it.

## Contributing

Issues and PRs welcome — better templates, new scenarios (founders, career switchers, sales), and tone variants are all fair game.
