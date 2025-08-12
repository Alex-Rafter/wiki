### Meeting Notes + Report Planning

Stuff to update on / things to cover 

- brief review of what we've been doing
- review of my time - not solely on this
- reputation api - high level and implications
- working group initial experiments / validating codebase and feedback
- post-experiment - bsk bring overs
- me back on sprint - new workflow for drafting UI
- Business objectives and shaping BP Static


### brief review (FE)

## what have we done
early codebase prototypes and demos
mocking responses protoype
built out interim endpoints and data fetch tooling
built out data load from flat files and data normalisation and validation 
build-time bsk-data loading and  transform APIs
run-time bsk-data loading and transform APIs - initial work
example pages and data load etc in use
alpha release v.01
reputation api (JCT not BP Static at present)
codebase testing / validating ideas, tooling, architecture decisions, etc with early testers  
bring over bsk ui library components and refactor for use in new codebase
building out new ui - components, page templates, etc 
new workflows for drafting components / page templates / UI 
	
## where are we at?
Off for New World for a bit for other work. Now back on - shipping again as of last week
Making versus mentoring

## reputation api (JCT not BP Static at present)

Successful sprint 
Currently on dev
Need small amount of time to refactor code following Dave's latest work 
Dispatch Worker architecture - working outside of BP Static. Maximise code-reuse (not 1 2 1 though)


## codebase testing / validating ideas, tooling, architecture decisions, etc with early testers
2x successful mini-sprints. 
link to brief: https://app.clickup.com/t/86c40x8vc
Both able to ship static components independently by end of the week
positive feedback on the DX

## DX Feedback Questions

## What has your experience using BP Static been like?

"Overall good. I wouldn’t say that any of my struggles during the week were related to understanding codebase or using astro. They were either design related or third party related (which I mentioned on Friday). I don’t think I had hard times to understand astro components after using vue, couldn’t say that it’s intuitive but it’s not that hard. One thing I noticed after going back to maintenance is that with new structure of page (everything is broken into components) it’s much easier to navigate / find things. While working on section I didn’t have full understanding of how to structure sections in components in terms of how small components should/could be (like should I keep button inside of card component of create a separate component for it), but I don’t think it would be a question when more things will be rolled over from current boilerplate as there will be more examples."

"It was enjoyable to work in a different way to how we usually work but it took me a while to get more comfortable using it. After spending a week on it, I started to understand how it worked a bit more."

## What works particularly well in the new codebase in your opinion?

"There were 2 things I liked particularly:

- No vb, which removes one step of complexity and will keep things more clear and organised.
    
- Scoping of css. Not thinking that I will break something somewhere else saves time."
    

"The way pages are laid out makes them a lot cleaner and having the styles and scripts in each component made for easier editing."

## Where do you notice particular improvements over our existing codebase(s) that you worked on previously?

"Work faster on local because don’t need to refresh the page to check changes in browser. This is a thing I didn’t realise until back to maintenance tasks, the impact of page autorefresh on save is big timesaver."

"I noticed that the speed when making small changes was a lot faster than the existing codebase. Also the way the pages are structured makes them easier to add/remove different components."

## What does the new codebase not work so well? Where could it be easier to use / where are improvements needed?

"There were a few cases when I wanted to use matchHeights, would be good if we could have it unless we want to stop using it."

"I couldn't see anything that needed improving once I spent more time working with it."

## What bugs did they find?

"Not found."

"I didn’t encounter any bugs."

## What else would you like to feedback at this point about the new codebase?

(No additional feedback provided)

"I can’t think of anything at the moment."

## What is not clear from the current documentation and training?

"Clear and understandable. Didn’t get suggestions for vs code extensions (./.vscode folder is not on github). Graph/sketch you draw for me to explain the logic behind what folder to put new components in (inside page’s _components, features, components) I think it could be helpful if you add it to docs."

"Everything was clear to me in the documentation and training."

## Key Learning and Takeaways

Confident we are on the right track in terms of DX
Early testing indicates we will be able to bring the team over to working in this new way (albeit it we are testing building static assets not with dynamic data yet)
Predictions in terms of workflow improvements eg speed of changes and value in component model validated in tests
Documentation / learning materials value (inc scaling training) and time allocation

	
## bring over bsk ui library components and refactor for use in new codebase

Natalia focus on BP Static
Working through a backlog of existing BSK UI Library components to a tight brief of how to refactir these for use in new codebase
Frequent support and in depth code review - training value, DX, acrghiture decisons in context here
Tight brief for this - link with documentation in terms of scaling training
2 x value : what is shipped, maintenance dev who is getting more expsoure to BP Static

## Next Steps with bring overs of bsk ui library

Step 2 for Natalia's work
Upgrades to existing components inc GSAP
Possible new custom directives input from me at this point

## My Time
Focus on support
Making versus mentoring revisit
Back to shipping!
Started on building out new ui - components, page templates, etc 
Experiments with new workflows for drafting components / page templates / UI 
Full demo of where we're at with UI at next meet
## Experiments with new workflows for drafting components / page templates / UI 

