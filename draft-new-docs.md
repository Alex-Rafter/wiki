# Bluesky Elements Component Docs (Draft)

## :green_circle: Gallery

The bsk-gallery component is a responsive image gallery with optional thumbnail navigation.
It supports both standard and full-width designs, and uses the Slick Carousel library for sliding functionality.

### Mandatory attributes

- images: A comma-separated list of vehicle image names - set up so as to work with csv output by COG Literal eg.<br>
 ```images="<%= Images_51.Text %>"```.
- manufacturer: The name of the vehicle's manufacturer.
- model: The name of the vehicle's model.
- version: The name of the vehicle's version.
- mileage: The vehicle's mileage.

### Optional attributes

- is: used to set variations : default, thumbs, full-width
- thumbs-to-show: specifies the number of thumbnails to show in the thunbs slider. Default: 4.
- has-video : Used to set video icon overlay. Default: false.

### Methods

- galleryClick(el): Navigates to the slide corresponding to the thumbnail clicked.
- init(el): Initializes the gallery component based on the display mode (is) and sets the total image count.
- Utility Functions
- fullWidthInit(el): Initializes the full-width gallery and thumbnail navigation with Slick Carousel.
- standardInit(el, thumbsToShow): Initializes the standard gallery and thumbnail navigation with Slick Carousel.

### Usage

To use the bsk-gallery component, include the custom bsk-element tag in your HTML:

```html
<bsk-gallery
is="thumbs"
manufacturer="<%=Manufacturer.Text%>"
model="<%=Model.Text%>"
version="<%=Version.Text %>"
mileage="<%= Mileage.Text %>"
images="<%= Images_51.Text %>"
has-video="true"
>
</bsk-gallery>
```

## :green_circle: Video Banner

The bsk-video-banner element is used to display a responsive full-screen video background with an optional headline, synopsis, and call-to-action button. The video is played using YouTube's embedded player. You can use this in conjunction with a cms banner to populate the attributes such as video id and headline etc.

### Mandatory Attributes

- youtube-id: The YouTube video ID for the background video

### Optional Attributes:

- hero-bg-height (default: '100vh'): Set the height of the video banner on desktop - useful for setting the height to fill the viewport while accomodating the header nav above e.g ```hero-bg-height="calc(100vh - 135px)"```
- hero-bg-height-mobile (default: 'calc(100vh - 93px)'): Set the height of the video banner on mobile devices. Same as above, but accomodates the mobile header nav e.g ``` hero-bg-height-mobile="calc(100vh - 66px)"```
- headline: The headline text displayed on top of the video
- synopsis: The synopsis text displayed below the headline
- button-text: The text displayed on the call-to-action button
- button-url: The URL the button will link to

### Detailed explanation:

- The component displays a full-screen video background using YouTube's embedded player.
- The video automatically plays and is set to loop.
- The video banner can have an optional headline, synopsis, and call-to-action button displayed on top of the video.
- The component is responsive and adjusts its dimensions based on the screen size and aspect ratio of the video.

### CSS:

- Media queries are used to adjust the video and text dimensions and positioning for different screen sizes and aspect ratios.
- The headline and synopsis text use responsive font sizes and line heights.
- The video is displayed with a slightly reduced opacity (0.8) to improve text readability.

#### Methods:

init(el): Initializes the YouTube player by calling the 'ytInitMain()' function which wraps the code used with the YT-Player and YouTube APIs.

### Example:

```html
<bsk-video-banner
youtube-id="ywFnUyzBb6I"
hero-bg-height="calc(100vh - 135px)"
hero-bg-height-mobile="calc(100vh - 66px)"
headline="I am a headline"
synopsis="I am a test synopsis"
button-text="Search Our Stock"
button-url="https://www.blueskyinteractive.com"
>
</bsk-video-banner>
```


## :green_circle: Carousel Banner

The bsk-carousel-banner element is used to display a responsive slider of banners.
The carousel uses the Slick.js library to create a fading slide transition with navigation arrows and optional dots for navigation.

### Optional Attributes:

- dots (default: false)

Example:

### Detailed explanation:

