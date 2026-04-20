# Overnighter Hype Generator

## Overview

On-demand workflow. Invoked manually when an overnighter is imminent.

**Trigger phrases:**
- "CLEO — overnighter hype"
- "run the overnighter planner"
- "overnighter incoming"

## Workflow

### Step 1: Intake Questions

Ask these questions in ONE message. Keep it conversational, not a form.

```
🥃 Overnighter incoming — give me the details:

1. **Where?** (Garage HQ / cottage / away — and whose place)
2. **When?** (Date + what time does it kick off)
3. **Who's in?** (All four or a subset — Eric, Hal, James, Carl)
4. **What's anyone bringing?** (Bottles, cigars, food — anything already planned)
5. **Food plan?** (Carl BBQ / order in / potluck / TBD)
6. **What's on that night?** (Sports, movie, nothing — any occasion)
7. **Theme or vibe?** (Casual hang / milestone / whisky focus / anything goes)
8. **Anything else I should know?**
```

Wait for answers before generating.

---

### Step 2: Generate Hype Package

Use answers + crew profiles to generate the full package.

**Read before generating:**
- `/Users/cleo/clawd/cleo-newsletters/smoke-barrel/config/crew-profiles.md`
- `/Users/cleo/clawd/cleo-newsletters/smoke-barrel/config/crew-traditions.md`
- `/Users/cleo/clawd/cleo-newsletters/smoke-barrel/config/collection.md`

---

## Output Structure

### Email Sections (in order)

#### 1. The Opening — Set the Tone
- 2-3 sentences of pure hype
- Reference the location, the crew, the occasion
- Tone: excited, warm, like the best group chat message ever sent

#### 2. The Timeline
Suggested schedule for the day/evening. Make it real and specific.

Example format:
```
4:00 PM — Arrival. First round poured before coats are off.
4:30 PM — Carl lights the smoker. Arguments about wood chips begin.
5:00 PM — First cigar. Something medium to warm up the palate.
6:30 PM — Dinner. Eat well. This is a marathon not a sprint.
8:00 PM — The serious pours begin. Flight #1.
9:30 PM — Second cigar. Something fuller now that dinner has settled.
10:30 PM — Wild card pour. Someone always produces something unexpected.
11:30 PM — The nightcap. One last dram. Something peaty.
12:00 AM — Someone falls asleep in a chair. The night is complete.
```

Adapt timing to: when it starts, who's cooking, what's on TV, overnight vs. late night.

#### 3. The Whisky Plan
- **Flight 1: The Warm-Up** — 2 bottles, approachable, sets the mood
- **Flight 2: The Main Event** — 2-3 bottles, more serious, themed if possible
- **The Wild Card** — 1 bottle, something unexpected or debated
- **The Nightcap** — 1 bottle, the closer

Pull from:
- Bottles anyone said they're bringing
- Eric's collection (collection.md) for gap-fillers
- Personalize: work in James's peat obsession, Hal's Japanese/Irish, Carl's Talisker comfort zone, Eric's rarity hunting

Include brief tasting notes for each. Keep it fun, not stuffy.

#### 4. The Cigar Order
- **Pre-dinner smoke** — lighter, sets the tone (Hal's Nicaraguan Maduro vibe)
- **Post-dinner smoke** — fuller body now that everyone's fed
- **Late night** — if anyone's still going, something slow-burning

Note who smokes what based on crew profiles.
Reference: Hal (Nicaraguan Maduro), James (Bolivar, Brick House, CAO), Carl (Cuban / Nicaraguan), Eric (Don Tomas, Alec Bradley)

#### 5. The Food Plan
Based on what was shared in intake. If Carl is BBQing:
- Hype it up — he's the BBQ king
- Suggest what pairs well with what's being poured
- Note timing relative to whisky/cigar plan

If ordering in or TBD, make suggestions that complement the spirit of the night.

#### 6. What's On
- If sports: hype the game, suggest what to pour during key moments
- If movie: suggest something that fits the vibe (whisky + fire + good film)
- If nothing planned: suggest a playlist vibe or background option

#### 7. What to Bring
Short checklist per person based on what's been committed:
```
Eric: [bottles confirmed + anything suggested]
Hal: [his contributions]
James: [his contributions]
Carl: [his contributions + BBQ supplies if applicable]
Everyone: Your A-game.
```

#### 8. The Closer
- One punchy paragraph
- Remind them why these nights matter
- Get them genuinely excited

---

## Tone Rules

- **Hype but grounded** — this isn't a corporate event, it's your crew
- **Specific beats generic** — "the Lagavulin 16 after dinner" beats "a peaty dram"
- **Reference crew history** — inside references land hard (Hal's OG status, Carl built Garage HQ, James's Lagavulin origin story)
- **No fluff** — every sentence should earn its place
- **No price talk** — ever

---

## HTML Design

Same warm dark aesthetic as Smoke & Barrel Weekly.

```html
<!DOCTYPE html>
<html>
<head>
<meta charset="UTF-8">
<style>
  body { background: #1a1410; color: #e8e3db; font-family: Georgia, serif; }
  /* Warm dark with amber accents */
  /* Mobile-friendly */
</style>
</head>
<body>
<!-- Content -->
</body>
</html>
```

Subject line format:
```
🔥 Overnighter Brief — [Location] — [Date]
```

---

## Delivery Workflow

### Step 1: Discord Preview
After generating, post a **summary** to Discord:

```
🔥 Overnighter Brief ready for review — [Location] — [Date]

**Timeline:** [Start time] → [End time approx]
**Crew:** [Who's in]
**Whisky plan:** [Flight themes in 1 line]
**Cigars:** [Quick summary]
**Food:** [What's happening]

Let me know when it's good to send — or any changes.
```

### Step 2: Hold
Wait for Eric to say "send it" or request changes.

### Step 3: Email Send
When approved:
```bash
gog gmail send \
  --account cleo.clawdbot@gmail.com \
  --no-input \
  --to ecnorton@gmail.com,jameskahnt@gmail.com,hallanuza@gmail.com,carl@camech.ca \
  --subject "🔥 Overnighter Brief – [Location] – [Date]" \
  --body-html "$(cat [generated-file])"
```

Save HTML to:
```
/Users/cleo/clawd/smoke-barrel-archive/overnighter-[date]-[location].html
```

---

## Crew Quick Reference

**Eric** — 105 bottles, Campbeltown/Islands hunter, wants nose≠palate intrigue, Don Tomas/Alec Bradley cigars

**Hal** — OG (25 yrs cigars, 9 yrs whisky), Japanese/Irish/Bunnahabhain gaps, Nicaraguan Maduro robusto, try-first learner

**James** — Lagavulin obsessed (hooked by 1979 vintage), peat + cask strength + long finish, Bolivar/Brick House/CAO, music is part of his ritual

**Carl** — Built Garage HQ, BBQ king, 30+ yrs whisky, smaller Scottish distilleries, Talisker 10 anchor, Cuban + Nicaraguan cigars, "opinions spew with reckless abandon"

---

## Invocation

Eric will trigger this manually. No cron. No schedule.

When triggered, run Step 1 (intake questions) immediately.
