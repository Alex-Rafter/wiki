## ![:earth_africa:](https://a.slack-edge.com/production-standard-emoji-assets/14.0/google-medium/1f30d.png) FE Sprint 1 - Update

### Review of Objectives

1. ✅ BP JSON - finished.
    - ✅ All 'endpoints' needed completed in full and returning data in a coherent structure.
    - ✅ Any gaps identified eg for future Tech work we might need etc.
    - ✅  Additional notes on API spec for Tech requirements
2. ✅ Data Fetching to Local Static Files - finished.
    - ✅ All endpoint data can be fetched from endpoints - on script run.
    - ✅ All data can be correctly translated into format needed for content store - on script run
    - ✅ All edited data (JSON) stored locally - as flat file content store / db - on script run
    - ✅ GitHub Actions workflows set up to trigger these script runs on POST.
    - ❌ Additional GitHub Actions workflows set up to send the POST req eg on schedule or workflow dispatch (to mimic any future Tech webhook), etc
3. ✅ Data loading into Astro templates - finished
    - ✅All data from local content store can be loaded in to the components
    - ✅ We have a consistent, and simple API, for loading from our content store into components
    - ✅* Demos to show of pulling this data in and showing on the front end


###  Deliverables by the numbers: 

- 34 interim API endpoints built and fully functional
- In testing, as little as 6.5 seconds to pull in all site and cms with partial stock from (slow) localhost endpoints from in tests
- around 0.5 seconds to pull in partial data (eg to update content store with a full refresh of all cms careers data)
- 14 parts to new data loading API (eg careers, newCars, stock, etc), all finished and fully functional. 

###  Additional things built

- New API config pattern to make it easy going forward to update / maintain / extend data fetch scripts 
- A lot of optimisations in data fetching scripts to speed things up a lot at that stage of the process 
- CMS data matches techlabs CMS class structure for easy onboarding and onboarding for devs 
- Full auto-complete implemented for the new data loading API (should make on-boarding FE devs much easier)
- Initial work and example of data filtering and ordering API 
- Initial work on reactive data helper
- Loads of other stuff tbh this is just a sample! :)

###  Gaps identified

We need a couple of pieces of CMS work doing as prio for the new data fetch to work properly. These seem to me to be quite modest pieces of work (but obviously i don't know their codebase!). 

###  FE Requirements for Tech Work

#### We can't ship without: 

- A new 'GetAllBannerFolderNames()' method added to Class CmsBannersService
https://cogcms.co.uk/apihelp/api/CogCms.Client.CmsBannersService.html
This should return a list of all (published) banner folder names

- A new 'GetAllPageFolderNames()' method added to Class CmsPagesService
https://cogcms.co.uk/apihelp/api/CogCms.Client.CmsPagesService.html
This should return a list of all (published) page folder names. 
This should have an optional argument to set whether these are top level page folders only or not (ie not nested page folders when the argument is passed)

- A new 'GetAllPanelNodeReferences()' method added to Class CmsPanelService
https://cogcms.co.uk/apihelp/api/CogCms.Client.CmsPanelService.html
This should return a list of all the node references for all published panels

- A New UrlWithoutOverride Property (or similar name) added to all classes that have a 'Target Url Override' field (eg pages, offers, etc)
This new property should return the original url at all times, regardless of whether the 'Target Url Override' field has a value or not. It should always return the url that would be returned by the existing url property when the 'Target Url Override' has not been used.

#### We can ship but can't update data in a smooth way without: 

- webhooks that send POST request on data (CMS) change with the data type (careers, newCars, etc) as part of the payload
- webhooks sending POST requests for any other data sources we want to run builds on data change for - again with the data type as part of the payload
- CMS preview - likely important to stop very frequent builds being ran just to see what changes look like

#### API Endpoint Design Requirements and Data Structures

The data structures created for each of the 34 endpoints are all in git here: 
https://github.com/MBBluesky/cog_boilerplate/tree/bp-static/json-version/api


*Additional API Requirements Note

Ideally I think the most useful first thing from a FE POV would be for the endpoints just to return data in the same structure as now but with corrected data types. For example (some) Boolean values are store as String type with Capitalised "True" and "False" as the values. Another case is tildes (~) representing empty fields. 
In both cases of "~" and "False", these will be evaluated as truthy because a string with any non-empty value will evaluate to true, which could cause some confusion.
To correct types we will need to put an additional translation layer in place which will slow down either the data fetch or date load scripts, and could be a bit error prone.

Also, just to say at the moment the UCD endpoint is returning all fields listed in COG field refrenec which is probably a bit much. But we could slim that down a bit no doubt. I've done this to test bringing it all over.

We need the endpoints to return data in the current structure for the tooling to work.
The tooling is purposefully built to be very sensitive to the structure of the data it fetches and tries to load. This is by design and built into the core of Astro.  If it differs from what the current structure is, the tooling with error and exit.
Its inevitable that as we transition away from interim endpoints we will need to tweak the schema that is used to validate the data fetched (and the other bits of teh codebase downstream of this). We will probably need to review this endpoint by endpoint as they come on line. 