- The component utilizes the Slick Carousel library to create a responsive and adaptive slider with a fading transition effect.
- The dots attribute can be set to "true" to enable dot navigation at the bottom of the slider. By default, the dots are disabled.
- The slider contains next and previous arrows for navigation between slides.
- The slider supports lazy loading for better performance with the 'ondemand' option.
- The component uses the 'adaptiveHeight' option to adjust the height of the slider based on the height of the current slide.

#### Methods
init(el): Initializes the Slick Carousel with the specified options and binds it to the '.slider' element.

### Example
```html
<bsk-carousel-banner dots="true"></bsk-carousel-banner>
```


## :green_circle: Carousel Banner Slide

The bsk-carousel-banner-slide element is used to display a banner slide, with options for video or image background. The component supports an optional headline, synopsis, and button with a link.

### Mandatory attributes:

- img-src

### Optional Attributes:

- headline
- synopsis
- buttonText
- link-url
- overlay (default: true)
- youtube-id

### Detailed explanation:

- If the youtubeId attribute is provided, the component will display a YouTube video as the background. The video will only play on larger screens (not xs or sm breakpoints).
- If no youtubeId is provided, an image will be used as the background. The image source is set with the img-src attribute.
- The overlay attribute is used to enable or disable the hero overlay. If it's set to true (default), a div element containing the headline, synopsis, and button will be shown on top of the background. This will be the most common useage when used with CMS banner text etc.

#### Methods:

- wrapInAnchor(el): Wraps the hero slide in an anchor tag if the overlay is disabled and a link-url is provided.
- initVideo(): Initializes the YouTube video if a youtubeId is provided and the current breakpoint is not xs or sm.
- init(el): Calls wrapInAnchor and listens for breakpoint changes to initialize the video if needed.

### Example :

```html
<bsk-carousel-banner-slide
youtube-id="ywFnUyzBb6I"
headline="I am the 1st video"
synopsis="I am a test synopsis"
button-text="Search Our Stock"
link-url="https://www.blueskyinteractive.com"
img-src="https://bluesky-cogcms.cdn.imgeng.in/media/kb4hlthl/group-inspire-ext-brand.jpg"
>
</bsk-carousel-banner-slide>
```

## :green_circle: CTA Section

The bsk-cta-section is a call-to-action (CTA) section element used to encourage user interaction. It features a two-column layout with an image on one side and a title, description, and an action button on the other side. The element is designed to be responsive and can be used for various CTAs. The default set up is provides a simple button to navigate to another page. There is also a part-exchange variant that outputs form fields and will redirect to a valuation page with vehicle reg passed in the url as a query string parameter.

### Mandatory Attributes:

- img-src
- title: The title text of the CTA section
- body-text: The description text of the CTA section
- btn-text: The text for the action button

### Optional Attributes:

- is: The type of CTA, either 'part-exchange' or any other string for a simple button
- aspect-ratio: The aspect ratio for the image in the CTA section (default is auto)
  Example for part-exchange form:

```html
<bsk-cta-section
  title="Get a Part-Exchange Valuation"
  bodyText="Enter your registration below to receive a free valuation for your vehicle."
  btnText="Get Valuation"
  img-src="https://bluesky-cogcms.cdn.imgeng.in/media/kb4hlthl/group-inspire-ext-brand.jpg"
  is="part-exchange"
>
</bsk-cta-section>
```

## :green_circle: CTA Section Full Width

The bsk-cta-section-full-width is a call-to-action (CTA) section element very similar to the standard bsk-cta-section but with different a layout. As above, the default set up is provides a simple button to navigate to another page. There is also a part-exchange variant that outputs form fields and will redirect to a valuation page with vehicle reg passed in the url as a query string parameter.

### Mandatory Attributes:

- img-src
- title: The title text of the CTA section
- body-text: The description text of the CTA section
- btn-text: The text for the action button

### Optional Attributes:

- is: The type of CTA, either 'part-exchange' or any other string for a simple button
- aspect-ratio: The aspect ratio for the image in the CTA section (default is auto)
  Example for part-exchange form:

### Example :

