# GitHub Mobile — Real Estate Site Management

## Why GitHub for Real Estate

Your Domovoy site lives on GitHub. Every property update, every new zone, every school addition — it's all version-controlled. From your iPhone, you can update the live site without touching a laptop.

---

## GitHub Mobile Setup

### Install & Configure
1. **App Store → GitHub** (official app)
2. Sign in as **marcuszakarov**
3. Star the **Domovoy** repo for quick access
4. Enable **push notifications** for Issues and PRs (clients/team can submit requests)

### Quick Access
- Pin the **Domovoy** repo to your GitHub home screen
- Add GitHub app to your iPhone Home Screen dock or App Library
- Create a **Siri Shortcut**: "Open Domovoy" → opens the repo directly

---

## Common Tasks from Your Phone

### 1. Edit Property Content on the Site

The Domovoy site is a single `index.html`. To update content:

1. Open GitHub Mobile → Domovoy repo
2. Tap `index.html`
3. Tap the **pencil icon** (edit)
4. Find the section you need to change (use browser search)
5. Make your edit
6. Scroll down → write commit message → **Commit**

**Common Edits**:
- Update property count: search for `370+` and update the number
- Update zone information: search for `coverage` section
- Update contact details: search for `contact` section
- Fix typos or update school names

### 2. Add New Content via Issues

Use Issues as your task tracker:

**Create Issue templates for your workflow**:

```markdown
## New Property to Add
**Property Name**:
**Zone**: (Koh Kaew / Thalang / Bang Tao / Kathu / Wichit / Chalong / Rawai)
**Nearest School**:
**Type**: (Villa / Condo / Townhouse)
**Bedrooms**:
**Price Range**:
**Key Features**:
**Photos uploaded**: Yes / No
**Status**: Available / Under offer / Let
```

```markdown
## Site Update Request
**Section**: (Hero / Schools / Zones / Contact / Other)
**What to change**:
**Priority**: (Now / This week / When possible)
**Requested by**:
```

### 3. Quick Photo/Content Push

When you have new property photos to reference:
1. Create an Issue with the property details
2. Attach photos directly in the Issue (drag & drop on mobile)
3. Photos get a permanent GitHub URL you can reference
4. Later (laptop or Claude): integrate into the site properly

### 4. Track Updates with Projects

Set up a GitHub Project board:

| Column | Purpose |
|--------|---------|
| **Inbox** | New requests, ideas, client feedback |
| **To Photograph** | Properties that need a site visit |
| **Content Ready** | Has photos + copy, ready to add |
| **Live** | Published on the site |
| **Archive** | Sold/let properties to remove |

---

## Branching Strategy for Non-Developers

Keep it simple:

- **`main`** — This is your live site. Don't edit directly.
- **`updates/[description]`** — Make changes here, then merge to main.

**From Phone**:
1. Create a branch (GitHub Mobile → Branch selector → New branch)
2. Make your edits on that branch
3. Create a Pull Request to merge into main
4. Review the changes → Merge
5. Your site is updated

If you're the only editor, editing `main` directly is fine too. The branch workflow is for when you have a team.

---

## Using GitHub with Claude Code

You can trigger Claude Code sessions from GitHub:

1. **Open an Issue** describing what you want changed
2. **Start a Claude Code session** referencing the Issue
3. Claude reads the Issue, makes the changes, pushes to a branch
4. **Review on your phone** → merge when happy

### Example Issue for Claude:
```
Title: Add 3 new properties to the Kathu zone

Body:
Please add these properties to the Domovoy site:

1. Villa Suan Luang - 3 bed, pool, near Kajonkiet School, 45,000 THB/mo
2. Condo The Deck - 2 bed, gym, near BCIS, 28,000 THB/mo
3. Townhouse Kathu Heights - 4 bed, garden, near QSI, 35,000 THB/mo

Add them to the coverage section under Kathu zone.
```

---

## Mobile-Friendly File Structure (Future)

As Domovoy grows, consider restructuring for easier mobile editing:

```
Domovoy/
├── index.html              ← Main landing page
├── toolkit/                ← This toolkit
├── properties/
│   ├── koh-kaew/
│   │   ├── villa-abc.md    ← Easy to edit on phone
│   │   └── condo-xyz.md
│   ├── thalang/
│   ├── bang-tao/
│   ├── kathu/
│   ├── wichit/
│   ├── chalong/
│   └── rawai/
├── schools/
│   └── school-data.json    ← School info database
└── assets/
    └── images/             ← Property photos
```

Each property as a separate Markdown file = easy phone editing, easy to find, easy to update.

---

## GitHub Actions (Automation Ideas)

Set these up once (laptop/Claude), then they run automatically:

### Auto-deploy on merge
```yaml
# .github/workflows/deploy.yml
name: Deploy Domovoy
on:
  push:
    branches: [main]
jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Deploy to hosting
        # Your deployment step here (Netlify, Vercel, GitHub Pages, etc.)
```

### Property listing reminder
```yaml
# .github/workflows/weekly-review.yml
name: Weekly Property Review
on:
  schedule:
    - cron: '0 9 * * 1'  # Every Monday 9 AM
jobs:
  remind:
    runs-on: ubuntu-latest
    steps:
      - name: Create review issue
        uses: actions/github-script@v7
        with:
          script: |
            github.rest.issues.create({
              owner: context.repo.owner,
              repo: context.repo.repo,
              title: `Weekly Property Review - ${new Date().toLocaleDateString()}`,
              body: '## Weekly Review Checklist\n- [ ] Check all listed properties still available\n- [ ] Update any price changes\n- [ ] Add new properties from this week\n- [ ] Remove sold/let properties\n- [ ] Check all contact links work'
            })
```

---

## Tips for Phone Editing

1. **GitHub Mobile's editor** is basic — for big changes, use Claude Code sessions
2. **For small fixes** (typos, numbers, contact info) — edit directly on phone
3. **Use Issues liberally** — they're your task list, even for yourself
4. **Commit messages matter** — write clear ones so you can track what changed
   - Good: "Update Kathu zone: add 3 new villas, update pricing"
   - Bad: "Update"
5. **Review before merge** — GitHub Mobile shows diffs clearly, use them
6. **Labels** — set up: `urgent`, `new-property`, `price-update`, `content`, `bug`
