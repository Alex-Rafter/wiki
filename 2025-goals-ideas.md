# Bluesky 2025 Goals and Project Ideas

- BP Static
- Productised Offering (premium template)
- Code Quality

## BP Static

### Goal ideas:

- By end Sept 2025 we ship : first full production site consuming data from APIs, submitting data to APIs
- By July 2025 we ship : BP Static v2 -  consuming data from APIs, submitting data to new APIs
- By June 2025 we ship : first full site consuming data from current COG BE, built into current COG BE
- By June 2025 : FE BP Static build team trained and shipping code - 2 FE build devs fully trained and able to build sites with the BP Static codebase
- By Feb 2025 we ship  : BP Static v1 -  consuming data from current COG BE, built into current COG BE

### Leveraging decoupled code

The prototype architecture is built with decoupling in mind from the start.

- API endpoint BE (code never touched by build devs)
- content store and automated build scripts etc (rarely touched by build devs)
- template codebase of pages,layout, components etc (frequently touched by build devs)


- The content store can consume data from any endpoint that can serve data in teh expected format - this decouples it from BE sources of data (ie COG or  API)
- The Template portion of the codebase (page, layout, components) used mainly by build devs / FE Team is decoupled from content store which fetches and transforms the endpoint data
This allows us to make changes to any of the 3 parts (API, content store, or templates) without disruption / major changes to the other.

#### Benefits of this architecture
- We can start building with BP Static now - allowing us to ship full FE prototypes and products early / prior to full API BE availability
- We can train build devs early / prior to full API BE availability  even as API work is being done / rolled out
- We can switch over to API endpoints as and when these come on line without majorly disrupting build devs

#### Time required for work.

#### BP Static v1 - initial 4 week (2 sprint) run
- sprint 1: content store work and automated build scripts etc
- sprint 2: initial bsk ui library setup, set up FE for use by build devs

**This 4 week work will likely not include Hypersearch move over. **

#### First full site - 4 weeks (with 2 build devs)
- Idea here is to train 2 build devs through the process of building and shipping this first product or site. They are then product leaders along with myself - making for mini team that can build, support others, etc

**Design work first (not inc in schedule)**

We then review at this point re: 2nd half of 2025 and the tine needed for the other goals

## Productised Offering (premium template)

The way BP Static pulls in data from an endpoint, links up very nicely with some of the patterns we have used  the 300 project for template site generation. An option is to bring the learnings from 300 project to BP Static and create a productised offering or premium template on top of BP Static.

Benefits
- Could give a way to get the new codebase generating revenue for the business quickly
- This could give us a way to build with the new codebase in a sandboxed way - as a product with definite start and end points and specific goals to measure on.

## Code Quality

Post build speed work, i think this is a key one we need to look at internally in FE. I think to do a good job on this, 'code quality' likely needs to be an overarching goal like we had with 'build speed' as an overall title for a bunch of different pieces of work we did inc bsk lib and the UI lib on top of this, build support and, etc

There are at least 2 areas to this i think: tooling and training.
- Tooling areas could include : leveraging shared deploy, setting up automated testing, linting + formatting,
- Training could include : team training, documenting our in-house coding / git practices, etc, build support, code review / deeper PR review for specific cases

### Benefits
- Fewer bugs / Higher quality of codebases
- Reduce common problems with our coding practices
- Better maintainability of sites
- Better trained core FE team on fundamentals
- Puts us in a better place to move to BP Static as a team


