
# New World Sprint 3 Planning

Keep it simple dude!
Don't add more, finish off what is there to a high standard - that is the overarching theme of the sprint. 
Documenting all the patterns is really key: 
folder structures, importing from barrel files, etc
making list of the codebase terminology 

--
## Codebase terminology 

Specific to the codebase
### ./src Dir Structure

Go over each and put what each may contain and not contain and why

./\_lib
./components
./features  
./layouts
./pages
./store
./styles
./workers

### Pages

#### Valid Folders in a Page Folder


```txt
./_components
./any-sub-pages
```

### Features

#### Overview
A bit like includes or partials

#### Modularity and Isolation
Each feature is isolated from every other feature that they share the ./src/features folder with.
They cannot 'talk' to each other or share code in any way.

The only code that a feature can import is:
shared code in the ./src directory's folders
external dependencies (npm packages etc)

eg 
a feature can import a common component like a vehicle card 

./src/components/

or perhaps a utility function that is designed to be used in many places
./src/modules/utils/helper.js

But it cannot import another feature's code. 

If something needs to be shared between two features? Great, move that code up a level to the ./src/components or ./src/modules etc and import it into both the original feature and the new feature you are creating.

This ensures code always flows downwards which helps keep code understandable - we know what is shared code and what is not. If we were to delete a feature folder we can be confident it would not break other features in other folders :)

Each feature then contains everything needed for its cod to run correctly: its components, styles, and javascript, etc. 
For that reason, you can think of any feature as being like a micro version of its ./src folder. It have its own components folder, and could have many other folders you will be used to from the ./src directory. 
### Valid Folders in any Feature

```txt
./_lib
./components
./modules
./store
./styles
./workers
./index.js
```

#### Exposing Features with an Exit Point
You can think of each feature as being walled off from everything else except for its one exit point.
All of the code in any features folder can only ever leave via this one exit point, and nowhere else.

All code you want to expose to the rest of the codebase **must** be exported via an index.js file in the feature's root

❌ Bad 

`./src/pages/some-page/index.Astro`

```js
import Feature from "@features/some-feature/components/Base.astro"
```

✅ Good 

`./src/features/some-feature/index.js`

```js
export default as Feature from "./components/Base.astro"
```

`./src/pages/some-page/index.Astro`

```js
import Feature from "@features/some-feature"
```


About the index.js
This is a simple barrel file used to create a single point from which features can be imported by the rest of the codebase.

*./src/features/some-feature/index.js*
What must this dir contain at a bare minimum?
- ./components
- Base.astro (and any variations of the main feature file)
- index.js
  
And at it maximum? 


### Components

### Component Coarseness Levels 
pages
features
components


### Static Endpoints
As well as fully built pages, we build assets for 2 different kinds of static endpoint: 

- data endpoints
- partials endpoints
##### Data
Pre-built static JSON data served from `/endpoints/data` endpoints

eg the endpoint `/endpoints/data/news-items` might serve all of the site's published news articles as JSON data
#### Partials
Pre-built static HTML served from from `/endpoints/partials` endpoints
these partials are full pages and are served without any doctype declaration, head or body tags etc

eg the endpoint `/endpoints/partials/news-cards` might serve 
a collection of all of the site's published news articles as pre-built HTML cards
### Component Naming Conventions 

Components
Naming: ComponentName
Base, server rendered component: 
Primary data source for text etc is static and dynamic data with Astro {}

Client Components
Naming: ComponentNameClient
Follows the same as base component that it is extended from but with the prefix 'Client'
eg 
Base Astro component 
VehicleCard
Client Component Variant
VehicleCardClient

Primary data source for is reactive data with BSK
template is wrapped in a template tag with an ID
component logic points to that template tag with the $template property
you will find these instantiated within the markup of feature or page
### Components +Features Naming
Always Base.astro
followed by named variants that extend the base
Follows similar pattern to default.aspx or index.html 

*Related*
How we build base components, and extend for variations with slots to override fallback content
### Global State
store
worker

*Related*
How we nest BSK: 
As few as possible and why (not needed like in COG platform to pass data to components)
start at page level, then add just one at feature level, then add to components lastly and only as needed
Use v-scope to scope to smaller areas with new data and small inline template directives for FE

### Data Loading Libs
@bsk-be-data: COG, CMS
@bsk-fe-data: COG, CMS, filters 

### BSK: 
refers to our in-house UI library built on top of petite vue and web components
essentially all core functions of petite vue are the same, with bsk components acting like [petite vue components with a template](https://github.com/vuejs/petite-vue?tab=readme-ov-file#components-with-template)

### Data Types 
- #### static: 
hardcoded values in markup
- #### dynamic: 
data determined at build time. Variables primarily declared or imported in front matter in Astro files
- ####  reactive: 
data determined at runtime. Variables primauily set in BSK component logic and v-scope directives

General
services
barrel files
internal 'public api'
worker
buildtime
runtime
v-scope
