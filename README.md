# Presidential precinct data for the 2020 general election

The Upshot scraped and standardized precinct election results from states and counties around the country, and joined this tabular data to precinct boundaries to create a nationwide election map. This map _does not_ have full coverage for every state: data availability and caveats for each state are listed below. We are releasing this data for re-use under the MIT license in this repository.

The GeoJSON dataset can be downloaded at: https://int.nyt.com/newsgraphics/elections/map-data/2020/national/precincts-with-results.geojson.zip

Properties on each precinct polygon:

- `GEOID`: unique identifier for the precinct, formed from the five-digit county FIPS code followed by the precinct name/ID (eg, `30003-08`)
- `votes_dem`: votes received by Joseph Biden
- `votes_rep`: votes received by Donald Trump
- `votes_total`: total votes in the precinct, including for third-party candidates
- `votes_per_sqkm`: total votes divided by the area of the precinct, rounded to an integer
- `pct_dem_lead`: `(votes_dem - votes_rep) / votes_total`, rounded to one decimal place (eg, -21.3)
- `pct_dem_lead_change`: `pct_dem_lead - pct_dem_lead_2016`
  - The 2016 lead value is calculated from the national dataset assembled by Ryne Rohla and [published in 2018 by The Upshot](https://www.nytimes.com/interactive/2018/upshot/election-2016-voting-precinct-maps.html); the 2016 and 2020 results are spatially joined by Census block-group

Please contact dear.upshot@nytimes.com if you have any concerns or questions about data quality, beyond the caveats we describe below.

## General caveats

- when possible we used official 2020 precinct boundaries provided by states or counties, but in most cases we generated the boundaries ourselves at the Census block-group level using L2 voter files; this results in generally accurate boundaries, but can be inaccurate in no- or very-low-population areas like business parks and rural land

## State by state data availability and caveats

|symbol|meaning|
|:----:|:------|
|✅|have gathered data, no significant caveats|
|⚠️|have gathered data, but doens't cover entire state or has other significant caveats|
|❌|precinct data not usable|
|❓|precinct data not yet available|

- `AL`: ❌ absentee and provisional results are reported countywide
- `AK`: ❌ absentee, early, and provisional results are reported district-wide
- `AZ`
- `AR`: ❓ precinct results not yet available statewide
- `CA`: ⚠️ does not readily publish statewide precinct-level data, so we have to collect results and boundaries county-by-county, where available
- `CO`: ✅
- `CT`: ⚠️ township-level results rather than precinct-level results
- `DE`: ✅
- `DC`: ✅
- `FL`: ⚠️ counties publish results individually, and some do not release precinct-level results; the state will release a standardized, statewide file in January
- `GA`: ✅
- `HI`: ✅
- `ID`
- `IL`: ⚠️ Cook County and City of Chicago results included, but statewide precinct results not yet available
- `IN`: ❓ precinct results not yet available statewide
- `IA`: ⚠️ Scott County does not provide machine-readable precinct-level data
- `KS`: ✅
- `KY`: ❌ half of the counties report votes countywide
- `LA`: ❌ early and provisional results are reported countywide
- `ME`: ⚠️ township-level results rather than precinct-level results
- `MD`: ✅
- `MA`: ✅
- `MI`: ⚠️ only certain counties report results at the precinct level
- `MN`: ✅
- `MS`: ❓ precinct results not yet available statewide
- `MO`: ❓ precinct results not yet available statewide
- `MT`: ✅
- `NE`: ✅
- `NV`
- `NH`: ⚠️ township-level results rather than precinct-level results
- `NJ`: ❌ no statewide reporting of precinct results, and most counties do not have precinct-level data due to their all-mail-voting operations this year
- `NM`: ✅
- `NY`
- `NC`: ⚠️ about half of the counties reported early, absentee, or provisional ballots countywide
- `ND`: ✅
- `OH`: ✅
- `OK`: ⚠️ Tulsa and Oklahoma Counties are excluded because ??
- `OR`
- `PA`: ⚠️ only certain counties report results at the precinct level
- `RI`: ⚠️ township-level results rather than precinct-level results
- `SC`: ❌ several types of ballots (failsafe, provisional, and failsafe provisional) are reported countywide
- `SD`: ⚠️ three counties reported absentee ballots countywide, and seven counties reported all votes countywide
- `TN`
- `TX`: ⚠️ does not readily publish statewide precinct-level data, so we have to collect results and boundaries county-by-county, where available
- `UT`: ❓ precinct results not yet available statewide
- `VT`: ⚠️ township-level results rather than precinct-level results
- `VA`: ❌ provisional and absentee votes are reported countywide
- `WA`: ✅
- `WV`: ✅
- `WI`: ✅
- `WY`

## Credits

- [Alice Park](https://github.com/umalice) and [Miles Watkins](https://github.com/mileswwatkins) compiled the precinct results, boundaries, and data processing
- [Benjamin Rosenblatt](https://twitter.com/BenJ_Rosenblatt) collected results and boundaries county-by-county in New York State
- [Charlie Smart](https://www.nytimes.com/by/charlie-smart) calculated `pct_dem_lead_change` and provided other technical support
- [Rachel Shorey](https://www.nytimes.com/by/rachel-shorey) and [Matthew Bloch](https://www.nytimes.com/by/matthew-bloch) calculated the precinct boundaries when official files weren't available
- [Amanda Cox](https://www.nytimes.com/by/amanda-cox) and [Kevin Quealy](https://www.nytimes.com/by/kevin-quealy) provided editorial guidance
- Additional scraping work by Rachel Shorey, [Quoctrung Bui](https://www.nytimes.com/by/quoctrung-bui), [Thu Trinh](https://github.com/trinhathu), and [Ben Smithgall](https://github.com/bsmithgall)
