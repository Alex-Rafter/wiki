
# New World Sprint 3 Planning

Keep it simple dude!
Don't add more, finish off what is there to a high standard - that is the overarching theme of the sprint. 
Documenting all the patterns is really key: 
folder structures, importing from barrel files, etc
making list of the codebase terminology 

--
## Codebase terminology 

Specific to the codebase
### Dir structure

### Component Coarseness Levels 
pages
features
components

Components
Base, server rendered component: 
Primary data source for text etc is static and dynamic data with Astro {}

ComponentClient
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


### Data Types 
static
dynamic
reactive

General
services
barrel files
internal 'public api'

