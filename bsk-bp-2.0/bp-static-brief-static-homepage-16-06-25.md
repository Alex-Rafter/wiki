## 📋 Overview

We now have an alpha release of our new Boilerplate Static codebase. 
We are at a point where we need 2 things: 
- 🧪 To run early tests of FE Developers using the codebase, allowing us to check if the codebase meets its early goals, and so that we can collect feedback on how it is to work with in Practice. This will help steer the next round of iterations of the codebase development.
- 🧱 To build out new static UI assets that will complement those we can bring over from the existing boilerplate codebase. Because we have new patterns established, and new dependencies that we can leverage in Boilerplate Static, this is an opportunity for us to use those to address an issue with have with existing sites whereby the layout and design is generally good but there is a lack of interactivity and motion. To this end we want to build out new UI components that utilise GSAP and the suite of GSAP plugins.

## 📦 Deliverables

- A: 1 homepage (static) made up of a least 5 sections. The homepage should leverage core dependencies, inc GSAP for animations / transitions / motion
- B: 1 set of feedback notes covering each of the DX research questions
- C: 📋 Backlog list of bugs / items for improvement

### 🏠 A: Homepage

Sections should include : 
- 🧭 header
- 🎯 hero
- 🚗 used vehicle listing (cards)
- 📢 cta section or 📰 news listings (cards)
- 🔻 footer

- Header / Nav
	- At least one dropdown section at mobile and desktop should allow to present a small amount of data for cms new cars - eg list image, price, previoudPrice,  
	  inspiration / example 'our-cars' on top nav https://www.volvocars.com/uk/l/offers/ex30/ 

- Focal point section - should leverage gsap for interactivity and motion
	- Hero or banner sections within document flow

- Used Vehicle listing - should be built using existing BP vehicle card patterns with: 
	  - swiper JS for carousel using attributes to declaratively set instance properties 
	  - Although the cards exist already it would be good to add some new new (subtle) motion on intersect or interaction with the feature
	    
- News Listing - again, should be built from existing component patterns with the focus being on
	-  Swiper JS for carousel using attributes to declaratively set instance properties 
	- New interaction / transitions on interaction or intersect 
	
- Footer
	- Simple footer is fine

Additional if we have time
- 💡 Attention grabber lightbox/ modal with new transition defaults - not Bootstrap defaults
	- Clients often use these on home-page load
	- Use this as an opportunity to create an interesting visual effect on page load


### 🧪 B: DX Research Questions: 

- What has your experience using BP Static been like?
- What works particularly well in the new codebase your opinion? 
- Where do you notice particular improvements over our existing codebase(s) that you worked on previously?
- What does the new codebase not work so well? Where could it be easier to use / where are improvements needed?
- What bugs did they find?
- What else would you like to  feedback at this point about the new codebase?
- What is not clear from the current documentation and training?

### 📚 Prep Reading

https://github.com/MBBluesky/boilerplate-static  
https://astro.build/  
https://gsap.com/  
https://github.com/vuejs/petite-vue

### 💬 Additional:

This is is an opportunity to use new tools and feed in to the shaping of the new codebase. Giving detailed feedback about your experience and any problems with using Boilerplate Static is one of the highest value things you can do during this iteration so please keep notes for DX catch ups as you go.