```html
<bsk-cta-section-full-width
  is="part-exchange"
  title="Part exchange your vehicle"
  body-text="Enter your registration number and mileage to get a free valuation today."
  btn-text="Get a Free Valuation"
  single="false"
  aspectRatio="16/9"
>
</bsk-cta-section-full-width>
```

## :green_circle: Offer Card
The bsk-offer-card element is used to display a single offer in a card format. The card includes an offer image, title, description, price, and an optional button for navigation. The offer description text is truncated to a maximum of 60 characters.

### Mandatory Attributes:

- img-src: The image URL for the offer card
- title: The title of the offer
- offer-text: The description text of the offer
- offer-url: The URL for the offer card and button (if provided)
- offer-price: The starting price for the offer

### Optional Attributes:
- button-text: The text for the button at the bottom of the card. If not provided, the default text is 'View Details'


### Example :

```html
<bsk-offer-card
  imgSrc="/path/to/image.jpg"
  title="Amazing Offer"
  offerText="Get an incredible deal on this exclusive product while supplies last."
  offerUrl="/amazing-offer"
  offerPrice="£199"
  buttonText="Learn More"
>
</bsk-offer-card>
```

## :green_circle: Inline Offer Card

The bsk-inline-offer-card element is used to display an offer card with relevant information such as the offer title, finance details, offer description, and related images. The card has a responsive design, with separate layouts for desktop and mobile views. The finance details are displayed in a table, and the text content can be truncated using the CSS property --line-clamp to limit the number of visible lines. The component includes two buttons, one to view all offers and the other to find out more about the specific offer. The primary button's link is set with the offer-url attribute, and the secondary button links to /offers by default.

### Mandatory Attributes:

- offer-title
- offer-finance-details
- offer-body
- offer-url
- offer-image

### Optional Attributes:

- line-clamp-length default is 3 lines

### Detailed explanation:

When using the Inline Offer Card with cms data, we need to get the offer-finance-details in the correct format. We have a helper function inside boilerplate's template logic directory directory.


```html
<!--#include file="/inc/modules/template-logic/return-key-value-pair.aspx" -->
```

Add the file as an include towards the top of your page, and the you can call the function like this:

```html
offer-finance-details="<%= If(offer.FinanceDetails.Any(), returnKeyValuePairStringified(offer.FinanceDetails), "") %>"
```

### Example with CMS Data:

```html
<bsk-inline-offer-card
  offer-title="<%= offer.Title %>"
  offer-finance-details="<%= If(offer.FinanceDetails.Any(), returnKeyValuePairStringified(offer.FinanceDetails), "") %>"
  offer-body="<%= offer.body %>"
  offer-url="<%= offer.CallToActionUrl %>"
  offer-image="<%=offer.Image %>"
  line-clamp-length="3"
>
</bsk-inline-offer-card>
```


## :green_circle: Breadcrumb
The bsk-breadcrumb element is used to create a breadcrumb navigation component that provides an easy way for users to navigate back to previous pages or sections. The breadcrumb includes a list of navigation items separated by a custom divider, and each item can include a font-awesome icon, text, and a URL for navigation. The color of the navigation items changes on hover, providing visual feedback for users.

### Mandatory Attributes:
- item-one The first breadcrumb item, must be provided in the following format: "[text, url]"

### Optional Attributes:
- item-two
- item-three
- item-four
- item-five
- divider: The glyph used as the breadcrumb divider (default is "/")*

*Additional breadcrumb items (up to 5 items total), must be provided in the same format as item-one: "[text, url]"


### Detailed explanation:
The component reads the values of the item attributes and pushes them into the items array.
The items array is looped through, and each item is rendered as a breadcrumb-item.
The first item in the breadcrumb can display a house icon using the fs-5 fa-light fa-house classes.
The last item in the breadcrumb is displayed with a different text color and without a hyperlink, indicating the current page.
The divider attribute is used to set the --bs-breadcrumb-divider CSS variable, which controls the character used as the breadcrumb divider.

### Example:

```html
<bsk-breadcrumb
  itemOne="[Home, /]"
  itemTwo="[Blog, /blog]"
  itemThree="[Category, /blog/category]"
  itemFour="[Article, /blog/category/article]"
  divider=">"
>
</bsk-breadcrumb>
```



