# BSK Elements Release Notes


## Release Notes v.03

Here are the highlights of the latest release :

- ### Focus on bug squashing this release

- ### Store logic improvements

- ### New Components in the library
  - Gallery component and variants
  - Spotlight components and variants inc strip
  - CTA section full width + variant + variant


## Release Notes v.02

Here are the highlights of the latest release :

- ### New Components in the library
  - Offers card and variants
  - Inline offers card
  - Breadcrumbs and variant
  - Hero banners slider and slide, and variant
  - Hero banners video
  - Part exchange and variant

- ### Bluesky Elements CLI tool + docs
  - 2 way sync between bluesky elements repo and build. Pull the latest verison of elements into a build, push any edited components back to a special branch on bluesky-elements for feeding back in to the repo.
  - prevent naming duplications when making new components with by listing all elements in a build.
  - rapid component creation from your clipboard. With this you can simly copy any code block and the cli tool will automatically create a new component file in the correct directory, and add the include you need to your build.
  - Here is the [location for the docs](https://github.com/Alex-Rafter/wiki/blob/main/bluesky-elements-docs.md) until all is intergrated into the Vitepress docs site : https://github.com/Alex-Rafter/wiki/blob/main/bluesky-elements-docs.md

- ### Misc
  Loads of smaller changes and refactoring of the codebase. Some cool bits include :
  - Custom directive for nesting components inside of each other.
  - Helper attribute makes it easy to identify if the component is only a simple template or if it has any additional logic attched to it.
