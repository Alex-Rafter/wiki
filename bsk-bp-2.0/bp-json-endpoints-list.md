## List of COG Endpoints

- website
- stock: 
	- summary
	- list and details?
- dealerships
	- summary
	- list and details?

## List of CMS Endpoints

- Top Level?
- Summary
	- The manufacturers they have
	- If they use the other things below. This would help to dynamically get data.
	- GetHomePage()? Or maybe that should be separated out?
- New Vehicles
	- Summary
		- Types of CMS Vehicles they use
		- List of franchises they have etc
		
- Careers
	- section
		- the list of all the careers list
		- section data
	- details data for each active career
		- Not sure if these should be their own thing or nested under section? WHatever is simplest - under section to start
- News
	- section / list
	- details data for each active + published 
	
- Offers
	- section / list
	- details data for each active + published 
	
- Testimonials
	- section / list
	- details data for each active + published 
 
- Pages
	- list of page-folders names (doesn't exist)
	- page details
	- Broken API for page folders
	
- Banners
	- list of banner-folders-names (doesn't exist)
	- banner collection details

- Vehicles: Car
	- Summary: 
		- Section data
		- List of franchises and their data (eg models list data)
		- Details  -each vehicle's details data
		
- Vehicles: Bike
	- As car
- Vehicles: Van
	- As car
- Vehicles: Motorhome
	- As car
	
- CmsBannersService
- CmsCareersService
- CmsMultiFranchiseNewCarService
- CmsNewBikeService
- CmsNewCarService
- CmsNewMotorhomeService
- CmsNewTruckService
- CmsNewVanService
- CmsNewsService 
- CmsOffersService
- CmsPagesService
-  CmsPanelService
- CmsTestimonialService

website: 
website name
GTM and other tracking details
address?
main contact info etc - what is the main number for the site eg for header etc?
finance provider: from list of options? Could use to set finance details etc
cookies management: is this cooikebot etc?

stock
https://bluebook.dev.cogplatform.co.uk/design/docs/cog/cog-field-reference/#used-vehicles

dealerships: 
https://bluebook.dev.cogplatform.co.uk/design/docs/cog/cog-field-reference/#dealerships
https://bluebook.dev.cogplatform.co.uk/design/docs/cog/opening-times/

*opening times only when opening times module is being used in thissite.config*

List of CMS Endpoints


----
Notes

do we need some sort of configuration file eg that says whether the site uses different admin modules like opening times or finance provider etc?

Tech Requirements: 
We need additional CMS APIs -
Banners etc - we need to be able to return a list of all the folders we have eg 
getAllBannerFolderNames - so these can be iterated over in subsequent fetches
getAllBannerFolderNames, getAllBannerFolderGuids, getAllBannerFolderNodeIds, getAllBannerTags

We need these for everything - eg for cmsPanels, etc we need to be able to get all of these references in a list
We need to be able to get panels by folderName and by their own panelReference

We may need to agree some naming conventions for cms content to be able to acurately test for, and pull in content that may or may not exist.

With current API, we can build out if we know ahead of time exactly what the pages are (or could be!). But what we can't do is pull a list of all the cms references, and dynamically use those. We have to statically set cms references eg we have to know the banner folder names ahead of time etc

Its really important we have a way of checking for and handling non-existant csm data. It should never error in these cases but fall back. 

We are doing this in the demo: 
banner folder names, page folder names, etc and we're using those to iterate over and get data.
Careers, news, offers, less of a prob as we can return all items as a list

---
Need to start simple and build up from there. 
CMS is the difficult one, not COG
COG: prioing modules we still use. 

Start with COG, then move to CMS. 

----
All endpoints (where poss): 

Summary 
Details

COG and CMS use same naming conventions but with diff data

COG
Summary 
Numbers - eg of stock, of dealerships,
list data: dealerships, 

Details
endpoint for detailed data

CMS
*likley to be contrived until we get extra data from CMS*
Summary 
section data
summary data - numbers etc
list data

Details
deeper details data for specific item


---
CogCmsPageAutoEdgeFields - Not included in CMS because the API docs error so i don;t know what the class properties are / can't access
Same : DataPointFields on (https://cogcms.co.uk/apihelp/api/CogCms.ClientModels.Pages.CogCmsPageModel.html)

---
To dynamically fetch careers items, new-cars, etc., just like we need a list of all pageFolder and bannerFolder names, we need to be able to get all the urls from the info/links section.

So, you can get a list of all pageFolders for example
And you can get a list of all that pageFolders pages with their urls - fur use with the urlOvervide.
We can construct this from the name though? 
We need to know if the url override field is completed. Because if it is we can't use that item.
Haven't we already covered that with pages though? Check that...
Yes! It works when you pass the careers url given with the list data. 

---

New Vehicles

Need something to sort out the urls - as they need re-ordering. Eg

Bad 
http://localhost:7842/api/cms/new-cars/model/?model_url=/mercedes-benz/new-cars/a-class/

Good

http://localhost:7842/api/cms/new-cars/model/?model_url=new-cars/mercedes-benz/a-class/


Then, need to check if that is a range page and get details for each model within a range.


---
BUGS

-----

\_cogCmsOffer.DataPointFields.SimilarManufacturers doesn't return any results when data is input into the fields?

---

34 Working endpoints : 

/api/cms/banners/details/default.aspx
/api/cms/banners/summary/default.aspx
/api/cms/careers/details/default.aspx
/api/cms/careers/summary/default.aspx
/api/cms/new-bikes/manufacturer/default.aspx
/api/cms/new-bikes/model/default.aspx
/api/cms/new-bikes/summary/default.aspx
/api/cms/new-cars/manufacturer/default.aspx
/api/cms/new-cars/model/default.aspx
/api/cms/new-cars/summary/default.aspx
/api/cms/new-motorhomes/manufacturer/default.aspx
/api/cms/new-motorhomes/model/default.aspx
/api/cms/new-motorhomes/summary/default.aspx
/api/cms/new-trucks/manufacturer/default.aspx
/api/cms/new-trucks/model/default.aspx
/api/cms/new-trucks/summary/default.aspx
/api/cms/new-vans/manufacturer/default.aspx
/api/cms/new-vans/model/default.aspx
/api/cms/new-vans/summary/default.aspx
/api/cms/news/details/default.aspx
/api/cms/news/summary/default.aspx
/api/cms/offers/details/default.aspx
/api/cms/offers/summary/default.aspx
/api/cms/pages/page/default.aspx
/api/cms/pages/page-folder/default.aspx
/api/cms/pages/summary/default.aspx
/api/cms/testimonials/summary/default.aspx
/api/cog/dealerships/details/default.aspx
/api/cog/dealerships/list/default.aspx
/api/cog/stock/details/default.aspx
/api/cog/stock/list/default.aspx
/api/cog/website/summary/default.aspx

---
BUG 

CMS

Why does the newCarSection() method take an argument but the newBikeSection() + newVanSection() doesn't?


Why does 

Class CogCmsNewCarManufacturer have SeoInformation but not  Class CogCmsNewMotorhomeManufacturer etc?


