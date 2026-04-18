# Smoke & Barrel Weekly Newsletter - Prompt

## Overview

This is a TWO-JOB workflow:
1. **Friday 8 PM:** Generate newsletter + Discord preview
2. **Saturday 8 AM:** Send pre-generated newsletter (separate job)

This prompt is for the FRIDAY PREVIEW generation.

## Role

Generate Smoke & Barrel Weekly newsletter for Eric's whisky/cigar crew.

## Required Reading

Before generating, READ these files:
- `crew-profiles.md` - Individual crew member preferences
- `crew-traditions.md` - Garage HQ rituals and history
- `wine-section-guide.md` - Wine recommendation guidelines
- `collection.md` - Eric's owned bottles (DO NOT recommend duplicates)
- `featured-history.json` - Avoid repeat recommendations

## Core Principles

- **DISCOVERY > REPETITION**
- Focus on NEW discoveries
- Personalize for crew members
- Reference Garage HQ, infinity bottles
- Check Gmail for distillery newsletters
- Research new releases
- Verify Whiskybase ratings

## Boy's Trip Corner

Goal: Inspire and warm up Hal & James (Carl and Eric already onboard)

### Rotation Ideas
- Weekend cottage (simple, accessible)
- Weekend trip to US (Buffalo, Detroit for different bottles/cigars)
- Cape Breton / Glenora Distillery (Canadian whisky pilgrimage)
- Building towards Scotland (Islay, Speyside - the motherland)

### Guidelines
- ONE paragraph per week
- Rotate ideas to keep fresh
- Show progression: small trips → grand adventure
- Keep aspirational, NOT logistics-heavy
- Don't repeat same destination consecutive weeks

## Tone Rules

**CRITICAL - DO NOT:**
- Make comments about affordability
- Use budget language
- Make price consciousness references
- Talk about "won't break the bank" or similar

**DO:**
- Personalize based on taste/style
- Let prices speak for themselves
- Focus on value and quality

## Newsletter Sections

### 1. This Month's Flight
4-5 bottles from Eric's collection.md

**Requirements:**
- Create RESEARCHED thematic flights (not random)
- Examples: "Irish Pot Still Showdown", "Islay Peat Ladder", "Bourbon Proof Spectrum"
- Include tasting notes
- Explain flavor progression
- Explain why this pairing works
- Flight should tell a story or teach something

### 2. Cigar & Whisky Pairings
2-3 pairings

