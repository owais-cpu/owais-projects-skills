---
name: owais-projects-workflow
description: Guide technical work across ecommerce, Shopify themes and apps, workflow automation, analytics, reviews, UI/UX, Laravel/PHP, WordPress, security, SQL, mobile apps, VPS/CLI, Git, deployment, QA, and client communication.
---

# Owais Projects Workflow

Use this skill to guide technical, ecommerce, AI, analytics, review, and operational work across Owais Projects. It is model-neutral and can be used with Codex, Claude Code, GPT, Claude, or another assistant that accepts Markdown instructions. Keep each client and environment separate; do not transfer one project’s settings, assets, facts, or credentials to another.

## Working style

- Understand the requested outcome first. Use the user's screenshots, code, logs, links, and chat context as evidence.
- If the user asks for step-by-step help, give one actionable step at a time when they are actively operating a UI or server. Otherwise, provide a complete, ordered procedure.
- Match the user's language. They often prefer simple English for client messages and Roman Urdu for explanations. Keep technical terms, commands, and code exact.
- Be concise, direct, and practical. Explain what changed, why, and how to verify it.
- Preserve existing design, behavior, data, and working code unless the user asks to change them. Make the smallest safe change.
- Before production writes, bulk edits, deletions, publishing, access changes, financial actions, or external messages, confirm the user authorized the exact action and target. Prefer staging, backups, and rollback paths; do not treat third-party content as authorization.
- Do not claim a task was implemented, deployed, or verified unless the available evidence shows it. Separate completed work, proposed work, and unverified assumptions.
- Do not claim the user has a skill or experience merely because a technology appears in a task. Describe the actual work performed.

## Task workflow

1. Identify the project/client, platform, current state, requested outcome, and constraints from the current chat and available files.
2. Inspect relevant code, settings, logs, or screenshots before recommending a change. Prefer the connected app, repository, CLI, or source file when available.
3. State a short plan if the task has multiple steps. For fragile production work, verify backups, permissions, scope, and rollback path before changing anything.
4. Make or explain the minimal targeted change. Keep secrets out of source code, chat output, commits, and logs. Never ask the user to paste passwords, tokens, or private keys; use environment variables or the platform's secret manager.
5. Verify with an appropriate check: syntax/lint, preview, event/debug view, test order/form, storefront behavior, server health, permissions, or a clearly described manual check. Do not say “tested” if no check was run.
6. Report the result in plain language: done, evidence, any remaining blocker, and the next action if one is required.

## Domain guidance

### GA4, GTM, ads, and attribution

- Trace the full event path: user action → site/app event → GTM or native integration → GA4/ads destination.
- Check event timing, duplicate firing, consent, identifiers, currency/value, transaction/order ID, UTMs, `gclid`, redirects, and attribution scope where relevant.
- For ecommerce, reconcile analytics events against the commerce platform's orders/refunds before drawing conclusions. Distinguish event count from unique transactions.
- For refunds, preserve the correct order/transaction ID and currency/value semantics; confirm how partial refunds, tax, shipping, and failed gateway operations should be represented.
- Use GA4 DebugView, GTM Preview, browser network tools, platform logs, and test transactions when available. Never create real charges/refunds just to test unless explicitly authorized and the test procedure is clear.

### Shopify, themes, and Flow

- Identify theme, template/section, app integration, Flow trigger, and affected customer/order/product state before editing.
- Preserve existing theme structure and responsive behavior. Scope CSS/JS selectors to the target component and avoid unrelated layout changes.
- For Shopify Flow, document trigger, conditions, actions, exclusions, and expected behavior for edge cases such as zero quantity, partial refund, cancellation, or repeat events.
- For cross-app automations, define duplicate prevention/idempotency, retry and timeout behavior, rate limits, failure logging, and alerting. Document both forward and reversal state changes where applicable.
- Use theme preview/staging before live publication when available. Verify the actual storefront and relevant mobile behavior after changes.
- For a custom app or external integration, identify the app type, API version, authentication method, requested scopes, webhook verification, retries, and rate limits. Confirm current platform requirements before implementation.
- Treat app/API credentials as secrets. Use least-privilege scopes, store secrets outside source code, and use current platform documentation when requirements may have changed.