## :green_circle: Simple Spotlight Group
The bsk-simple-spotlight-group element is used to create a group of spotlight items in a responsive layout. The group can be displayed either as a strip or grid. In strip mode, the items are displayed in a horizontal carousel, while in grid mode, they are displayed in a grid format. The carousel is initialized using the Slick library in strip mode and adapts to different screen sizes.

### Optional Attributes:
- is: The display mode for the spotlight group, either 'strip' or 'grid'

### Usage:
To use the bsk-simple-spotlight-group element, wrap a series of bsk-simple-spotlight components within the element and set the 'is' attribute to either 'strip' or 'grid', depending on the desired display mode.

### Example:

```html
<bsk-simple-spotlight-group is="strip">
  <!-- Nest simple bsk-simple-spotlight custom elements inside the group -->
</bsk-simple-spotlight-group>
```

## :green_circle: Simple Spotlight
The bsk-simple-spotlight element is used to display a spotlight item with an icon, title, and description. The spotlight item is designed to be responsive and adaptable to various layout styles such as 'strip' and 'bordered'. The spotlight item can also include an optional URL attribute to create a link for users to navigate to a specific page when clicked.

### Mandatory Attributes:
- title: The title of the spotlight item
- body: The description text of the spotlight item
- icon: The icon class for the spotlight item (eg using Font Awesome css classes)

### Optional Attributes:
- url: The URL for the spotlight item, which turns the entire item into a clickable link (default is null)
- is: The layout style for the spotlight item, accepts 'strip' or 'bordered' (default is none)

### Example

```html
<bsk-simple-spotlight
  title="Fast Service"
  body="Our team of experts ensures that your vehicle receives top-notch service in a timely manner."
  icon="fas fa-wrench"
  url="/services"
  is="strip"
>
</bsk-simple-spotlight>

```


## :car: UCR Grid
The bsk-ucr-grid element is used to display a responsive grid layout for vehicle cards. The grid layout adapts according to the screen size, displaying a single column on mobile screens, two columns on tablet screens, and three columns on desktop screens. The grid also supports two different view types: list view and grid view. The grid items have transition animations for both view types when they appear on the page.

### Optional Attributes:
- list-transition : add css transition between list and grid views (default is false)

### Example :

```html
<bsk-ucr-grid list-transition="true">
    <!-- Nest vehicle card custom elements or a cog repeater inside -->
</bsk-ucr-grid>
```

### Example with Nested COG Repeater

```html
<bsk-ucr-grid list-transition="true" >
  <COG:COGDynamicRepeater_V1
  ID="COGDynamicRepeater_V1"
  runat="server"
  DataType="UsedCarData"
  CarsPerPage="15"
  DynamicPagerID1="PagerBottom"
  DynamicPagerRangeID1="DynamicPagerRangeTop"
  Template="/COGTemplates/Vehicles/CarRepeat.ascx"
  />
</bsk-ucr-grid>
```

## :car: UCR List/Grid Toggle
The bsk-ucr-list-grid-toggle element is used to provide a toggle between list and grid views on used list pages. The toggle consists of two icons, one representing a list view and the other representing a grid view. The active view is indicated by the icon's color changing to primary.
The component listens for click events on the icons to toggle between list and grid views by updating the ```store.ucr.gridType``` value.


### Example:

```html
<bsk-ucr-list-grid-toggle></bsk-ucr-list-grid-toggle>
```

## :car: Vehicle Card

The bsk-vehicle-card is the main container element for the vehicle card custom elements, with the ability to switch between a grid view and a list view. The ```v-wrap``` directive used in the template causes all elements nested inside the component to be wrapped in the component's ```article``` tag. CSS classes are dynamically set based on the variant    and whether the grid type is set to 'list' or 'grid' (stored in global property ```store.ucr.gridType```). This allows the element and components nested within it to be styled properly for list view.

### Mandatory attributes :

No mandatory attributes are required for this portion.

### Optional attributes :

- theme

### Example:

```html
<bsk-vehicle-card theme="bp"></bsk-vehicle-card>
```

## :car: Vehicle Card Img

