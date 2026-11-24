# Data package

Frozen public Hong Kong government sources retrieved 17 November 2026.
`manifest.json` supplies URLs, byte counts and SHA-256 hashes of original source files.
`source_urls.json` is the direct download mapping.

## Curated inputs

- `curated/cpi_monthly.csv`: date (month start), composite_cpi and cpi_a. Headline values from C&SD December 2025 report Table 2.1, same Oct 2019-Sep 2020 base. 36 months, 2023-2025.
- `curated/oala_rates.csv`: effective_date, monthly_hkd, source. Select the last applicable rate for each analysis month. No one-off supplements.
- `curated/population_district.csv`: 18 districts, older counts 2011/2016/2021, total population 2021. Historical values are transparently transcribed from census Table 8.1. 2021 values match DC_21C.CSV. All district growth uses 2016-2021 to avoid 2011 Eastern/Wan Chai boundary issues.

## Raw source groups

- `oala_*.pdf`, policy/release HTML: allowance policy and historical rates. The 2025 OALA amount appears in Annex I, final page, SSA section.
- `cpi_report.pdf`, CPI release/table attachments: CPI values and cross-check context.
- `care_current.csv`: downloaded historical series including more dates than the study uses. The analysis filters Jan 2023-Dec 2025. Never substitute the latest row for a historical month.
- `care_dictionary.pdf`, Dec 2024/2025 PDFs: precise waiting-time definition and independent cross-checks.
- `older_persons_2021.pdf`, `census_district.zip`: census report and the unaltered published district CSV archive.
- `daycare.csv`, `daycare_2026.xlsx`: SWD 1 Apr 2026 day-care list. Capacity totals 4,243 across 103 listed units/sites.
- `de.geojson`, `dcu.geojson`, `decc.geojson`: three SWD/CSDI location layers. 106 source features, 103 matched April-list records used. Later coordinates do not prove historical locations.
- `district_simplified.geojson`: official C&SD/CSDI 2021 census districts, queried in WGS84 with 5-decimal coordinates and a small geometry tolerance for display. Used for district identity and static/interactive maps.
- Metadata JSON/HTML files document source names, coverage and revision context.

## Geographic assignment

Host district uses point-in-polygon on the matching 2021 boundary layer. Original CSDI DistrictEN labels remain in the generated `centres_geocoded.csv`. One Cheung Muk Tau unit is labelled Sha Tin but falls inside the Tai Po census polygon. The primary host allocation follows that polygon. The alternate equal-split scenario follows the April list's published service districts. It does not estimate actual user flows.

Capacity / population x 1,000 is a mixed-year provision proxy, not contemporary coverage, vacancy or unmet need. Source capacities and populations remain unchanged. The 2011 land total is comparable citywide; its Eastern/Wan Chai district counts are not used in direct growth comparisons.

Extract this ZIP beside the notebook so that `data/raw` and `data/curated` exist. The notebook includes all analytical code. `prepare_sources.py` rebuilds these curated inputs from the bundled sources when desired. Attribution belongs to SWD and C&SD/CSDI. Government data terms and OpenStreetMap attribution continue to apply.