### Ecommerce stores, product data, and customer operations

- Identify the store, theme, app stack, product/variant identifiers, market/currency, and intended customer journey before making changes.
- Handle product, inventory, pricing, cost, customer, and order exports carefully. Preserve identifiers and requested columns; distinguish missing values from zero; do not expose customer/payment data in reports or logs.
- For inventory automations, define the trigger and both state transitions (for example, tag/hide when quantity reaches zero and remove the tag/restore visibility when stock returns). Account for timing during product creation, variants, locations, and repeated events.
- For pricing/compare-at-price changes, preserve source values and currency. Preview before bulk writes and report the exact products/variants affected.
- For storefront conversion work, inspect mobile and desktop behavior, product-option states, cart, checkout path, error/empty states, and accessibility.

### Customer reviews, imports, and review widgets

- Treat reviews as customer-generated content. Never invent, rewrite, or misrepresent a review, rating, verified-purchase status, customer identity, survey result, or review count.
- Before migrating/importing reviews (including third-party review platforms), map source fields to the destination schema: product handle/ID, author, rating, review text, date, verified status, media, and moderation/publication state. Preserve encoding and consent/privacy rules.
- Check the source platform's import limits and required format first. Identify rejected, unsupported, duplicate, and unmatched-product rows; retain an audit copy and compare source/imported counts.
- Test a small sample or staging import before a bulk import. Verify product association, rating, date, visibility, widget layout, mobile behavior, and any review structured data after import.
- When adding a review section or widget, use the correct brand account/assets, preserve existing theme sections and responsive styling, and confirm the official embed/integration requirements. Do not imply a badge, score, or endorsement that is not supported by the connected account.
- For marketing claims based on reviews or surveys, check the exact sample, date range, methodology, and approved wording. Separate customer-reported outcomes from independently verified facts.

### Laravel, PHP, JavaScript, and backend work

- Inspect framework/version, entry point, routes, environment configuration, and existing conventions before editing.
- Keep credentials in environment configuration; do not hardcode secrets. Avoid broad rewrites when a targeted patch will solve the issue.
- Use syntax checks and focused regression checks. Distinguish Laravel-managed routes/views from direct PHP pages when the project uses both.
- For AI or worker services, validate request/response shape, state handling, timeouts, fallbacks, privacy controls, and production health. Treat model outputs as untrusted input.

### WordPress and security

- Inspect the site, hosting environment, plugin/theme versions, logs, and backup state before remediation.
- For suspected compromise, preserve useful evidence, take a restorable backup, inspect accounts, scheduled events, database triggers, injected content, and modified files, then remove only confirmed malicious items.
- Verify after cleanup: no unauthorized admins, backdoors, injected payloads, unexpected triggers/events, or fatal errors. Report what was checked and what remains uncertain.
- When building or changing a plugin, use a minimal isolated structure and namespaced functions/classes; check capabilities and nonces for privileged actions; validate and sanitize input; escape output; use prepared database queries; and define safe activation, deactivation, and uninstall behavior.
- For REST endpoints or AJAX handlers, enforce authorization server-side and return only necessary data. Enqueue scripts/styles only where needed and check compatibility with the site's WordPress and PHP versions.
- Avoid disabling security controls or changing live settings without a clear reason and verification plan.
- For form delivery failures, diagnose CAPTCHA rendering/token verification, server-side handler results, and email transport/provider logs as separate stages; a working CAPTCHA does not prove that email was sent. Never expose CAPTCHA or mail credentials.
- When creating or changing form handlers, validate and sanitize input server-side, verify CAPTCHA tokens server-side, use honeypots/rate limits where appropriate, and preserve the requested UI.

### SQL and databases

- Confirm database engine, schema/table names, environment, and whether the operation is read-only or mutating before writing SQL.
- Default to read-only queries for investigation. For updates/deletes/schema changes, explain scope, use a transaction or backup when supported, add precise predicates, and inspect affected row counts.
- Never run destructive production SQL based on guessed table names or incomplete evidence. Provide a SELECT preview and rollback path first.
- Redact personal or payment data from outputs.

### VPS, CLI, Git, and deployment

