# Red Wine Section - Newsletter Guide

**Position:** Towards the end, after whisky and cigars sections  
**Added:** 2026-02-07

---

## Section Title Options
- 🍷 **Red After Dark**
- 🍷 **The Final Pour**
- 🍷 **End of Night Red**
- 🍷 **Garage Vino**

---

## Standard Structure

### 1. Red of the Week
**Format:**
```
🍷 [Wine Name] ([Varietal], [Region], [Vintage])
Price: $XX.XX at [LCBO](link)

[2-3 sentence tasting note - not wine-snob language]

Why it works: [Connection to the crew/garage vibe]
```

**Example:**
```
🍷 Catena Malbec (Mendoza, Argentina, 2021)
Price: $21.95 at LCBO

Big, bold, fruit-forward. Think blackberries and a hint of smoke - basically the red wine equivalent of an Islay. Smooth enough to sip after a Padron, with enough backbone to stand up to the last cigar of the night.

Why it works: This is what you crack open when the whisky's done its job and you're settling in for the final stretch. Pairs beautifully with the lingering smoke.
```

### 2. Pairing Note (Optional, rotate)
Connect the wine to what came before in the session:
- "After an Ardbeg and a Padron, this cuts through perfectly"
- "Smooth landing after peaty whiskies"
- "The perfect bookend to a bourbon-forward night"

### 3. Overnighter Pick (Occasional - 1x per month)
**Format:**
```
🌟 Overnighter Splurge: [Premium Wine Name]
Price: $XX.XX at LCBO (link)

[Why this is special - occasion wine]
```

**Price Range for Overnighter:** $40-80 CAD (special, but not absurd)

---

## Wine Selection Criteria

### Everyday Picks ($15-25)
- **Varietals the crew will enjoy:**
  - Malbec (bold, fruit-forward)
  - Cabernet Sauvignon (structured, rich)
  - Tempranillo/Rioja (earthy, complex)
  - Syrah/Shiraz (bold, spicy)
  - Zinfandel (jammy, full-bodied)
  - Super Tuscans (Italian blends)
  
- **Avoid:**
  - Light/delicate wines (Pinot Noir unless it's bold)
  - Wines that need food pairing
  - Overly tannic wines that need aging

### Overnighter Picks ($40-80)
- Aged Bordeaux
- Premium Napa Cabernet
- High-end Amarone
- Special reserve Rioja
- Cult winery bottles

---

## Tone & Language

**Do:**
- "This is what you crack after the last cigar"
- "Bold enough to follow whisky"
- "Smooth landing after a peaty night"
- "The bookend to a great session"

**Don't:**
- Wine-snob jargon ("tertiary notes of leather and tobacco")
- Food pairing details (they're not eating)
- Overly technical (pH levels, aging potential)
- Pretentious language

**Keep it:**
- Approachable
- Connected to the garage vibe
- Focused on the experience, not the specs

---

## Research Sources

### LCBO Search
- Use: `https://www.lcbo.com/en/catalogsearch/result/#q=WINE_NAME&t=Products`
- Verify: In stock, price, vintage
- Filter: Red wines, $15-25 range

### Wine Reviews (For Context, Not Copy)
- Vivino (crowd ratings - good for "this is popular" signal)
- Wine Spectator (professional scores - use sparingly)
- LCBO product descriptions (often have tasting notes)

### Reddit Wine Communities (Optional)
- r/wine - "What's good at LCBO?" threads
- r/ontario - LCBO finds and deals

---

## Link Requirements

Every wine mention needs:
1. **LCBO product page link** (direct to the wine)
2. **Price in CAD**
3. **Availability check** ("In stock" callout if applicable)

---

## Rotation Tracking

Add featured wines to `/Users/cleo/clawd/smoke-barrel/featured-history.json`:

```json
{
  "last_featured": {
    "Catena Malbec 2021": "2026-02-15",
    "..."
  }
}
```

Avoid repeating wines within 8-10 weeks unless:
- New vintage available
- Price drop or special release
- Overnighter-tier wine (those can repeat less frequently)

---

## Sample Full Section

```markdown
## 🍷 Red After Dark

The whisky's done, the cigars are half-ash, and it's time for the final pour. Here's what you crack when the night's winding down.

### Red of the Week: Catena Malbec (Mendoza, 2021)

**[$21.95 at LCBO](https://www.lcbo.com/...)**

Big, bold, fruit-forward. Think blackberries and a hint of smoke - basically the red wine equivalent of an Islay. Smooth enough to sip after a Padron, with enough backbone to stand up to the lingering smoke.

**Why it works:** This is what you open when the last cigar's halfway done and nobody's ready to call it a night yet. Perfect bookend to a bourbon-forward evening.

**Pairs with:** That final Oliva or Padron. The wine's fruit cuts through the smoke beautifully.

---

### 🌟 Overnighter Pick: Penfolds Bin 389 (South Australia, 2019)

**[$54.95 at LCBO](https://www.lcbo.com/...)**

This one's for when Carl fires up the garage heater for an all-nighter. Cabernet-Shiraz blend aged in the same barrels used for Grange (Penfolds' flagship). Rich, layered, complex - the kind of wine that sparks a 2 AM debate.

**Save it for:** The next epic overnighter. This deserves the full crew and a few hours to spare.
```

---

*Use this guide every week. Keep the section fresh, the wines varied, and the language grounded. This is the final act of the garage session - make it count.*
