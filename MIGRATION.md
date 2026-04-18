# Migration Guide - OpenClaw to Claude Routines

This guide covers migrating CLEO newsletters from OpenClaw cron jobs to Claude Routines (or keeping them in OpenClaw with improved organization).

## Repository Structure

All newsletter prompts are now centralized in this repository with markdown format for easy migration.

```
cleo-newsletters/
├── README.md               # Overview of all newsletters
├── MIGRATION.md            # This file
├── cybersecurity/          # Cybersecurity Daily Brief
├── emerging-tech/          # Emerging Tech Daily Brief
├── stock-chatter/          # Stock Chatter Daily Brief
└── smoke-barrel/           # Smoke & Barrel Weekly
```

## Option 1: Keep in OpenClaw (Recommended for Now)

### Update Cron Jobs to Reference This Repo

The cron jobs should now read prompts from this repository instead of `/Users/cleo/clawd/cron-prompts/`.

#### Update Workflow

1. **Pull latest changes** before each newsletter run:
   ```bash
   cd /Users/cleo/clawd/cleo-newsletters && git pull
   ```

2. **Read prompt from repo:**
   ```bash
   cat /Users/cleo/clawd/cleo-newsletters/<newsletter>/prompts/<prompt>.md
   ```

3. **Example for Cybersecurity Brief:**
   ```bash
   # In the cron job prompt:
   cd /Users/cleo/clawd/cleo-newsletters && git pull && \
   cat /Users/cleo/clawd/cleo-newsletters/cybersecurity/prompts/daily-brief.md
   ```

#### Update Cron Job Commands

For each cron job:

```bash
openclaw cron edit <job-id> \
  --message "$(cat /Users/cleo/clawd/cleo-newsletters/<newsletter>/prompts/<prompt>.md)"
```

**Job IDs:**
- Cybersecurity: `986eb67a-1ecc-43a1-a21b-3631bfd3042e`
- Emerging Tech: `c1e0d576-698c-4e19-bbc4-7dab83e4da95`
- Stock Chatter: `ad7359fc-47e3-4771-b17d-e6a7f5e18d1d`
- Smoke & Barrel Friday: `bc1efd48-ae2e-4f84-977f-de89c8d02917`
- Smoke & Barrel Saturday: `37bd0e68-44a3-41fa-9be0-b9629c6d10dc`

### Advantages of Staying in OpenClaw

- ✅ Existing infrastructure works
- ✅ All logging/monitoring in place
- ✅ Easy to update via git
- ✅ Central version control
- ✅ Can review diffs before updating

## Option 2: Migrate to Claude Routines

### Prerequisites

1. Claude Pro or Team account
2. Access to Claude Projects or Routines
3. Way to trigger routines on schedule (cron, GitHub Actions, etc.)

### Migration Steps per Newsletter

#### 1. Create Claude Project

1. Go to Claude.ai
2. Create new Project
3. Name it (e.g., "CLEO - Cybersecurity Brief")

#### 2. Add Knowledge Base

Upload reference files as project knowledge:

**For Cybersecurity:**
- None required (uses external tools)

**For Emerging Tech:**
- None required (uses external tools)

**For Stock Chatter:**
- Upload `stock-chatter/config/TICKERS.md`
- Upload `stock-chatter/config/holdings.json`
- Upload `stock-chatter/config/exchange_map.json`

**For Smoke & Barrel:**
- Upload `smoke-barrel/config/crew-profiles.md`
- Upload `smoke-barrel/config/crew-traditions.md`
- Upload `smoke-barrel/config/wine-section-guide.md`
- Upload `smoke-barrel/config/collection.md`
- Upload `smoke-barrel/config/featured-history.json`

#### 3. Set Custom Instructions

Copy the markdown prompt from `<newsletter>/prompts/<prompt>.md` into the Project's custom instructions.

**Note:** You may need to adjust file paths since Claude won't have direct filesystem access.

#### 4. Create Routine (If Available)

If Claude Routines is available:
1. Create new Routine
2. Link to Project
3. Set schedule (cron-like syntax)
4. Configure output delivery (email, webhook, etc.)

#### 5. Alternative: GitHub Actions

If Routines aren't available, use GitHub Actions to trigger Claude API:

```yaml
name: Cybersecurity Brief
on:
  schedule:
    - cron: '30 12 * * 1-5'  # 7:30 AM EST = 12:30 PM UTC
jobs:
  generate:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Generate Brief
        env:
          ANTHROPIC_API_KEY: ${{ secrets.ANTHROPIC_API_KEY }}
        run: |
          # Call Claude API with prompt from repo
          # Send email via API
```

### Challenges with Claude Routines Migration

**Tools Not Available:**
- `blogwatcher` CLI (custom tool in OpenClaw)
- `gog` CLI (Google/Gmail tool in OpenClaw)
- Direct filesystem access for reference files

**Solutions:**
1. **Replicate tools:** Build equivalent functionality using Claude's native tools
2. **API integrations:** Use Anthropic API + external services
3. **Hybrid approach:** Keep some parts in OpenClaw, move others to Routines

## Option 3: Hybrid Approach

### Recommended for Smoke & Barrel

- **Keep generation in OpenClaw** (has all the tools and reference files)
- **Use Claude for ideation/review** (can upload to Claude for feedback)
- **Best of both worlds**

### Example Workflow

1. Friday 8 PM: OpenClaw generates newsletter
2. Automatic: Upload draft to Claude Project for review (optional)
3. Saturday 8 AM: OpenClaw sends (or waits for approval)

## Updating Prompts

### In OpenClaw

1. **Edit markdown file** in this repo
2. **Commit and push:**
   ```bash
   git add <newsletter>/prompts/<prompt>.md
   git commit -m "Update: <description>"
   git push
   ```
3. **Sync cron job:**
   ```bash
   openclaw cron edit <job-id> \
     --message "$(cat cleo-newsletters/<newsletter>/prompts/<prompt>.md)"
   ```

### In Claude Routines

1. **Edit markdown file** in this repo
2. **Commit and push** (same as above)
3. **Update Project custom instructions** in Claude UI
4. Or: If using API, next run will pull latest from repo

## Testing

### Before Full Migration

1. **Test in Claude UI** with a sample prompt
2. **Verify all reference data** is accessible
3. **Test external tool alternatives**
4. **Compare output quality** vs OpenClaw version

### Validation Checklist

- [ ] Newsletter generates successfully
- [ ] All required data sources accessible
- [ ] Output format matches expectations
- [ ] Delivery mechanism works (email/webhook)
- [ ] Schedule triggers correctly
- [ ] Error handling works

## Rollback Plan

If migration fails:

1. **Keep OpenClaw jobs running** (don't disable until Claude version proven)
2. **Git revert** if prompt changes break anything
3. **Document issues** in GitHub Issues
4. **Iterate** until stable

## Current Status (April 18, 2026)

- ✅ All prompts converted to markdown
- ✅ Repository structure created
- ✅ Reference files organized
- ✅ Committed and pushed to GitHub
- ⏳ OpenClaw cron jobs not yet updated (still using old paths)
- ⏳ Claude Routines migration not started

## Next Steps

**Immediate (Stay in OpenClaw):**
1. Update cron jobs to reference this repo
2. Test that all newsletters generate correctly
3. Monitor for issues

**Future (Claude Routines):**
1. Evaluate Claude Projects/Routines availability
2. Pilot one newsletter (suggest: Stock Chatter - simplest)
3. Iterate based on results
4. Migrate others if successful

## Questions?

Contact: Eric Norton (via CLEO)

---

*Last updated: April 18, 2026*
