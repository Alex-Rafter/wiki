
Hi Guys 

Below is an update on Sprint 2. The extra notes on deliverables and additional bits are only a small selection of things from the sprint tbh as there is just so much to talk about! I will save more specifics for the meet Tues. The TLDR is its going really well, and we're on track to have everything ready to bring the FE Devs on board for the 'learning by shipping' stage by end of Sprint 3.

FE New World : Sprint 2

**Review of Objectives**
 
🎯 Over-arching Aims for Sprint 2

- ✅ All building blocks in place for the 'front of the front' of the new codebase,  with a 'happy path' for each part of the front end that will be touched by FE devs.
- ✅ Existing CSS design system values, and tooling for pulling in UX/UI team's Bootstrap variables should work fully with new codebase.

Objectives:
High Level 
- ✅ We will be clear on where BSK is used and where Vue is used, with documented roles.
- ✅ All the specifics of using component model will be ironed out, with patterns code production ready, and with (initial) documentation.
  *One note here re: prod ready code, because I have written so much code over the sprint, some areas will need refactoring, and this will be a core focus of sprint 3*

CSS
- ✅ Bootstrap properly set up bringing in our existing scss modules, inc cms styles
- ✅ Integrate all existing scripts to pull in design tokens from form data
- ✅ Refactor of global styles - minimising global css bundle

JS Framework / JS Lib
- ✅ BSK 2.0 fully integrated using npm for package management
- ✅ BSK global state solution improved for use in Astro
- ✅ Additional BSK custom directives created
- ✅ Pattern established for converting build time data into reactive client side data

Refactoring
- ❌ Everything done so far is production ready and tested as much as is feasible at this stage.
  
Deliverables 
- Global store with Service Worker Pattern established for state management and data handling
- Codebase structure organised with initial documentation on each part to support this
- Many many patterns established for working with the codebase - this has been a major focus on the sprint - establishing how we work in each part of the codebase, why its structured the way it is, how we create / name / extend components etc. 
- Patterns and terminology established for the key areas of codebase that will be touched by front end devs - clarity on lots of q questions eg what goes where? how finely should components be sliced and when? when should we use BSK, and Vue components? 
- Patterns in place for how we build at page, feature, and component levels

Additional things built
- The big one here is i have implemented multi-threading to significantly improve performance when loading / querying / transforming data from APIs. This makes a dramatic difference - demo to show Tues!
- A really important win has been establishing a way of working which will allow us to leverage simple BSK components across nearly all of the codebase including when we are reactively rendering UI based on data loaded at runtime - this will help limit the API surface area front end devs will need to learn / interact with even when moving beyond solely statically rendered content (eg for filtering stock, news, etc)
- Alongside refactor of global css, i have integrated new tooling to purge all unused css minimising bundle size - the css is very lean now

Gaps identified
- No new gaps identified for BE / Techlabs work beyond those from last sprint and those discussed at prototype meets 