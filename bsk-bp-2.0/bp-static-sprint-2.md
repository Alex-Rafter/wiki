
# BP Static: Sprint 2


Break the project down and make project boards for css and bsk? Not sure we need 2 boards tbh. 

Add tasks to the 1 project board then.

CSS: 
Need to bring everything over and have all the dir structure sorted.
Test.
Just use BS 5.1 for now: update packages as needed.

JS: 
Sort out if we are using BSK or Vue.
If we're using BSK, do everything downstream of that.


---
## Notes

### issues: 

- What to do about fallback values if we use this 'reactive' attr to load data? 
- What 

Do we need prepare reactive? Only if its loads of data. Otherwise just using teh stanard way we load stuff is prop better? 
The reactive as a way to load stuff still might have value? 



----

### Ideas and Patterns etc 

Coarse components 
We start coarse, and move to smaller component slices gradually as need arrives but not before: YAGNI. 

where to put bsk tags 
web components - when used, the bsk tag is always the outermost tag in an .astro component

#### Managing Variations: Slots First Approach

OOP as mental model - extending from base component
standard / base component 
use (named) slots with fallback content - that is the default content in the base component version
we always use named slots to make things explicit and clear
component variations then import the base version, and extend it by passing variations to the markup via slots. 
this allows us a lot of control without adding any (extra) logic to the component templates

----

Tidy up tasks

Back of the front
Add a services dir and maining to classes for API / data fetching and loading

Front of the front

what about naming conventions inside src dir
mv bsk lib inside src/\_lib
sort out the styles dir structure, dir names, etc
store moved to js dir?
clean up js dir bp mv over experiments etc?


-----
### src dir organisation

features
composables
layouts
pages
utils
assets
config
lib
services
test
components
features
stores
types

Good poss
https://fadamakis.com/a-front-end-application-folder-structure-that-makes-sense-ecc0b690968b

This is the one to follow
https://blog.webdevsimplified.com/2022-07/react-folder-structure/

src/\_lib
src/components
src/features
src/layouts
src/pages
src/utils?
src/modules?

src/\_lib
src/\_lib/bsk
src/\_lib/bsk-data (services)
src/\_lib/scripts

src/features
src/features/index.js
src/features/example-feature/
src/features/example-feature/index.js

(optional for code shared between components)
src/features/example-feature/components
src/features/example-feature/modules
src/features/example-feature/styles

(optional for code shared between components)
src/features/components
src/features/modules
src/features/styles

**modules**—JS-only code that can be reused anywhere in the given application
**store**

**Always using index.js/vue/jsx** — as the entry file into the given component or view


---

\_lib/
components/
features/
layouts/
pages/
store/
styles/
modules/

js/ or /modules/ or /composables/ or /utils?

Language changes 

features 
components 
pages
layouts

features makes sense as it fits with agile - building ech 'feature', updating each 'feature'
gives a shared language across the team and the codebase

Easy principles : 
start coarse - at the page level - easy, quick, don't over-optimise
move stuff from any page in src/pages into src/features when it is shared between pages
the first component is always called Base.astro - we extend from that with slots 
move stuff into src/components that is shared between features