The img tag includes a lazyloaded class and is conditionally assigned the list-view class based on the gridType property in the store. The href attribute of the anchor tag is bound to a url variable, and the title attribute displays various vehicle information. The data-vehicle attributes contain additional vehicle data that can be used for tracking or other purposes. The &lt;noscript&gt; tag provides alternative content for browsers that do not support JavaScript.

### Mandatory attributes :

- img-src
- url
- regyear
- manufacturer
- model
- version
- price
- monthly
- stockid
- index

### Optional attributes :

- No optional attributes

### Example:

```html
<bsk-vehicle-card-img></bsk-vehicle-card-img>
```



## :car: Vehicle Card Body

The bsk-vehicle-card-img-body element creates a container element for the vehicle card text components. It makes use of the v-wrap directive to ensure all children are placed inside the component's html rather than outside of it. CSS classes are dynamically set on card-body element for both list view and grid view. This ensures the child components sit correctly inside the container for both of these views.

### Mandatory attributes :

No mandatory attributes are required for this portion.

### Optional attributes :

No optional attributes for this portion.

### Example:

```html
<bsk-vehicle-card-body></bsk-vehicle-card-body>
```

## :car: Vehicle Card Titles

The bsk-vehicle-card-titles element defines the vehicle card's title and sub-title, and allows them to be styled differently for both grid view and a list view. CSS classed are dynamically set based on the variant and whether the grid type is set to 'list' or 'grid' (variable - store.ucr.gridType).

### Mandatory attributes :

- manufacturer
- model
- version

### Optional attributes :

No optional attributes for this portion.

### Example:

```html
<bsk-vehicle-card-titles
  manufacturer="fiat"
  model="500"
  version="SE L S/S 5-Dr Estate"
>
</bsk-vehicle-card-titles>
```

## :car: Vehicle Card Pricing

The bsk-vehicle-card-pricing element is used to display vehicle pricing information.
It has has two possible variations : default and was-now-save.
BY default, the component will only show the price and monthly payment and will show these in row layout using flex.
If the is attribute is set to 'was-now-save', the element will display in a css grid layout using css variables that set col and row positions.
The values that show will be for previous price, current price, and savings, along finance price.
The vehicle price is formatted to include commas in the thousands place.
CSS classes are dynamically set based on the variant and whether the grid type is set to 'list' or 'grid' (variable - ```store.ucr.gridType```).

### Mandatory attributes :

- price
- monthly

### Optional attributes :

- is

### Example:

```html
<bsk-vehicle-card-pricing
  price="6,500"
  monthly="250"
></bsk-vehicle-card-pricing>
```

## :car: Vehicle Card Specs

The bsk-vehicle-card-specs element is used for displaying vehicle specifications. The template uses v-for to iterate over each specification and display it with its associated icon (if specified) in a span element. Conditional class bindings are used to set styles for list and grid view, and icon and pills styles.

### Mandatory attributes :

- specs : passed as list of items separated by a pipe character e.g ```specs="34230 miles|Petrol|Automatic"```

### Optional attributes :

- is
- icons : passed as list of items separated by a pipe character e.g ```icons="fas fa-tachometer-alt|fas fa-gas-pump|fas fa-cogs"```

### Example:

```html
<bsk-vehicle-card-specs
  is="pills"
  specs="34230 miles|Petrol|Automatic"
  icons="fas fa-tachometer-alt|fas fa-gas-pump|fas fa-cogs|fas fa-cogs"
>
</bsk-vehicle-card-specs>
```

## :car: Vehicle Card Actions

The button is linked to a URL that is passed through the 'href' attribute. The 'title' attribute displays the car's details. The anchor tag with button classes also contains several custom data attributes that hold tracking information about the vehicle.

### Mandatory attributes :

- img-src
- url
- regyear
- manufacturer
- model
- version
- price
- monthly
- stockid
- index

### Optional attributes :

- is

### Example:

```html
<bsk-vehicle-card-actions
  is="blank"
  url="http://boilerplate.dev.cogplatform.co.uk/"
  regyear="2015"
  manufacturer="fiat"
  model="500"
  version="Sport"
  price="6500"
  monthly="250"
  stockid="7262"
  index="1"
>
</bsk-vehicle-card-actions>
```

