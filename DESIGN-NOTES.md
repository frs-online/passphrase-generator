# FRS Design Theme Notes

## Extracted from frs-online.de

### Colors
| Role | Hex | Notes |
|------|-----|-------|
| Primary Text | `#31363a` | Dark gray, main body text |
| Secondary Text | `#6b7277` | Muted gray for links/labels |
| Background | `#ffffff` | Clean white |
| Links | `#428bca` | Classic blue |
| Accent 1 | `#1abc9c` | Teal/turquoise (active states) |
| Accent 2 | `#ffcc00` / `#ffaa00` | Yellow-orange (CTA/highlights) |
| Borders | `#d2d7da` | Light gray |
| Hover BG | `#ebedef` | Very light gray |

### Typography
- **Primary Font:** Lato (sans-serif)
- **Weights used:** 100, 300, 400, 700, 900
- **Text rendering:** optimizelegibility, antialiased
- **Letter spacing:** 0.75px on body text

### Design Style
- **Light theme** (white background, dark text)
- **Professional B2B** aesthetic
- **Clean, minimal** with subtle shadows
- **Corporate/technical** feel (security industry)
- Box shadows: `0 2px 4px rgba(0,0,0,0.25)` or `0 4px 8px rgba(0,0,0,0.25)`

### Current Passphrase Generator vs FRS Theme

| Aspect | Current Generator | FRS Theme |
|--------|-------------------|-----------|
| Background | Dark (`#0a0a0b`) | Light (`#ffffff`) |
| Text | Light (`#fafafa`) | Dark (`#31363a`) |
| Accent | Green (`#22c55e`) | Teal (`#1abc9c`) or Yellow (`#ffcc00`) |
| Font | Space Grotesk / JetBrains Mono | Lato |
| Style | Modern dark mode | Clean corporate light |

### Recommendation
Two options:
1. **Full rebrand** to match FRS corporate theme (light, Lato, teal accent)
2. **Keep dark theme** as standalone tool (current style is modern/professional, just different)

For internal tools, matching corporate identity builds trust. Suggest option 1.

---

## GitHub Organization Recommendations

### Organization Name
**Selected:** `frs-online` (matches domain frs-online.de)

### GitHub Organization: Key Considerations

#### Can you transfer ownership later?
**Yes.** Repository ownership can be transferred:
- From personal account → organization
- From organization → another organization
- From organization → personal account

However: **Organization ownership itself** requires at least one owner. You can add/remove owners freely.

#### Should you create an organization for a 15-person company?
**Yes, recommended** because:
- Separates personal projects from company code
- Allows adding employees later (even contractors)
- Professional appearance for any public repos
- Easier to manage access if someone leaves
- GitHub Free tier includes unlimited private repos for organizations

#### Implications of using personal account (`marcelreschke`) as org owner:
- Your personal account becomes the "owner" (can be changed later)
- You can invite others as owners/members
- Billing goes through the org (Free tier is fine for this use case)
- Your personal repos stay separate

#### Recommended Setup:
1. Create org `frs-online` with `marcelreschke` as owner
2. Create repo `passphrase-generator` (can be public for GitHub Pages)
3. Enable GitHub Pages from the repo settings
4. URL will be: `https://frs-online.github.io/passphrase-generator/`