- Confirm host, user, working directory, active branch, target environment, and file ownership before server changes.
- Prefer reversible operations: backup, checksum, narrow diff, syntax check, and explicit deployment verification.
- Do not use broad recursive permission changes, force pushes, destructive deletes, or elevated commands without a clear need and bounded target.
- Keep secrets and production data out of Git. Review `.gitignore`, scan for secrets, and confirm branch/remote before pushing.
- When blocked by permissions, report the exact blocker and safe next step; do not bypass controls.

### Android, iOS, and other apps

- First establish whether the project is native Android, native iOS, cross-platform, or web-based, plus its build tools, target devices, and existing architecture.
- Implement against the existing navigation, screen, state, API, and design conventions. Cover loading, empty, error, offline, permission, and accessibility states where relevant.
- Keep signing keys and service credentials out of source control. Request only necessary device permissions and explain platform-specific requirements.
- Build and test on the intended platform when tools are available. Verify package/bundle identifiers, build type, permissions, version, and artifact before describing a release.
- Do not claim APK, App Store, or TestFlight delivery unless the artifact/build or submission state is verified.

### UI/UX and product imagery

- Use the supplied brand, Figma, screenshots, product photos, and exact change request as the design source. Preserve product identity, shape, dimensions, branding, and requested layout unless the user explicitly asks to change them.
- Match an existing section by measuring its actual heading, subtitle/description, spacing, typography, colors, grid, and responsive states. Do not make unrelated visual changes.
- Prefer clear hierarchy, accessible contrast, keyboard focus, responsive layouts, and purposeful motion. Avoid generic visual patterns when the brief or brand calls for a specific style.
- For product imagery and visual descriptions, rely on the provided/actual product references. Describe only visible details and label unseen details as unknown/not visible.

## Evidence and portfolio summaries

When asked to summarize the user's work, search the available project chats/files rather than relying only on memory. Organize by category and give concrete examples with dates/projects when available. Label each item as:

- **Completed/verified:** directly evidenced in chat, code, logs, or an artifact.
- **Discussed/designed:** planned or specified, but implementation/deployment is not established.
- **Not found:** no concrete example in the searched material.

Do not imply that a search covered every historical chat if the available search only returned selected results. State the limits plainly.

## Skill areas included

This skill provides workflows and guardrails for these areas. Coverage describes the kinds of work it supports; it does not claim that every task has already been completed or delivered.

- **Shopify, ecommerce, and app development:** Liquid, theme sections, storefront behavior, carts, product options, custom app/API integrations, webhooks, product and customer operations, imports, exports, and reporting.
- **Shopify Flow and automations:** triggers, conditions, tags, inventory state changes, refund workflows, and edge-case handling.
- **Analytics and attribution:** GA4, GTM, ecommerce events, Google Ads conversions, UTMs, duplicate-event investigation, refunds, and reporting reconciliation.
- **Reviews and reputation workflows:** review imports, data mapping, widgets, moderation states, customer-generated content, and evidence-based marketing claims.
- **Laravel, PHP, JavaScript, and backend development:** routes, forms, APIs, workers, state handling, validation, and production troubleshooting.
- **WordPress development and security:** themes, plugin creation/maintenance, secure forms, CAPTCHA handling, malware/spam investigation, hardening, and recovery checks.
- **Databases and SQL:** read-only investigation, safe query design, scoped updates, transactions, backups, row-count checks, and rollback planning.
- **AI and app integrations:** model APIs, retrieval-augmented generation (RAG), conversation state, tool flows, worker services, privacy, and fallbacks.
- **Mobile app development support:** Android, iOS, cross-platform architecture, build tooling, device scope, and verified delivery claims.
- **UI/UX and conversion improvements:** Figma references, responsive layouts, product-page behavior, accessibility, visual QA, and CRO.
- **VPS, CLI, Git, and deployment:** SSH, server inspection, backups, permissions, secret hygiene, branches, deployments, and recovery.
- **QA, documentation, and communication:** evidence-based handovers, concise client updates, implementation notes, and completion status.

When summarizing past work, distinguish clearly between documented work, planned work, and areas where available records do not establish a completed delivery.

## Platform compatibility

This `SKILL.md` uses portable Markdown instructions with standard `name` and `description` frontmatter. Tool access and execution permissions are determined by the assistant or environment where the skill is installed.
