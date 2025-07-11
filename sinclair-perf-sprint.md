

## Goal
The core aim of this sprint is to improve the performance of the website from a speed and technical SEO point of view.

## Day 1

Measure baseline
Write notes on brief to feedback re: constraints with /search page etc
These can be done with measurements for an initial docs to give to Simi

### Initial Notes

Generally this looks no worse than any other site we build tese days - so we are likley limited without purge - 
Can we use purgse css? This would be a big win if we can get it working!
WHat JS can we get rid of
Its prob important to feed back that the imporvements are unlkiley to be anywhere like the ones we got on JCT - without a fundamental change in how we build
What dev tools stuff can we leverage to get insight into what is unused? 

TS BSK Version as a first reocmmendation for imporving homepage perf
HTMX - are we even using this? That can probs go.
GTM / scripts loaded via GTM accounts for nealy half of home js payload

We need baseline scores with and without the third paryy stuff

Baseline

Homepage 



---
Ideas 

Make a testing repo / env that i can use with Sinc but also other sites in the future so i don;t have to re-do all this.

I need to set up the Sin repo in such a way that i can baseline with and without third parties.
This gives us a truer reflection of what we control perf-wise and recommendations. 

Hero LCP is bad. BSK makes this worse. If i can address this with a fallback until load or similar this might help.



---

Get baseline scores 

normal 
without third parties 
run 3 to 5 times 
average scores
report back on these
report findings, recommendations, and constraints

