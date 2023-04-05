# Cognition Style Guide FE Dev Feedback


## XD Links Referenced
- Style guide :  https://xd.adobe.com/view/ae691825-dd27-4699-9809-6abcc17231ce-fb3a/
- Design : https://xd.adobe.com/view/c7b890fc-eb32-41fc-89f2-4727c8298cfb-92eb/


#### Typography :
- margin - q if just bottom or margin all?
- Pls can we use rem not em to keep in line with bs
- q on heading line height?
- Can we pull out the key values for heading that we will set in bs type vars as css (eg line height) from xd not useful in this regard.

```css
$headings-margin-bottom:
$headings-font-family:
$headings-font-style:
$headings-font-weight:
$headings-line-height:
$headings-color:
```

*issue with line-height on wessex at 1.8

#### Spacing
Wessex 10px not small enough for lowest spacing level - can we make sure we have smaller ones than this on the scale for use as spacing utils. Is 6px smallest we will need in build? Poss good to have one smaller than this.
Are button spacings (x and y paddings) supposed matched to this spacing scale or separate? Getting y 11px and x 20px on standard button.

#### Borer radius
If only using the two sizes can we make explicit which should override which bs var? Eg should it just be 4px for all unless specified for the component?
$border-radius:
$border-radius-sm:
$border-radius-lg:

#### Components
pages 1 -5 - can't see any content on these pages?

#### Btn group
vertical variation looks a bit out possibly?

#### Cards
Did we get a decision with Lauren on future dev work re: card and carousels re: keep in or take out?
Could the click action in vehicle uploader be a good candidate for adding in under card components?

#### List Group and Modals
Are we using these as designed here in the current design? Eg modals look like this?
Eg AI image overlay border-radius is at 10px, but set as 4px on the modal component? or is this diff component?

#### Progress Bar
If we are only using custom do we need these other ones?
Can we add not to rm from the lib we ship instead

### tooltips
font sizings 14px and 16px?
Can we have examples of icon to action from design - icon / tooltip states would be useful to pull out here.

#### Tables
Will rm all other variants to reduce lib size?
YES - can rm the variants we are not using

##### Qs from referencing design to style guide

###### Design dashboard
- Upload buttons : is this a button component? Is this style used throughout the site? If so can we add to the style guide? Might be helpful to have in there?

###### upload imagery
- button click tooltip -> pull out as component for styleguide if used throughout site
- seems like the circle with icon is a motif? Component for style guide?

###### Uploader imperfection details
- the tags component - can we link to a bs component? or add this to style guide as a custom component as its used throughout parts of the site?

###### Blur Images
- the custom selectable cards - can we pull out into the styleguide with the default and selected states? eg also used on ai image generated step 2

### Side notes
icons to script - pull out for js import and css import for use in stylesheets

