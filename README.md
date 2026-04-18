# CLEO Newsletters

Centralized repository for all CLEO newsletter prompts, configuration, and archives.

## Overview

This repository contains all newsletter systems managed by CLEO (Computerized Logistics for Executive Operations), Eric Norton's AI assistant.

## Newsletter Portfolio

### 1. Cybersecurity Brief
**Audience:** Corporate security professionals (senior director level)  
**Schedule:** Daily, Monday-Friday, 7:30 AM EST  
**Recipients:** eric.norton@calian.com, kevin.wilson@calian.com, allan.varrette@calian.com

[Documentation](./cybersecurity/prompts/daily-brief.md)

### 2. Emerging Tech Brief
**Audience:** Defence technology professionals  
**Schedule:** Daily, Monday-Friday, 8:30 AM EST  
**Recipients:** eric.norton@calian.com, chad.watson@calian.com

[Documentation](./emerging-tech/prompts/daily-brief.md)

### 3. Stock Chatter
**Audience:** Eric (personal)  
**Schedule:** Daily, Monday-Friday, 4:30 PM EST (end of trading)  
**Recipients:** ecnorton@gmail.com

[Documentation](./stock-chatter/prompts/daily-brief.md)

### 4. Smoke & Barrel Weekly
**Audience:** Eric's whisky/cigar crew (Eric, James, Hal, Carl)  
**Schedule:** Two-job workflow  
- Friday 8:00 PM - Generate + preview
- Saturday 8:00 AM - Send

**Recipients:** ecnorton@gmail.com, jameskahnt@gmail.com, hallanuza@gmail.com, carl@camech.ca

[Documentation](./smoke-barrel/prompts/weekly-newsletter.md) | [Saturday Send](./smoke-barrel/prompts/saturday-send.md)

## Repository Structure

```
cleo-newsletters/
├── README.md
├── cybersecurity/
│   ├── prompts/
│   │   └── daily-brief.md
│   ├── archives/
│   └── config/
├── emerging-tech/
│   ├── prompts/
│   │   └── daily-brief.md
│   ├── archives/
│   └── config/
├── stock-chatter/
│   ├── prompts/
│   │   └── daily-brief.md
│   ├── archives/
│   └── config/
└── smoke-barrel/
    ├── prompts/
    │   ├── weekly-newsletter.md
    │   └── saturday-send.md
    ├── archives/
    ├── config/
    │   ├── crew-profiles.md
    │   ├── crew-traditions.md
    │   ├── wine-section-guide.md
    │   ├── collection.md
    │   └── featured-history.json
    └── reference/
```

## Migration to Claude Routines

All prompts are now in markdown format for easy migration to Claude Projects or Claude Routines.

### Key Features

- **Markdown format:** Easy to read, edit, and version control
- **Modular structure:** Each newsletter is self-contained
- **Reference separation:** Config and reference files organized per newsletter
- **Archive ready:** Dedicated archive directories for historical newsletters

## Usage

### For OpenClaw Cron Jobs

Reference these prompts in your cron job configurations:

```bash
openclaw cron edit <job-id> \
  --message "$(cat cleo-newsletters/<newsletter>/prompts/<prompt>.md)"
```

### For Claude Routines

1. Navigate to desired newsletter directory
2. Copy markdown prompt content
3. Paste into Claude Project or Routine configuration
4. Adjust file paths if needed

## Maintenance

### Adding a New Newsletter

1. Create directory structure:
   ```bash
   mkdir -p new-newsletter/{prompts,archives,config}
   ```

2. Create prompt markdown file in `prompts/`

3. Add any reference files to `config/`

4. Update this README with newsletter details

### Updating Prompts

1. Edit markdown file in `prompts/`
2. Commit changes with clear message
3. Sync to active cron job or routine

## Reference Files

### Smoke & Barrel

Crew profiles and reference data are in `smoke-barrel/config/`:
- `crew-profiles.md` - Individual crew member preferences
- `crew-traditions.md` - Garage HQ rituals and history
- `wine-section-guide.md` - Wine recommendation guidelines
- `collection.md` - Eric's whisky collection (~107 bottles)
- `featured-history.json` - Tracking for avoiding repeats

### Stock Chatter

Stock tracking files:
- `TICKERS.md` - Watchlist
- `holdings.json` - Current positions
- `exchange_map.json` - Exchange lookups

## License

Private repository - All rights reserved.

## Author

CLEO - Computerized Logistics for Executive Operations  
Personal AI assistant to Eric Norton

---

*Last updated: April 18, 2026*
