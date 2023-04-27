# Bluesky Ideas - Workflow

## Workflow idea :

Change the fe workflow at a macro level

## principles :
- builds should be primarily exercises of configuration not development - followed by shorter stage of addiitonal customisation on top as needed.
- dev work should happen upstream of builds.
    - dev work is slow. It takes time to QA and iron out bugs when building from scratch by its very nature.
    - We should capitalise on the man-hours we spend on custom dev work instead of losing it to one-offs as now on build
- Work should be split into descrete stages, and each can be tested and signed off :
- We can build on relative strengths within the team - eg css-focused devs would have a particualr stage to lean into their expertise, logic-focused (vb and js) would also have a specifc stage-
- We can create more robust sites signifcantly more quickly with the same levels of differentiation (or more) than now-

## Descrete stges of workkflow :
- ui/ux design stage
- design to static html and / or vue template
- testing and amends
- partials / components made dynamic
    - eg add in literals, cog data, cms data and refs to cms modules, any server side logic etc
at this point the partial
    - At this point we have robust, well tested dynamic partials with default / bp styling, that 'just work' and can be droppped into any project.
- site configuration data is input via web-based form / forms.
    This includes stuff like, webid, cms instance name and modules, design tokens for use in bs vars, etc.
    The form is dynamic - prompting user to choose partials for each page, and requesting the neccessary refs on choice - eg choose a banner partial for home page -> promoted for cms banners folder id.
- Script is run locally by dev which pulls in the config data and edits the codebase removing unused page variations, adding includes, updating cms refs, etc
- The dev is then able to run checks and add addional styling or any other parts / customisations that need to be done manually. This would be days of work rather than weeks / months as now.

The end product is the same as we produce now in so far as :
- its a cog site
- no need to completely change tech stack eg to spas etc to change to a new workflow

Ideas for MVP / Lean testing
- We could do this with specifc site sections first :
- design tokens to bs vars.
- We can use the 300 as a testing ground for the workflow and build out from there

-----

## Other :
Working in partials and components
Partials are row-level strips of site?
components below that?
scss is located in the partial's dir - next to the aspx / html file. Not far away from it - easy then to rm code and add in code to a project (and to script this).