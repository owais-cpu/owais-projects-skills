# Owais Projects Skills

A portable workflow skill for technical, ecommerce, AI, analytics, and operations work. The installable skill folder is `skills/owais-projects-workflow/`.

## Included skill areas

- **Shopify, ecommerce, and app development:** Liquid themes and sections, storefront behavior, carts and product options, custom app/API integrations, webhooks, store operations, product/customer data, imports, exports, and reports.
- **Shopify Flow and workflow automation:** triggers, conditions, inventory/tag state transitions, refund flows, duplicate prevention, retries, failure logging, and repeat-event safeguards.
- **GA4, GTM, and attribution:** ecommerce events, conversion tracking, UTMs, duplicate-event diagnosis, refund measurement, and platform reconciliation.
- **Reviews and reputation:** review data mapping/imports, widgets, moderation states, authentic customer claims, and review QA.
- **Laravel, PHP, JavaScript, and backend development:** routes, forms, APIs, worker services, validation, state handling, and troubleshooting.
- **WordPress development and security:** themes, plugin development/maintenance, secure forms, CAPTCHA validation, malware/spam investigation, hardening, and recovery checks.
- **SQL and database handling:** safe read-only queries, scoped writes, transactions, backups, affected-row checks, and rollback planning.
- **AI features and integrations:** model APIs, RAG, conversation state, tool flows, privacy, timeouts, and fallbacks.
- **Android, iOS, and cross-platform app development:** screens and state, APIs, device permissions, platform builds, QA, and verified release status.
- **UI/UX, Figma, and CRO:** responsive design, accessibility, product-page flows, visual comparison, and conversion-focused QA.
- **VPS, CLI, Git, and deployment:** SSH, server checks, backups, permissions, secret hygiene, deployment, and recovery.
- **QA and client communication:** evidence-based summaries, handovers, implementation notes, and accurate completion reporting.

This list describes the workflows the skill covers. It does not claim that every area has a verified completed project.

## Fast install

### Claude Code plugin (one-time setup)

Run these as **two separate commands** in Claude Code:

```text
/plugin marketplace add owais-cpu/owais-projects-skills
/plugin install owais-projects-workflow@owais-projects-skills
```

Then restart/reload Claude Code and invoke `/owais-projects-workflow:owais-projects-workflow` when you want it. In Claude Code Desktop, use **Plugins → Add plugin** and select the Owais Projects marketplace.

### Codex and other supported local coding agents

Install the skill globally across supported agents with the Skills CLI:

```bash
npx skills add owais-cpu/owais-projects-skills --skill owais-projects-workflow --agent '*' --global --yes
```

Or choose specific agents, for example:

```bash
npx skills add owais-cpu/owais-projects-skills --skill owais-projects-workflow --agent codex --agent claude-code --global
```

This CLI supports many local coding agents; available targets depend on its current agent list. To install only in the current project, omit `--global`. To update later, run `npx skills update owais-projects-workflow --global`.

### ChatGPT, Claude.ai, and other chat interfaces

These interfaces do not install files into a local agent folder with a shell command. Download `skills/owais-projects-workflow/SKILL.md` from this repository and add it through the platform’s Project/Skill settings. See the platform-specific instructions below.

## Install in Codex

Clone this public repository:

```bash
git clone https://github.com/owais-cpu/owais-projects-skills.git "$HOME/owais-projects-skills"
```

To refresh a copy you already cloned, run this command before copying the skill again:

```bash
git -C "$HOME/owais-projects-skills" pull
```

**Install for all your projects (user-level):**

```bash
mkdir -p "$HOME/.agents/skills/owais-projects-workflow"
cp "$HOME/owais-projects-skills/skills/owais-projects-workflow/SKILL.md" \
  "$HOME/.agents/skills/owais-projects-workflow/SKILL.md"
```

**Install in the current project:** run this from your project root after cloning:

```bash
mkdir -p .agents/skills/owais-projects-workflow
cp "$HOME/owais-projects-skills/skills/owais-projects-workflow/SKILL.md" \
  .agents/skills/owais-projects-workflow/SKILL.md
```

Codex discovers skills from either location.

## Install in Claude Code

Use the clone command above, then choose one install scope.

**Install for all your projects (user-level):**

```bash
mkdir -p "$HOME/.claude/skills/owais-projects-workflow"
cp "$HOME/owais-projects-skills/skills/owais-projects-workflow/SKILL.md" \
  "$HOME/.claude/skills/owais-projects-workflow/SKILL.md"
```

**Install in the current project:** run this from your project root:

```bash
mkdir -p .claude/skills/owais-projects-workflow
cp "$HOME/owais-projects-skills/skills/owais-projects-workflow/SKILL.md" \
  .claude/skills/owais-projects-workflow/SKILL.md
```

Claude Code discovers skills from either location.

## Install in Claude.ai or Claude Desktop

1. Clone the repository using the command above.
2. Create a ZIP with the skill folder at its root:

   ```bash
   cd "$HOME/owais-projects-skills/skills"
   zip -r "$HOME/owais-projects-workflow.zip" owais-projects-workflow
   ```

3. In Claude settings, open **Capabilities → Skills**, upload `owais-projects-workflow.zip`, and enable the skill. The Skills area and availability can vary by product version, account, and workspace settings.

## Use in ChatGPT

**Recommended: use a Project.** This keeps the full skill available without squeezing it into a short instruction field.

1. Create a ChatGPT Project and name it for this workflow.
2. Add `skills/owais-projects-workflow/SKILL.md` to the Project files.
3. In Project instructions, add:

   ```text
   For technical, ecommerce, automation, analytics, web, security, database, AI, or app-development tasks, consult the uploaded owais-projects-workflow SKILL.md and follow its workflow. Preserve existing behavior, protect secrets and customer data, and distinguish verified work from plans or assumptions. Do not claim a change was made or tested without evidence.
   ```

**Existing custom GPT:** if you have an editable GPT, add `SKILL.md` as Knowledge and put a short instruction in its Instructions field telling it to follow that file. Knowledge provides reference material; behavioral rules belong in Instructions. New custom GPT creation may be unavailable for personal accounts; editing an existing GPT depends on account/workspace eligibility. Use a ChatGPT Project for the full skill when GPT creation is unavailable.

**Custom Instructions:** the full skill is about 14,000 characters, so it will not fit in ChatGPT Plus's 5,000-character Custom Instructions limit. Use a Project file for the full skill; use Custom Instructions only for a short summary.

There is no supported shell command that installs a skill directly into ChatGPT Projects or GPT Builder; add the file through the ChatGPT UI.

## Folder layout

```text
skills/
└── owais-projects-workflow/
    └── SKILL.md
```

## License and reuse

The current version is under the [Owais Projects Limited-Use License](LICENSE). It permits unmodified personal or internal business use, including uploading an unmodified copy to an AI assistant for those purposes, and using the workflow to produce your own work. It does not permit modifying or redistributing the skill files.

**Earlier-version notice:** A previous public commit contained an MIT license. This replacement does not revoke permissions already granted for that earlier version or copies made under it. The current version on the main branch uses the limited-use terms above.