LLM-based drafting of new UI followed by manual review and refactoring*
Sandboxed role for LLM with manual pick up ensures quality
when is vibe-coding not vibe-coding?
Very early days but very exciting in terms outcomes
comparing outputs : very roughly 1 week of new starter time during DX testing manual coding equal to 90 mins with this new workflow
How : newer LLM based tooling, custom instructions, CI/CD, manual review and refactor 
LLM workflow implications - opps / fears / hype versus reality etc
Looking forward: UI Jams, drafting ideas and viewing in browser - CI/CD workflows
combining form data, context engineering and CI/CD
Needs: investment. Anthropic Claude / Claude Code, Open AI Codex, Dedicated CDN space
FE tooling on BP Static - open source
Again, early days - full demo of where we're at with UI at next meet and workflow demo / experiments coming



we have the early alpha release which covers mainly data duties : data fetch scripts, data loading in astro, build time data handling and bsk-data API, data transform API, initial / early work on front end data handling
now we have 
early contributors and feedback on working with the codebase 
some static assets / web design built through these 2 weeks of teaching and validating parts of the new codebase
an growing collection of out BSK UI library brought over and ready to hook up to data
the start of new ui components and page templates 
aims and objectives review - now versus future

### working group initial experiments

Overall succesful
Done with one maintenance dev without any besp or buold expeirences 
One experinced build dev

What was teh test?
link to brief: https://app.clickup.com/t/86c40x8vc

To build out purley static assets with a focus on web design (hardcoded / not hooked up to data sources)
To note DX feedback to questions and in catch ups

Both able to build: 


### what's next? 

bsk UI library bring over work (static) completed : simple then complex
new ui components and page templates (static) built out 
refactor data fetch and load codebase / tooling post-tech work related to interim end points 
dynamic data: 
bsk UI library components working with dynamic data sources
new ui library components working with dynamic data sources
new page tempkates and related components working with dynamic data sources
custom directive work : gsap and swiper

At this point we will have: 
an early BP 2.0 that can work with different site data sources to built static sites
pages: home, offers, news, page folders and pages, careers, vehicle details, new vehicle list, new vehicle details

what wont be covered at this point?


---

working group initial experiments - Feedback 

#### Natalia

What has your experience using BP Static been like?
Overall good. I wouldn’t say that any of my struggles during the week were 
related to understanding codebase or using astro. They were either design 
related or third party related (which I mentioned on Friday).
I don’t think I had hard times to understand astro components after using vue, 
couldn’t say that it’s intuitive but it’s not that hard.
One thing I noticed after going back to maintenance is that with new structure 
of page (everything is broken into components) it’s much easier to navigate / 
find things.
While working on section I didn’t have full understanding of how to structure 
sections in components in terms of how small components should/could be (like 
should I keep button inside of card component of create a separate component 
for it), but I don’t think it would be a question when more things will be rolled 
over from current boilerplate as there will be more examples.

What works particularly well in the new codebase your opinion?
There were 2 things I liked particularly:
No vb, which removes one step of complexity and will keep things more 
clear and organised.
Scoping of css. Not thinking that I will break something somewhere else 
saves time.

Where do you notice particular improvements over our existing 
codebase(s) that you worked on previously?
Work faster on local because don’t need to refresh the page to check changes in
browser. This is a thing I didn’t realise until back to maintenance tasks, the 
impact of page autorefresh on save is big timesaver.

What does the new codebase not work so well? Where could it be easier 
to use / where are improvements needed?
There were a few cases when I wanted to use matchHeights, would be good if 
we could have it unless we want to stop using it.

What bugs did they find?
Not found.

What else would you like to feedback at this point about the new 
codebase?

What is not clear from the current documentation and training?
Clear and understandable.
Didn’t get suggestions for vs code extensions (./.vscode folder is not on github).
Graph/sketch you draw for me to explain the logic behind what folder to put 
new components in (inside page’s _components, features, components) I think it
could be helpful if you add it to docs.

#### Oli

What has your experience using BP Static been like?
It was enjoyable to work in a different way to how we usually work but it took me a while to get more comfortable using it. After spending a week on it, I started to understand how it worked a bit more.

What works particularly well in the new codebase in your opinion?
The way pages are laid out makes them a lot cleaner and having the styles and scripts in each component made for easier editing.

Where do you notice particular improvements over our existing codebase(s) that you worked on previously?
I noticed that the speed when making small changes was a lot faster than the existing codebase. Also the way the pages are structured makes them easier to add/remove different components.

What does the new codebase not work so well? Where could it be easier to use / where are improvements needed?
I couldn't see anything that needed improving once I spent more time working with it.

What bugs did they find?
I didn’t encounter any bugs.

What else would you like to feedback at this point about the new codebase?
I can’t think of anything at the moment.

What is not clear from the current documentation and training?
Everything was clear to me in the documentation and training.

