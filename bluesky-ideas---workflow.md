# Bluesky Ideas - Workflow

## Workflow idea :

Change the fe workflow at a macro level. Move (most) dev work upstream of builds, create more space for leaning into relative strengths, leverage scripting to automate much of the build process.

## Principles for the workflow:
- builds should be primarily exercises of configuration not development - followed by shorter stage of additional customisation on top as needed.
- dev work should happen upstream of builds.
    - dev work is slow. It takes time to QA and iron out bugs when building from scratch by its very nature.
    - We should capitalise on the man-hours we spend on custom dev work instead of losing it to one-offs as now on build
- Work should be split into discrete stages, and each can be tested and signed off :
- We can build on relative strengths within the team - eg css-focused devs would have a particular stage to lean into their expertise, logic-focused (vb and js) would also have a specific stage
- We can create more robust sites significantly more quickly with the same levels of differentiation (or more) than now

## Discrete stages of workflow :
- ui/ux design stage
- design to static html and / or vue template
- testing and amends
  - as we do now on buidlks but do at this much earlier stage and while partial / component is static html
    - This is potentially much easier to share / discuss and quicker to amend.
- partials / components made dynamic
    - eg add in literals, cog data, cms data and refs to cms modules, any server side logic etc
at this point the partial
    - At this point we have robust, well tested dynamic partials with default / BP styling, that 'just work' and can be dropped into any project.
- site configuration data is input via web-based form / forms.
    - This includes stuff like, webid, cms instance name and modules, design tokens for use in bs vars, etc.
    - This does not necessarily have to be a fe dev - could be projects for stuff like config data, and ux/ui for design tokens
    - This web-form is dynamic - it prompts the user eg after selecting a partial for a page, it prompts for the necessary dependent data such as cms node - eg choose a banner partial for home page -> prompted for cms banners folder id.
- A script is run locally by fe dev which then pulls in the config data and edits the codebase in line with the config, removing unused page variations, adding includes to match chosen partials, updates cms node refs, etc.
- The dev is then able to spin up locally and run checks, and add in any additional customisation, styling or any other parts that need to be done manually. This would be days of work rather than weeks / months as now.

The end product is the same as we produce now in so far as :
- its a cog site
- no need to completely change tech stack eg to spas etc to change to a new workflow
- siginificant time savings

Ideas for MVP / Lean testing
- We could do this with specific site pages sections first - no need to do all of BP in one go to test
- design tokens to bs vars.
- We can use the 300 as a testing ground for the workflow and build out from there : make one super robust site with a few options eg diff spotlight variations on home. Then config -> site build.

-----

## Other :
Working in partials and components
Partials are row-level strips of site?
components below that?
scss is located in the partial's dir - next to the aspx / html file. Not far away from it - easy then to rm code and add in code to a project (and to script this).