**Requirements:**
- Match specific cigars (Cigar Chief) with whiskies
- Explain WHY they pair well (flavor profiles, strength, complementary notes)
- Research actual pairing principles (don't guess)
- Verify cigar availability at Cigar Chief

### 3. Special Bottles
2-3 bottles - Gap fillers / New arrivals

**Requirements:**
- Interesting bottles that fill gaps OR newly available at LCBO/BSW
- Not just overnighter bottles - anything genuinely interesting
- Check https://booze-feed.ca/whisky for new LCBO arrivals
- Verify LCBO/BSW availability FIRST
- **CRITICAL:** US tariffs block bourbon at LCBO - verify before recommending American whisky
- Include Whiskybase rating and link
- Skip section if no interesting bottles available

### 4. World Watch
2-3 bottles - New releases / Duty free targets

**Requirements:**
- Popular, unique, newly released bottles WORLDWIDE
- Eric travels - bottles to watch for at duty free
- Don't need local availability
- Include country/region where commonly found
- Include Whiskybase rating and link
- Focus on buzz, high ratings, limited releases

### 5. Smoke Report
2-3 cigars

**Requirements:**
- Check https://www.cigaraficionado.com for ratings, reviews, releases
- Verify availability at Cigar Chief
- Include back-in-stock items, new arrivals, seasonal picks
- Can mention pairing suggestions (reference section 2)

### 6. Red Wine Picks
2-3 wines, LCBO ONLY

**Requirements:**
- Verify LCBO availability and pricing
- $15-25 CAD for everyday drinking
- Can go higher for "overnighter picks"

### 7. Boy's Trip Corner
ONE paragraph

**Requirements:**
- Rotate destinations
- Keep aspirational and inspiring
- No logistics, costs, or step-by-step details

## Whiskybase Integration

**MANDATORY** for EVERY whisky mentioned:
- Search Whiskybase for the bottle
- Include rating (e.g., "86/100 on Whiskybase")
- Include link to Whiskybase page
- Use ratings to validate quality/interest

## Research Sources

### Required Checks
- **Whiskybase.com** - Ratings and reviews for all bottles
- **https://booze-feed.ca/whisky** - New LCBO whisky arrivals
- **https://www.cigaraficionado.com** - Cigar ratings, reviews, releases
- Gmail newsletters - Distillery releases, industry news
- **LCBO website** - Availability and pricing verification
- **BSW Liquors** - Availability and pricing verification
- **Cigar Chief** - Cigar availability verification

## Verification Workflow

1. Research potential products (newsletters, Whiskybase, booze-feed, Cigar Aficionado)
2. For Special Bottles: Check booze-feed.ca, VERIFY LCBO/BSW availability
3. **CRITICAL:** Verify bourbon availability (US tariffs = currently blocked at LCBO)
4. For Smoke Report: Check Cigar Aficionado ratings, VERIFY Cigar Chief availability
5. For World Watch: Find Whiskybase ratings, research availability
6. Cross-check Eric's collection.md (avoid duplicate recommendations)
7. Check featured-history.json (avoid repeats)
8. Generate newsletter with verified, researched content

## Quality Standards

- **Better to skip a section** than fill with mediocre picks
- Special Bottles should be genuinely interesting
- Flights should be educational (not random bottles)
- Pairings should be researched (not guessed)
- **Quality over quantity**

## HTML Styling

### Design Requirements
- Warm dark aesthetic (keep current vibe)
- Light body text for desktop readability (#f4f1ed or #e8e3db)
- Sufficient contrast for headings and links
- Mobile-friendly + desktop-optimized

### Structure
```html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<style>
/* Warm dark background with light text */
</style>
</head>
<body>
<!-- Newsletter content -->
</body>
</html>
```

## Friday Evening Preview Workflow

### Steps

1. **Generate** full HTML email content
2. **Calculate** tomorrow's date (Saturday):
   ```bash
   SATURDAY_DATE=$(date -v+1d +%Y-%m-%d)
   ```
3. **Write** HTML to:
   ```
   /Users/cleo/clawd/smoke-barrel-archive/${SATURDAY_DATE}-smoke-barrel-weekly.html
   ```
   - Names file with SATURDAY'S date (when it will be sent)
   - Example: Friday Mar 20 creates `2026-03-21-smoke-barrel-weekly.html`
4. **Verify** file exists:
   ```bash
   ls -lh /Users/cleo/clawd/smoke-barrel-archive/${SATURDAY_DATE}-smoke-barrel-weekly.html
   ```
5. **Create SUMMARY** of newsletter:
   - 2-3 sentences per section in bullet format
   - Highlight key bottles, pairings, trip idea
   - Keep it scannable
   - Include filename: "Saved to: ${SATURDAY_DATE}-smoke-barrel-weekly.html"
6. **Post summary** to Discord:
   ```
   📋 Smoke & Barrel Weekly preview ready for Saturday 8 AM. 
   Let me know if you want any tweaks before it sends.
   ```
7. **DO NOT SEND EMAIL** - that happens Saturday morning

### Critical Notes

- This job ONLY generates + previews
- File is named with SATURDAY's date (tomorrow from Friday)
- Saturday send job finds it using `$(date +%Y-%m-%d)` on Saturday morning

## Crew Personalization

### Eric Norton
- 105 bottles (largest collection)
- Gaps: Springbank, Kilkerran (Campbeltown), Arran
- Ideal: Sweet peat + long oily finish + nose/palate intrigue
- Cigars: Don Tomas, Alec Bradley
- Excited by: Rarity/limited availability

### Hal Anuza
- 9 years whisky, 25 years cigars (OG)
- Gaps: Japanese, Irish, Bunnahabhain
- Curious: Indian whisky (Amrut, Paul John), Colorado whisky
- Cigars: Nicaraguan Maduro robusto (heritage)
- Budget: $50-150 whisky
- Learning: Try first, read later

### James Kahnt
- 26 years whisky, 20 years cigars
- Lagavulin obsessed (avoid Lagavulin 8 though)
- Gaps: Lagavulin 10 travel exclusive, Bardstown
- Ideal: Peat + cask strength + long finish
- Cigars: Bolivar, Brick House, CAO
- **Unique:** Music + whisky connection

### Carl
- 30+ years whisky, 10+ years cigars
- Built Garage HQ (BBQ king)
- Wants: Smaller Scottish distilleries not in Ontario
- Gaps: Bardstown
- Ideal: Smoky, peaty, fruit, cask strength
- Cigars: Cubans and Nicaraguan
- Learning: Methodical hunter

## Recipients

Email will be sent Saturday to:
- ecnorton@gmail.com
- jameskahnt@gmail.com
- hallanuza@gmail.com
- carl@camech.ca

## Schedule

- **Friday 8:00 PM** - Generate + preview
- **Saturday 8:00 AM** - Send (separate job)

## Reference Files Location

All reference files in `/Users/cleo/clawd/smoke-barrel/`:
- crew-profiles.md
- crew-traditions.md  
- wine-section-guide.md
- collection.md
- featured-history.json
