# HubSpot Prompts Skill for Claude

A library of **81 expert HubSpot prompts** organized by role and use case, built as an installable skill for [Claude](https://claude.ai) Cowork mode. Instead of hunting for the right prompt, just type `/hubspot-prompts` and Claude helps you find, adapt, or create the perfect prompt for your workflow.

---

## What It Does

This skill gives Claude a searchable library of HubSpot prompts covering Sales, Marketing, Commerce, Service, Customer Success, and RevOps. It works in four modes:

| Mode | How to trigger | What happens |
|---|---|---|
| **Guided** | `/hubspot-prompts` | Claude walks you through: pick a role, then a use case, then a prompt |
| **Filtered** | `/hubspot-prompts sales` | Jumps straight to that role's use cases |
| **Smart Match** | `/hubspot-prompts I need to find deals going cold` | Claude scans the library, finds the closest match, and adapts it to your words |
| **Freeform** | `/hubspot-prompts custom` or when nothing matches | Claude helps you write a prompt from scratch using HubSpot best practices |

The key design principle: **templates are starting points, not cages.** Claude always adapts prompts to your specific context, and you can go fully custom at any time.

---

## Installation

### Option 1: One-Click Install (Recommended)

1. Download the [`hubspot-prompts.skill`](./hubspot-prompts.skill) file from this repo
2. Open **Claude Desktop** and enter **Cowork mode**
3. Open the `.skill` file — Claude will show a **"Save skill"** button
4. Click it — done! The skill is now available in all your Cowork sessions

### Option 2: Manual Install

1. Clone or download this repo:
   ```bash
   git clone https://github.com/YOUR_USERNAME/hubspot-prompts-skill.git
   ```
2. Copy the contents (SKILL.md, prompt-index.md, and the `prompts/` folder) into your Claude skills directory
3. Restart Claude Desktop if needed

### Option 3: Build the .skill File Yourself

If you've made changes and want to repackage:
```bash
cd hubspot-prompts-skill
zip -r hubspot-prompts.skill SKILL.md prompt-index.md prompts/
```
Then install the resulting `.skill` file using Option 1.

---

## Usage

### Guided Mode — Browse and pick

Just type:
```
/hubspot-prompts
```
Claude will ask you to choose a role (Sales, Marketing, etc.), then show the available use cases, and present matching prompts for you to choose from.

### Filtered Mode — Jump to a role

Already know your department? Go direct:
```
/hubspot-prompts sales
/hubspot-prompts marketing
/hubspot-prompts commerce
/hubspot-prompts service
/hubspot-prompts customer success
/hubspot-prompts revops
```
Claude shows the use cases within that role and lets you pick.

### Smart Match — Describe what you need

Type a natural-language description and Claude finds the best match:
```
/hubspot-prompts I need to find deals that haven't been touched in 30 days
/hubspot-prompts help me analyze which products sell best
/hubspot-prompts I want to check ticket resolution times this quarter
```
Claude will show the closest prompt(s), explain how it would adapt them to your request, and ask if you want to use, tweak, or go custom.

### Freeform — Write your own

If you want full control or nothing in the library matches:
```
/hubspot-prompts custom
/hubspot-prompts I want to write my own prompt for something specific
```
Claude helps you build a prompt from scratch, using HubSpot best practices for structure, object references, and output formatting.

---

## Prompt Library

### Sales (31 prompts)

Covers the full sales workflow from prospecting to close.

| Use Case | Count | Examples |
|---|---|---|
| Sales Enablement | 7 | Meeting prep, pitch deck conversion, follow-up emails, documentation |
| Optimize Sales Performance | 6 | Sales velocity, deal analysis, action item prioritization |
| Deal Prioritization | 4 | Open deal analysis, stale account identification, strategic account planning |
| Performance & Analytics | 4 | Meeting transcript analysis, product-deal correlation, invoice analysis |
| Customer Success | 3 | Customer journey mapping, strategic relationship planning |
| Segment Effectiveness | 3 | Segment conversion likelihood, personalized outreach, contact prioritization |
| Targeting & Segmentation | 2 | Sales-ready contact identification, product-segment analysis |
| Industry Selling | 2 | First principles analysis, invoice patterns by industry |
| Lead Nurture | 2 | Stakeholder communication strategy, subscription tracking |
| Productivity | 2 | Executive assistant mode, meeting action items |
| Funnel Optimization | 1 | End-to-end customer journey analysis |
| Lead Generation | 1 | Predictive contact scoring |
| Prospecting | 1 | Personalized outreach email drafting |
| Objection Handling | 1 | Challenger selling and first-principles thinking |
| Quote Performance | 1 | Quote analysis with line item details |
| Subscription Intelligence | 1 | New subscription sales tracking |
| Invoice Analysis | 1 | Invoice vs. deal value analysis |
| Product Performance | 1 | Product win/loss analysis from line items |
| Customer Support | 1 | Technical documentation creation |

### Marketing (15 prompts)

From lead capture to campaign analytics.

| Use Case | Count | Examples |
|---|---|---|
| Performance & Analytics | 7 | Traffic source analysis, content performance, acquisition channel ROI |
| Targeting & Segmentation | 3 | Firmographic analysis, lifecycle stage targeting, ideal company profiling |
| Segment Effectiveness | 3 | Segment engagement patterns, lifetime value, buyer journey mapping |
| Customer Retention | 3 | At-risk customer identification, churn pattern analysis |
| Funnel Optimization | 3 | Lead-to-deal conversion, campaign coordination, market positioning |
| Lead Nurture | 2 | Early-stage lead engagement, contact assignment review |
| Customer Success | 1 | Customer financial journey mapping |
| Lead Generation | 1 | High-intent contact identification |
| Invoice Analysis | 1 | Revenue pattern analysis from invoice data |

### Commerce (18 prompts)

Orders, invoices, carts, subscriptions, and product catalog.

| Use Case | Count | Examples |
|---|---|---|
| Order Insights | 6 | Order value by region, fulfillment delays, cancelled orders, repeat customers |
| Cart Insights | 4 | Abandoned carts, cart-to-order conversion, product abandonment patterns |
| Invoice Analysis | 3 | Late payments, outstanding receivables, overdue invoices |
| Quote Performance | 2 | Expiring quotes, quote-to-order conversion |
| Subscription Intelligence | 2 | Churn risks, upgrade/downgrade patterns |
| Product Performance | 1 | Product demand and pricing analysis across quotes |

### Service (9 prompts)

Ticket management, SLA tracking, and support operations.

| Use Case | Count | Examples |
|---|---|---|
| Customer Support | 9 | Ticket resolution metrics, SLA compliance, high-priority company tickets, escalation patterns, support workload distribution |
| Performance & Analytics | 1 | Time-to-response and time-to-close metrics |

### Customer Success (4 prompts)

Retention, onboarding, and account health.

| Use Case | Count | Examples |
|---|---|---|
| Customer Success | 4 | Payment pattern analysis, new customer onboarding, deal-cancellation risk |
| Customer Retention | 2 | At-risk account identification, engagement scoring |
| Invoice Analysis | 1 | Payment delay detection |

### RevOps (4 prompts)

Pipeline hygiene, deal routing, and operational efficiency.

| Use Case | Count | Examples |
|---|---|---|
| Sales Enablement | 3 | Deal hygiene audit, pipeline velocity, deal allocation analysis |
| Optimize Sales Performance | 2 | Owner performance comparison, stage duration analysis |
| Productivity | 1 | Deal data quality checks |

---

## How It Works Under the Hood

The skill has three key files:

**`SKILL.md`** — The brain. Contains the routing logic that tells Claude how to determine which mode to use, how to present prompts, and how to help with freeform writing. This is what Claude reads when you invoke the skill.

**`prompt-index.md`** — The search index. A lightweight file listing all 81 prompts with their role, use cases, and a short summary. Claude scans this to find matches without having to read every individual prompt file.

**`prompts/`** — The library. 81 individual markdown files organized into 6 role subfolders. Each file contains keyword tags, use case labels, and the full prompt text. Claude only reads the specific file(s) it needs.

```
hubspot-prompts-skill/
├── README.md               ← you are here
├── LICENSE                  ← MIT license
├── SKILL.md                ← skill instructions for Claude
├── prompt-index.md         ← lightweight search index
├── hubspot-prompts.skill   ← one-click installable package
└── prompts/
    ├── sales/              ← 31 prompt files
    ├── marketing/          ← 15 prompt files
    ├── commerce/           ← 18 prompt files
    ├── service/            ← 9 prompt files
    ├── customer_success/   ← 4 prompt files
    └── revops/             ← 4 prompt files
```

---

## HubSpot Connection

This skill works in two ways:

**Without HubSpot connected** — Claude helps you find and craft prompts. You copy them and use them wherever you need (HubSpot AI, other tools, etc.).

**With HubSpot connected** — If you have the HubSpot MCP connector installed in Claude, the skill can execute prompts directly against your live HubSpot data. Claude will offer to run the prompt for you after selection.

To connect HubSpot to Claude, search for the HubSpot connector in Cowork's connector marketplace.

---

## Contributing

Contributions are welcome! Here's how to add prompts:

1. **Fork** this repo
2. **Create a prompt file** in the appropriate `prompts/[role]/` folder following this format:
   ```markdown
   <!-- keywords: keyword1, keyword2, keyword3 -->
   # Role: Use Case Name

   ## Use Cases
   Use Case 1, Use Case 2

   ## Prompt
   Your prompt text here. Use [BRACKETS] for user-specific values.
   ```
3. **Update `prompt-index.md`** — add an entry for your new prompt in the appropriate role section
4. **Submit a pull request** with a description of what your prompt does and when it's useful

### Prompt Writing Guidelines

A good HubSpot prompt should have:

- **Clear action verb** — Analyze, Find, Show, Create, Draft, Identify, Compare
- **Specific HubSpot objects** — deals, contacts, companies, tickets, quotes, invoices, orders, line items, subscriptions
- **Filters and conditions** — time ranges, stages, amounts, properties, lifecycle stages
- **Desired output** — fields to show, format, sorting, limits
- **Context for analysis** — what to calculate, compare, or conclude

### Available Roles

When adding prompts, place them in one of the existing role folders: `sales`, `marketing`, `commerce`, `service`, `customer_success`, `revops`. If your prompt genuinely doesn't fit any of these, open an issue to discuss adding a new role.

### Available Use Cases

Existing use cases include: Cart Insights, Customer Retention, Customer Success, Customer Support, Deal Prioritization, Funnel Optimization, Industry Selling, Invoice Analysis, Lead Generation, Lead Nurture, Objection Handling, Optimize Sales Performance, Order Insights, Performance & Analytics, Product Performance, Productivity, Prospecting, Quote Performance, Sales Enablement, Segment Effectiveness, Subscription Intelligence, Targeting & Segmentation.

You can add new use cases — just make sure to tag them consistently.

---

## Rebuilding the .skill File

After making changes, rebuild the installable package:

```bash
cd hubspot-prompts-skill
zip -r hubspot-prompts.skill SKILL.md prompt-index.md prompts/
```

The `.skill` file is just a zip archive with a `.skill` extension. It must contain a `SKILL.md` at the root with YAML frontmatter (`name` and `description` fields).

---

## Sharing

**GitHub** — Share this repo directly. Users can clone it or download the `.skill` file from Releases.

**skills.sh** — Upload the `.skill` file to [skills.sh](https://skills.sh) for discovery by the Claude community.

**Direct sharing** — Send the `hubspot-prompts.skill` file to anyone. They open it in Claude Cowork and click "Save skill."

---

## License

MIT License — see [LICENSE](./LICENSE) for details.

---

## Credits

Built by [Edyta Jordan](https://edytajordan.com). Prompts sourced from HubSpot's official prompt library and adapted for Claude skill format.
