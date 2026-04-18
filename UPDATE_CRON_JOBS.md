# Update OpenClaw Cron Jobs

This document provides commands to update all OpenClaw cron jobs to reference the new centralized newsletter repository.

## Prerequisites

```bash
cd /Users/cleo/clawd/cleo-newsletters
git pull  # Ensure you have latest
```

## Cron Job Updates

### 1. Cybersecurity Daily Brief

**Job ID:** `986eb67a-1ecc-43a1-a21b-3631bfd3042e`  
**Schedule:** Mon-Fri 7:30 AM EST

```bash
openclaw cron edit 986eb67a-1ecc-43a1-a21b-3631bfd3042e \
  --message "$(cat /Users/cleo/clawd/cleo-newsletters/cybersecurity/prompts/daily-brief.md)"
```

### 2. Emerging Tech Daily Brief

**Job ID:** `c1e0d576-698c-4e19-bbc4-7dab83e4da95`  
**Schedule:** Mon-Fri 8:30 AM EST

```bash
openclaw cron edit c1e0d576-698c-4e19-bbc4-7dab83e4da95 \
  --message "$(cat /Users/cleo/clawd/cleo-newsletters/emerging-tech/prompts/daily-brief.md)"
```

### 3. Stock Chatter Daily Brief

**Job ID:** `ad7359fc-47e3-4771-b17d-e6a7f5e18d1d`  
**Schedule:** Mon-Fri 4:30 PM EST

```bash
openclaw cron edit ad7359fc-47e3-4771-b17d-e6a7f5e18d1d \
  --message "$(cat /Users/cleo/clawd/cleo-newsletters/stock-chatter/prompts/daily-brief.md)"
```

### 4. Smoke & Barrel Friday Preview

**Job ID:** `bc1efd48-ae2e-4f84-977f-de89c8d02917`  
**Schedule:** Friday 8:00 PM EST

```bash
openclaw cron edit bc1efd48-ae2e-4f84-977f-de89c8d02917 \
  --message "$(cat /Users/cleo/clawd/cleo-newsletters/smoke-barrel/prompts/weekly-newsletter.md)"
```

### 5. Smoke & Barrel Saturday Send

**Job ID:** `37bd0e68-44a3-41fa-9be0-b9629c6d10dc`  
**Schedule:** Saturday 8:00 AM EST

```bash
openclaw cron edit 37bd0e68-44a3-41fa-9be0-b9629c6d10dc \
  --message "$(cat /Users/cleo/clawd/cleo-newsletters/smoke-barrel/prompts/saturday-send.md)"
```

## Update All at Once

```bash
#!/bin/bash
# Update all cron jobs at once

REPO="/Users/cleo/clawd/cleo-newsletters"

echo "Updating Cybersecurity Brief..."
openclaw cron edit 986eb67a-1ecc-43a1-a21b-3631bfd3042e \
  --message "$(cat $REPO/cybersecurity/prompts/daily-brief.md)"

echo "Updating Emerging Tech Brief..."
openclaw cron edit c1e0d576-698c-4e19-bbc4-7dab83e4da95 \
  --message "$(cat $REPO/emerging-tech/prompts/daily-brief.md)"

echo "Updating Stock Chatter Brief..."
openclaw cron edit ad7359fc-47e3-4771-b17d-e6a7f5e18d1d \
  --message "$(cat $REPO/stock-chatter/prompts/daily-brief.md)"

echo "Updating Smoke & Barrel Friday..."
openclaw cron edit bc1efd48-ae2e-4f84-977f-de89c8d02917 \
  --message "$(cat $REPO/smoke-barrel/prompts/weekly-newsletter.md)"

echo "Updating Smoke & Barrel Saturday..."
openclaw cron edit 37bd0e68-44a3-41fa-9be0-b9629c6d10dc \
  --message "$(cat $REPO/smoke-barrel/prompts/saturday-send.md)"

echo "✅ All cron jobs updated!"
```

## Important File Path Updates

The new prompts reference the newsletter repository for config files:

### Smoke & Barrel Reference Files

**Old paths:**
```
/Users/cleo/clawd/smoke-barrel/crew-profiles.md
/Users/cleo/clawd/smoke-barrel/crew-traditions.md
/Users/cleo/clawd/smoke-barrel/wine-section-guide.md
/Users/cleo/clawd/smoke-barrel/collection.md
/Users/cleo/clawd/smoke-barrel/featured-history.json
```

**New paths:**
```
/Users/cleo/clawd/cleo-newsletters/smoke-barrel/config/crew-profiles.md
/Users/cleo/clawd/cleo-newsletters/smoke-barrel/config/crew-traditions.md
/Users/cleo/clawd/cleo-newsletters/smoke-barrel/config/wine-section-guide.md
/Users/cleo/clawd/cleo-newsletters/smoke-barrel/config/collection.md
/Users/cleo/clawd/cleo-newsletters/smoke-barrel/config/featured-history.json
```

**ACTION REQUIRED:** Update the markdown prompts to reference new paths, OR create symlinks:

```bash
ln -s /Users/cleo/clawd/cleo-newsletters/smoke-barrel/config/crew-profiles.md /Users/cleo/clawd/smoke-barrel/crew-profiles.md
ln -s /Users/cleo/clawd/cleo-newsletters/smoke-barrel/config/crew-traditions.md /Users/cleo/clawd/smoke-barrel/crew-traditions.md
ln -s /Users/cleo/clawd/cleo-newsletters/smoke-barrel/config/wine-section-guide.md /Users/cleo/clawd/smoke-barrel/wine-section-guide.md
ln -s /Users/cleo/clawd/cleo-newsletters/smoke-barrel/config/collection.md /Users/cleo/clawd/smoke-barrel/collection.md
ln -s /Users/cleo/clawd/cleo-newsletters/smoke-barrel/config/featured-history.json /Users/cleo/clawd/smoke-barrel/featured-history.json
```

### Stock Chatter Reference Files

**Old paths:**
```
/Users/cleo/clawd/stocks/TICKERS.md
/Users/cleo/clawd/stocks/holdings.json
/Users/cleo/clawd/stocks/exchange_map.json
```

**New paths:**
```
/Users/cleo/clawd/cleo-newsletters/stock-chatter/config/TICKERS.md
/Users/cleo/clawd/cleo-newsletters/stock-chatter/config/holdings.json
/Users/cleo/clawd/cleo-newsletters/stock-chatter/config/exchange_map.json
```

**ACTION REQUIRED:** Same as above - update prompts or create symlinks.

## Verification

After updating, verify each job:

```bash
openclaw cron runs --id <job-id> --limit 1
```

Check that the task shows the new markdown prompt content.

## Rollback

If issues occur, revert to old prompts:

```bash
openclaw cron edit <job-id> \
  --message "$(cat /Users/cleo/clawd/cron-prompts/<old-file>.txt)"
```

Old prompt files are still in `/Users/cleo/clawd/cron-prompts/` as backup.

---

*Last updated: April 18, 2026*
