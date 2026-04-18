# Smoke & Barrel Saturday Send - Prompt

## Role

Send the pre-generated Smoke & Barrel Weekly newsletter.

**This job ONLY sends.** The newsletter was generated Friday evening.

## Workflow

### 1. Locate Newsletter File

```bash
FILE="/Users/cleo/clawd/smoke-barrel-archive/$(date +%Y-%m-%d)-smoke-barrel-weekly.html"
```

**Note:**
- Friday job creates file with Saturday's date (tomorrow from Friday)
- Saturday job looks for today's date (matches what Friday created)

### 2. Verify File Exists

```bash
ls -lh "$FILE"
```

### 3. Send Email

**Only if file exists:**

```bash
gog gmail send \
  --account cleo.clawdbot@gmail.com \
  --no-input \
  --to ecnorton@gmail.com,jameskahnt@gmail.com,hallanuza@gmail.com,carl@camech.ca \
  --subject "🥃 Smoke & Barrel Weekly – $(date +'%B %d, %Y')" \
  --body-html "$(cat $FILE)"
```

### 4. Update Tracking

**If email send succeeds (message_id returned):**

Update `/Users/cleo/clawd/smoke-barrel/featured-history.json` with this week's featured items.

### 5. Confirm to Discord

```
✅ Smoke & Barrel Weekly sent to the crew (Eric, James, Hal, Carl)
```

## Error Handling

### Newsletter File Not Found

Post to Discord:
```
❌ No Smoke & Barrel newsletter found - Friday generation may have failed
```

### Email Send Failed

Post to Discord:
```
❌ Failed to send Smoke & Barrel Weekly - check logs
```

### Critical Rules

- **Do NOT report success** unless `gog gmail send` returns a `message_id`
- **Do NOT update tracking** if send fails
- **Do NOT post success to Discord** if send fails

## Recipients

- ecnorton@gmail.com
- jameskahnt@gmail.com
- hallanuza@gmail.com
- carl@camech.ca

## Schedule

**Saturday 8:00 AM EST**

## Notes

- This is the second part of the two-job workflow
- Newsletter content is already generated
- Just send and confirm
- Simple and reliable
