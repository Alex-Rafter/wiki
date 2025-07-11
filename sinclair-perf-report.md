

# Sinclair Performance Sprint Report (Part 1)

## Contents

- Intro
- Focus areas
- baselining
- work done
- performance improvements
- recommendations
- next steps

## Intro

To manage the deployment of such large scale changes alongside other client work, we have updated the plan for work and deployment of changes so as to split this into several parts. This report covers the first part of the work, which is likley contains the largest global changes to the site. Although the focus of this work is on the group and brand homepages, because it is the first part of the work, by its nature it contains the largest global changes to the site also.

## Baselining

With regards to performance improvement, we can only improve code that we manage and so to properly asses the impact of the perf work, the measurement of impact focuses on lighthouse scores and measures without 3rd party scripts enabled.

Method: 
Lighthouse CLI and Lighthouse CI used as core tools to measure perf.
Tests run 5 times and averages taken to rule out variance. This is important as results vary a lot in testing!

LIVE SITE with 3rd Parties

- "performanceScore": 34,
- "firstContentfulPaint": "5.8 s",
- "largestContentfulPaint": "11.5 s",
- "totalBlockingTime": "1249 ms",
- "cumulativeLayoutShift": "0.034",
- "speedIndex": "6.8 s",
- "timeToInteractive": "12.5 s"
- JS 1,362 kB transferred
- JS 2,221 kB resources

LIVE SITE without 3rd Parties

- "performanceScore": 53,
- "firstContentfulPaint": "5.1 s",
- "largestContentfulPaint": "8.9 s",
- "totalBlockingTime": "247 ms",
- "cumulativeLayoutShift": "0.066",
- "speedIndex": "6.4 s",
- "timeToInteractive": "9.1 s"
- JS 976 kB  transferred
- JS 1,004 kB resources

### Findings from baselining

3rd party code is having a significant impact on perf across the site. 

- **Performance Score:** Lowered by **33%** (from 53 down to 34)
- **JavaScript transferred size:** Added **386 kB** (~28% more JS)
- **JavaScript uncompressed resources:** Added **1,217 kB** (~55% more JS)
- **First Contentful Paint:** Slowed down by **0.7 s** (~12% slower)
- **Largest Contentful Paint:** Slowed down by **2.6 s** (~29% slower)
- **Total Blocking Time:** Increased by **1,002 ms** (~400% higher)
- **Time to Interactive:** Slowed down by **3.4 s** (~37% slower)
- **Speed Index:** Slowed down by **0.4 s** (~6% slower)

### Recommendations from Baselining

If perf is an important objective, an audit of all 3rd party code is needed and the size of the payload needs to be reduced significantly. The issue here is not only the size of the payload but the amount of resources required to execute this code which can block the main thread rendering html and styles (core to perf scores such as FCP and LCP)

## Sprint Work Done

- Initial changes to enable baselining with and without 3rd party JS 
- group homepage refactor
- audi homepage refactor
- byd homepage refactor
- cupra homepage refactor
- finance-and-leasing homepage refactor
- gwm-ora homepage refactor
- hyundai homepage refactor
- jaguar homepage refactor
- land-rover homepage refactor
- mercedes-benz homepage refactor
- seat homepage refactor
- skoda homepage refactor
- smart homepage refactor
- volkswagen homepage refactor
- volkswagen-vans homepage refactor
- JavaScript bundle refactoring
- SCCS/ CSS bundle refactoring
- New post-build step scripts and tooling to purge unused code
- Various refactors of non-bundled and inline scripts, fixing issues with script run orders and adding missing event listeners etc to ensure things run / query the DOM etc at the correct time
- Refactoring code into new includes to reduce code duplication 
- Reducing unused UI library code
- Refactoring carousel code across the site to optimise load times

## Performance Improvements

Test page `/perf-test`

used so we can control the cms banner folder to maintain consistency between tests 
content is changing frequently and scores varying with this 

perf scores 

## Recommendations

Audit of 3rd parties 
Move to Tiny Search BSK version - much smaller payload 0- given its on group and brand homepages optimising components for perf will help
Thin out CSS further

## Next Steps

UVD loading state for gallery - to reduce LCP
move pages css to their own css files rather than global bundle