## :car: Vehicle Card Location
The bsk-vehicle-card-location element is used to display the location information on the vehicle card. It includes a location icon and a location name, both of which are linked to the specified URL. The location name is styled with a bold font weight by default.

### Mandatory Attributes:
- location: The name of the location
- location-url: The URL for the location link

### Example:

```html
<bsk-vehicle-card-location
  location="Bluesky | Coventry"
  location-url="www.google.com"
>
</bsk-vehicle-card-location>
```

## :car: Vehicle Card Image Count
The bsk-vehicle-card-img-count element is used to display the image count and video status on a vehicle card. The component is designed to be positioned absolutely, appearing at the bottom left corner of the vehicle card image. The image and video count are displayed as badges with icons and text, indicating the total number of images and whether there is a video available for the vehicle.

### Mandatory Attributes:
- img-count: The number of images for the vehicle
- has-video: A boolean indicating if there is a video available for the vehicle

### Example:


```html
<bsk-vehicle-card-img-count
  img-count="32"
  has-video="true"
></bsk-vehicle-card-img-count>
```

## :car:  Vehicle Card Sash
The bsk-vehicle-card-sash element is used to display a sash on a vehicle card. It is positioned absolutely over the card image. The sash consists of a ribbon with customizable text.

### Mandatory Attributes:
- text: The text to be displayed on the sash ribbon

### Example:

```html
<bsk-vehicle-card-sash text="reserved"></bsk-vehicle-card-sash>
```


## :heart: Shortlist Local Heart
The bsk-shortlist-local-heart element is used to display a clickable heart icon that allows users to add or remove a vehicle from their shortlist. The heart icon changes its appearance based on whether the vehicle is added to the shortlist or not. This component requires the vehicle's information to be passed in the data attribute.

### Mandatory Attributes:
- data: A JSON string containing the vehicle's information, including stockID, url, manufacturer, model, reg, year, price, image, colour, transmission, fuelType, and mileage. This is built to work in tandem with the boilerplate include :

```html
<!--#include file="/inc/modules/petite/shortlist-plus/props-object.aspx" -->
```

Add this towards the top of the repeater, and your can then use the PropObj variable in the data attribute e.g ```data="<%= PropObj %>"```

### Optional Attributes:
- child-class: A custom CSS class to apply to the heart icon

### Example:

```html
<bsk-shortlist-local-heart
data="<%= PropObj %>"
childClass="text-danger"
></bsk-shortlist-local-heart>
```


## :heart: Shortlist Global Heart
The bsk-shortlist-global-heart element is used to display a heart icon that represents the user's shortlisted items. The heart icon serves as a link to the shortlist page. The icon's appearance changes based on the count of shortlisted items. If the count is less than 1, the heart icon will be outlined, otherwise, it will be solid.

### Mandatory Attributes:
- None

### Optional Attributes:
- child-class: A custom CSS class to apply to the global-heart element if needed.

```html
<bsk-shortlist-global-heart childClass="custom-heart"></bsk-shortlist-global-heart>
```

## :green_circle: Read More Button

The bsk-read-more element is used to provide a 'read more' button that can be triggered to reveal additional text content. The button is designed to be responsive, appearing only on smaller screens.

### Mandatory Attributes:

- target: The id selector for the text element to be truncated and revealed
- chars: The maximum number of characters to display in the truncated text

### Optional Attributes:

- extra-class: Additional CSS classes to be applied to the 'Read more' button element

### Example:

```html
<bsk-read-more target="textToTruncate" chars="100" extra-class="foo"></bsk-read-more>
```

Here, the `bsk-read-more` component is used to target the `p` element within the `.card-text` element. The `chars` attribute is set to 100, meaning that only the first 100 characters of the text will be displayed until the 'Read more' button is clicked. An additional `extra-class` attribute is included to add the "foo" class to the 'Read more' button element.


## :green_circle: Clear Filters

The bsk-clear-filters element is used to display a button that resets all select options to their default position. It is designed to be used in conjunction with COG search filters.

### Mandatory Attributes:

- text: The text to display on the button

### Example:

```html
<bsk-clear-filters text="Clear All Filters"></bsk-clear-filters>
```
