---
name: hubspot-prompts
description: Find, adapt, or create HubSpot prompts for sales, marketing, commerce, service, customer success, and RevOps. Supports guided selection, smart matching from natural language, and fully custom prompts. Use when the user mentions hubspot prompts, CRM prompts, sales prompts, marketing prompts, service prompts, commerce prompts, revops prompts, deal analysis, lead generation, pipeline, or tickets.
---

# HubSpot Prompts Skill

A library of 81 expert HubSpot prompts organized by role and use case, with smart matching and freeform flexibility.

Help users find, adapt, or create HubSpot prompts for sales, marketing, commerce, service, customer success, and RevOps workflows. Supports guided selection, smart matching from natural language, and fully custom prompts enhanced with HubSpot best practices.

## Trigger Keywords

hubspot, hubspot prompts, crm prompts, sales prompts, marketing prompts, service prompts, commerce prompts, revops prompts, customer success prompts, deal analysis, lead generation, pipeline, tickets

---

## How This Skill Works

You have a library of 81 HubSpot prompts organized into 6 roles and 22 use cases. Your job is to help users find the right prompt, adapt it to their needs, or write a custom one — whichever gets them the best result fastest.

### Step 1: Determine the Mode

Read what the user provided alongside the `/hubspot-prompts` invocation and choose a mode:

| User input | Mode | What to do |
|---|---|---|
| Nothing, or just the skill name | **Guided** | Ask the user to pick a role, then a use case |
| A role keyword like "sales", "marketing", "service" | **Filtered** | Show use cases within that role and ask them to pick |
| A descriptive request like "I need to find deals going cold" | **Smart Match** | Scan the index, find the best-matching prompt(s), and present them |
| Explicitly says "custom" or "my own prompt" or their request doesn't match any template | **Freeform** | Help them write a prompt from scratch using HubSpot best practices |

### Step 2: Execute the Mode

---

#### MODE 1: Guided Selection

Use the AskUserQuestion tool to present choices. First ask for the role:

**Roles available:**
- **Sales** (31 prompts) — deals, pipeline, prospecting, objection handling, forecasting
- **Marketing** (15 prompts) — campaigns, lead nurture, segmentation, content, analytics
- **Commerce** (18 prompts) — orders, invoices, carts, subscriptions, product performance
- **Service** (9 prompts) — tickets, SLA, customer support, resolution tracking
- **Customer Success** (4 prompts) — retention, onboarding, health scores, expansion
- **RevOps** (4 prompts) — pipeline allocation, deal routing, process optimization

Once they pick a role, present the use cases available in that role. Then read the matching prompt file(s) and present them.

---

#### MODE 2: Filtered by Role

The user said something like "sales" or "marketing". Read `prompt-index.md` (located in this skill's folder), filter to that role's section, and present the use cases as choices using AskUserQuestion:

Example for "sales":
- Deal Prioritization
- Optimize Sales Performance
- Targeting & Segmentation
- Lead Generation
- Funnel Optimization
- Customer Success
- Sales Enablement
- Prospecting
- Objection Handling
- Industry Selling
- Lead Nurture

Let them pick one or more, then show the matching prompts.

---

#### MODE 3: Smart Match

The user described what they need in natural language. This is the most common and most important mode.

**Process:**

1. Read `prompt-index.md` from this skill's folder
2. Scan the summaries and use case labels for semantic overlap with the user's request
3. Identify the top 1-3 matching prompts
4. Present them to the user like this:

> **I found a prompt that's close to what you need:**
>
> *[Role] — [Use Case]*
> "[The prompt text]"
>
> **Here's how I'd adapt it for your specific request:** [describe the adjustments]
>
> Want me to use this adapted version, tweak it further, or would you prefer to write your own from scratch?

**Important:** Don't just dump the template. Show the user how you'd modify it to match their intent. Merge their language and specifics into the template structure.

If there are multiple good matches, present up to 3 with a brief note on why each might fit, and let the user choose.

If no prompt is a good match (similarity is low), say so honestly and offer to go Freeform:

> "I don't have a template that closely matches what you're looking for, but I can help you write a custom prompt using HubSpot best practices. Want to go that route?"

---

#### MODE 4: Freeform / Custom

The user wants to write their own prompt or nothing in the library matched. Help them build a great prompt using these HubSpot best practices:

**Structure a good HubSpot prompt with:**
1. **Clear action verb** — start with what you want (Analyze, Find, Show, Create, Draft, Identify, Compare...)
2. **Specific HubSpot objects** — name the objects (deals, contacts, companies, tickets, quotes, invoices, orders, line items, subscriptions)
3. **Filters and conditions** — time ranges, stages, amounts, properties, lifecycle stages
4. **Desired output** — what fields to show, format, sorting, limits (e.g., "show top 10 by amount")
5. **Context for analysis** — what to calculate, compare, or conclude

**Example of a well-structured prompt:**
> "Analyze open HubSpot deals that were created during last 3 months with amounts over $10,000 that are not in closed-won or closed-lost stages. Show deal names, amounts, close dates, associated companies, and time in current pipeline stage."

Even in freeform mode, after the user gives you their draft, check the index one more time — there might be a template that could strengthen their prompt. If so, suggest incorporating elements from it.

---

### Step 3: Deliver and Offer Next Steps

After presenting the prompt (whether from template, adapted, or custom), always offer:

1. **Use it now** — if HubSpot tools are connected, offer to run the prompt against their actual HubSpot data
2. **Refine it** — "Want to adjust the time range, add more filters, or change the output format?"
3. **Explore related prompts** — "There are [N] other [role] prompts for [use case] — want to see those too?"
4. **Save a custom version** — if they modified a template significantly, note that they can save it for reuse

---

## File Structure

```
hubspot-prompts/
  SKILL.md                  ← you are here
  prompt-index.md           ← lightweight index for fast scanning
  prompts/
    sales/                  ← 31 prompts
    marketing/              ← 15 prompts
    commerce/               ← 18 prompts
    service/                ← 9 prompts
    customer_success/       ← 4 prompts
    revops/                 ← 4 prompts
```

## Reading Prompt Files

When you need to show a prompt's full text, read the file from `prompts/[role_slug]/[filename].md`. Each file contains:
- `<!-- keywords: ... -->` — for matching
- Role and use case labels
- The full prompt text

## Important Notes

- **Never force a template.** If the user wants to go custom, support them fully.
- **Adapt, don't copy-paste.** Templates are starting points. Always personalize to the user's context.
- **Placeholder handling.** Many prompts contain `[BRACKETS]` for user-specific values. When presenting a prompt, highlight these and ask the user to fill them in.
- **HubSpot connection.** If HubSpot MCP tools are available in the session, offer to execute the prompt directly against their data after selection.
