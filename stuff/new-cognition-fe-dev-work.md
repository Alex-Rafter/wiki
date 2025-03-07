# New Cognition FE Dev Work

## Idea for a Way to Approach to the Cognition FE DEV work

Issues :
- Some initial work needed on style guide -> BS variables
- Design and BS / FE set up needs to be flexible so as to accommodate changes as Cognition is built out
- Codebase likely needs to be worked via Visual Studio.

Poss Solution :

Design -> Static HTML -> Razor Pages

- Focus on static html build out of components first
- A focus from design and FE on setting up things like the customised variables and util classes etc so that iteration can be done easily within the design constraints
- These then handed over for integration into the Razor pages / partials

Poss benefits :
- Speed - no set up issues with getting FE set up with Visual Studio
- Separates out work between FE and Tech - no working the codebase / component 'handover'
- Static html will be v easily shareable - either on a dev site or as static html embeds so that these can be interacted with / and discussed prior to integration