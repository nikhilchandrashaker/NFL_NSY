# Net Sack Yards — 2025 NFL Regular Season

A descriptive study of how much pass-rush production defenses keep after giving yards back through undisciplined pass-rush penalties. Covers all 32 teams, 2025 regular season only.

## The metric

**Net Sack Yards (defense)** = yards lost by opposing offenses on sacks − yards surrendered on undisciplined pass-rush penalties. Higher is better.

**Net Sack Yards Lost (offense)** = sack yards lost − penalty yards gained from opponents' pass-rush fouls. Lower is better.

"Undisciplined pass rush" is defined here as three accepted penalty types: roughing the passer, defensive offside, and neutral zone infraction.

## Files

| File | What it is |
|---|---|
| `net_sack_yards_2025_real_data.xlsx` | The dataset. Tabs: **Net Sack Yards** (defense), **Offense View**, **Sources & Notes**. Blue cells are sourced inputs; black cells are formulas. |
| `net_sack_yards_dashboard.html` | Interactive dashboard (Defense/Offense toggle, ranked bars, scatter, sortable table). Self-contained; open in any browser. Also published as an artifact. |
| `net_sack_yards_research_paper.pdf` | Short research paper using only the 2025 regular season. |
| `README.md` | This file. |

## Headline results

- League: 1,287 sacks, 8,336 sack yards, 2,295 penalty yards surrendered, 6,041 net yards (give-back rate 27.5%).
- Best defenses by net: Cleveland (321), Atlanta (320), Houston (310), Denver (302).
- Worst: Chicago (50), Kansas City (75), NY Jets (115), San Francisco (133).
- Denver led the league in sacks (68) but fell from 1st to 4th once penalties were netted out.

## Sources

- **Sacks / sack yards (defense):** FOX Sports team defense stats, 2025 regular season. Sack counts cross-checked against NFL.com for all 32 teams.
- **Sacks taken / yards lost (offense):** NFL.com team stats, 2025 regular season.
- **Penalties by type and team:** NFLPenalties.com (nflfastR-based).

## Adjustments and checks

1. NFLPenalties.com totals include playoff games. Postseason flags were found in each penalty log and removed:
   - Roughing the passer: Philadelphia (8 yds), LA Rams (5 yds).
   - Defensive offside: Buffalo (2 × 5), LA Rams (5), Seattle (2 × 5).
   - Neutral zone infraction: Denver (5), LA Rams (5).
   The same flags were removed from the beneficiary teams on the Offense View.
2. Only accepted penalties count; declined and offsetting flags carry no yardage. Yardage is as marched.
3. Reconciliation: after adjustment, league penalty totals are 1,251 yds (roughing), 672 yds (defensive offside) and 372 yds (neutral zone). Offense and defense sack totals match exactly (1,287 sacks, 8,336 yds).

## Caveats

- Defensive offside and neutral zone infraction are pre-snap fouls, not tagged to pass-rush snaps, and defensive offside includes some special-teams flags. They are a proxy.
- Not included: encroachment, running into the passer, unnecessary roughness on the QB, face masks (not available by team from the sources).
- The automatic first down on roughing the passer is not valued.
- No exposure adjustment (opponent dropbacks were not available).
- Single season only; a full-league 2024 sack-yard source could not be found, so no prior-season comparison is included.

## Updating or extending

- In the workbook, edit the blue input cells; rankings and net values recalculate.
- To add a penalty type, add count and yard columns and extend the "Penalty Yards Surrendered" formula (column K) on the defensive tab and the "Penalty Yards Gained" formula (column K) on the Offense View.
- The dashboard's data is an embedded JSON array near the top of its script; replace it to refresh.
