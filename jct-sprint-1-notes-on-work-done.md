
# JCT Sprint 1 Notes on Work Done

remove all images from root
rm unused service worker
clean up root dir: images, etc
rm unused js
tidy up js-head: remove unused scripts, make sure on globally included scripts are in global includes
tidy up js-foot: remove unused scripts, make sure on globally included scripts are in global included
webpack: move over to use webpack chunks / load page-specific js using webpack chunks

clean up all unused scss and css
We need to check which styles are still used and which are stale
For each scss module under the src dir in the codebase:
use VS Code global search for each of the main style rules in the scss module
If the styles are not used in the codebase's template files (aspx, ascx, bsk .html) or cms grid, remove these from the codebase (you can always comment out while testing before finally removing)
*If the scss modules uses the SASS ampersand syntax, you may need to edit the string you search for so that it is the full selector as it would be compiled*

only include global styles in global stylesheet 
for each scss module check the content and where thos rules are used. Unless they are truly global, 
compile the scss module to css 
move that new css module to the css directory instead
load these small modules of css on each page


remove unused icon libraries, and icon imports
remove unused fonts, 
ensure globally included assets are actually used globally. If not, include only on pages used. 
*This could apply to fonts, icons, third party scripts, etc*

For any third party scripts not needed on page load / used further down the page, consider loading with intersection obvs

Ensure banner images use imgengine cdn and correct query string params
make sure imgengine query string params are optimised for size images take up
consider using sriv profile to set sizings and cache times for sirv assets
add correct fetchpriority attributes for images inc banner images - eg fetchpriority=high to first banner img

PRECONNECT
Add prreconnect for main resources eg 
`<link rel="preconnect" href="https://bluesky.sirv.com">`

STYLES
remove unused bootstrap varabiables / styles - eg do we actually *need* all the table variants on this site? 
rm unused bootstrap modules, plugins

SCRIPTS
Ensure scripts do not block main thread - eg use defer attribute on sripts like jquery


IMAGES
remove any unused images - eg no images in project root
check image sizes / reszie asstes - are the imgs appropriately sized for the space they take up on the page? Are the optimised with cdn etc? 


tidy ups
rm unused pages
rm any redirected pages not in use


--------------------------------------
--------------------------------------
