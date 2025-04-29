
I am modularising variable assignment via defineCollection function calls. 
To do this i am moving these to the relevant files within the src\_lib\content-config dir 
I have started this process and you can see examples in: 
src\_lib\content-config\banners.js
src\_lib\content-config\pages.js
src\_lib\content-config\panels.js

I want you to continue with the work i have started. 
You are to move the variable assignment via defineCollection function calls to within the relevant files as i have. 
Add the relevant schema that is hosued within the same file. eg the file
src\_lib\content-config\banners.js i have moved the const bannersSummary to this file, added the schema property and assigned BannersSummarySchema. 
Export those variables
Import them into the src\content.config.mjs
