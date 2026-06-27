# Thomas' Election Analysis Page

## 2026 Colorado Primary
[2026 Primary Turnout Map](https://twbruce4.github.io/CO_2026_Primary_Turnout.html)

[Turnout % by Precinct](https://twbruce4.github.io/CO_2026_Primary_Turnout_PCT.html)

#### Methodology

I've gathered all publicly available voter turnout files (CE-068 and CE_068c) from Colorado counties that provide them (thanks to the elections offices of Broomfield County, Boulder County, Denver County, Adams County, Arapahoe County, Jefferson County, Douglas County, and Mesa County for making these files available). The above map will be updated daily with the most recent files from each county.

Here is the methodology I used for assigning partisanship:

1. Voters registered with a party are automatically assigned to that party, since Colorado has semi-open primaries (i.e., if you are registered as a party you can only vote in that party's primary).
2. If `VOTED_PARTY` is specified in the voter file, the voter is assigned that party since that is what ballot they officially turned in. Some counties either do not fill in this field, or don't immediately provide it on the day the ballot is turned in - this is why the percetage of Unaffiliated (UAF) voters varies significantly by county.
3. For counties that provide a registration history (EX-005 Voting History List), I pulled in the most recent partisan registration if they were previously registered as a party but are now UAF.
4. For counties that provide registered voters (all but Mesa County), I created a list of addresses with at least 2 registered voters, and at least 80% registered to one party. The assumption here is that unaffiliated voters at that address will vote the same way as the partisan ones ("address" includes unit number for multi-family buildings, so it should be sufficiently limiting to families/roommates).

#### Analysis and Forecasting

Here is what I can confidently say about this election. Turnout so far is strong for Democrats. The counties I've included in my map went 60% for Kamala Harris in 2024, and primary turnout is upwards of 6 points better than that for Democrats. This could be for a couple reasons:
- Energized Democratic voter base. Considering Gov. Polis' recent pardon of Tina Peters, left-leaning voters reason to be upset and motivated to turn out against establishment candidates.
- "Crossover voting" behavior, i.e., Republican-leaning Unaffiliated voters voting their Democratic ballot, or Republican voters changing their registration to Democrat for the primary. This is not usually a common phenomenon, but conditions are ripe for it - Republicans only have one competitive statewide primary (Governor), where Victor Marx has a comfortable lead according to recent polling. If this is happening, it's tough to predict how they would vote - do they choose the most centrist candidate possible? Choose the most extreme with the hopes that it gives them a better chance of winning the general? There are different strategies there.

As far as forecasting, primary elections are much more difficult to forecast than general elections. Partisan data alone is not necessarily useful, and a lot of assumptions need to be made based on polling, regional turnout behavior, etc. It's even more difficult in this case since I don't have any data from El Paso County (the most populous county in Colorado, containing Colorado Springs and suburbs).

One thing that helps is that Colorado voter files contains voter year of birth. A [recent poll of the gubernatorial race](https://coloradosun.com/2026/06/25/phil-weiser-michael-bennet-poll-colorado-governors-race/) showed current Attorney General Phil Weiser slightly ahead of current Senator Michael Bennet in the gubernatorial race, with his strength among young voters having a big impact. Using the poll preferences by age group, we can estimate how Weiser is doing in the counties where I have data.

| Age  | DEM | REP | UAF/Other | Weiser %[^1] | Bennet %[^1] |
|-------|-----|------------|---|------|--------|
| 18-45 | 64,751  | 17,392   | 7,888 | 74.7%  |    25.3%    |
| 45-64    | 69,322  | 36,444   |7,459 |  54.7%  |   45.3%   |
| 65+ | 129,296   |  76,300    | 11,364   | 38.6% |  61.4%   |
[^1]: Percentages of decided voters in the Public Policy Polling poll

If we allocate UAF voters to DEM at the same ratio as the DEM/REP partisan ratio, that gives us this result:

| | Votes| % |
|----|-----|----|
| Weiser |  146,186   | 51.9%   |
| Bennet |  135,436   | 48.1%   |

It's important to note that this is only the turnout in the counties I've pulled data for, and it's pretty safe to say that Weiser will do better in these counties than in the rest of the state (the crosstabs in the PPP poll show as much - Weiser is strongest in Denver metro Congressional districts and the I-70 mountain corridor. So one conclusion here is that the estimate for "Already Voted" in the poll seems to be biased towards Weiser. However, there are still a few days of voting left. The last few days of voting in Colorado are typically:

- high turnout relative to previous days
- more Dem-leaning than previous days
- more young voters than previous days

The following plot shows the increase over time of younger voters (<45 years old) as a percentage of the Democratic electorate:

<img width="589" height="507" alt="image" src="https://github.com/user-attachments/assets/c93e4707-564b-4c19-8afd-1ab9a765e27d" />

If this trend continues, then Weiser will improve his margins in the coming days, but it's hard to say if it will be enough to overcome his deficits in rural areas. And again, Colorado Springs will be a factor - his chances will hinge on being at least somewhat competitive there.

At this point, I think realistically that it's a 50/50 race. Without seeing statewide data and/or more robust polling (there have only been a handful of polls on this race, all with wildly different conclusions), it's hard to draw any conclusions besides the fact that turnout is high.

Other races to watch include:

- CO-01: 30-year incumbent Diana DeGette vs. left-wing, Bernie Sanders-endorsed challenger Melat Kiros. Kiros is currently the betting market favorite, and after the recent results in New York City, she may be able to build on that momentum.
- US Senate: Julie Gonzales challenging incumbent John Hickenlooper. Gonzales has a much bigger fundraising deficit than Kiros and needs to spread it statewide, putting her at a big disadvantage. However, some polls have shown her within striking distance if she can reach enough voters.
- CO-08: Manny Rutinel and Shannon Bird battle for the chance to challenge Rep. Gabe Evans in Colorado's most purple congressional district.
- Attorney General: Current Secretary of State Jena Griswold is the favorite here because of name recognition, but with 4 viable candidates anything could happen.
- Republican Governor: Are the polls right about Victor Marx? I haven't seen ad presence of any Republicans here, oddly enough the only sign I've seen was for Scott Bottoms, who is a distant 3rd in the polls.
