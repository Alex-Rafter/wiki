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
<bsk-read-more target="#textToTruncate" chars="100" extra-class="text-primary"></bsk-read-more>
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

## :green_circle: Footer Address

The bsk-footer-address element is used to display an address in the footer of the website.

### Mandatory Attributes:

- address: The address to display

### Optional Attributes:

- is: The alignment of the address (default is left-aligned, can also be set to centered)

Example:

```html
<bsk-footer-address
  address="123 Main St, Anytown USA, 12345"
  is="centered"
>
</bsk-footer-address>
```
## :green_circle: Footer Bottom

The bsk-footer-bottom element is used to display text, such as a  copyright message, at the bottom of a page. The component is designed to be responsive and can be customized with different background colors.

### Mandatory Attributes:

- none

### Optional Attributes:

- none

### Slots:

The component includes one slot for inserting the text:

- text-content : The text to be displayed in the footer. This can include HTML markup.

### Example:

```html
 <bsk-footer-bottom>
          <span slot="text-content">
            &copy; <%=Year(Now)%> <%=Website_Name.Text%>, Automotive website provided by <a
              href="https://www.blueskyinteractive.co.uk" target="_blank" rel="noopener">Bluesky Interactive Ltd</a>
          </span>
        </bsk-footer-bottom>
```## :green_circle: Footer Contact

The bsk-footer-contact element is used to display contact information in the footer section of a web page. The contact information includes an email address and telephone number, with clickable links for both.

### Mandatory Attributes:

- email: The email address to display
- telephone: The telephone number to display

### Optional Attributes:

None.

Example:

```html
<bsk-footer-contact
  email="info@example.com"
  telephone="+44 1234 567890"
>
</bsk-footer-contact>
```
## :green_circle: Footer Content

The bsk-footer-content element is used to display content in the footer section of a webpage. This component can be customized by setting different attributes on the element.

### Optional Attributes:

- title: The title of the footer content (default is null)

### Slot:
- content: All content inside the bsk-footer-content tag will be displayed in the footer content area.

#### Centered Links

When the bsk-footer-content element has the attribute "is" set to "centered-links", it will display any list items inside the element as centered links in a row.

Example:

```html
<!-- Default footer content -->
<bsk-footer-content>
  <h6>About Us</h6>
  <p>Learn more about our company and what we do.</p>
</bsk-footer-content>

<!-- Footer content with centered links -->
<bsk-footer-content is="centered-links" title="Connect With Us">
  <ul>
    <li><a href="#">Facebook</a></li>
    <li><a href="#">Twitter</a></li>
    <li><a href="#">Instagram</a></li>
  </ul>
</bsk-footer-content>
```
## :green_circle: Footer

The bsk-footer element is used to display a footer at the bottom of a web page. This component can be used with two different styles (centered and standard) and includes up to four slots to display content in each style. The slots allow developers to customize the content without the need for affecting the CSS, and they are responsive to different screen sizes.

### Mandatory Attributes:

None.

### Optional Attributes:

- is: A string value indicating whether the footer should be displayed in a centered style ('centered') or default.

### Slots:

- one : The content to be displayed in the first column of the footer.
- two : The content to be displayed in the second column of the footer.
- three: The content to be displayed in the third column of the footer (only for the standard style).
- four: The content to be displayed in the fourth column of the footer (only for the standard style).
- bottom (mandatory): The content to be displayed at the bottom of the footer.

### Example:

```html
<bsk-footer>

  <div slot="one">
      <bsk-footer-logo img-src="https://bluesky.sirv.com/Websites/cog_boilerplate/images/logo.png" img-alt="logo">
      </bsk-footer-logo>
      <bsk-footer-address address="Boilerplate UI,123 Somewhere Street, Town,City,CH34 F45"></bsk-footer-address>
      <bsk-footer-contact
      email="info@boilerplate.co.uk"
      telephone="01284 623127"
      ></bsk-footer-contact>
      <bsk-footer-socials
      facebook="https://www.facebook.com/BlueskyInteractive"
      twitter="https://twitter.com/Bluesky_Int"
      linkedin="https://www.linkedin.com/company/bluesky-interactive-ltd"
      youtube="https://www.youtube.com/user/BlueskyInteractive"
      instagram="https://www.instagram.com/blueskyinteractive/"
      >
     </bsk-footer-socials>
  </div>

  <div slot="two">
    <bsk-footer-content title="Quick links">
        <ul class="mb-0" slot="content">
          <li><a href="/used-car-results.aspx">Used Vehicles</a></li>
          <li><a href="/new-cars/">New Vehicles</a></li>
          <li><a href="/offers/">Offers</a></li>
          <li><a href="/service/">Servicing</a></li>
          <li><a href="/business/">Business</a></li>
          <li><a href="/news/">News</a></li>
          <li><a href="/contact-us/">Contact Us</a></li>
        </ul>
      </bsk-footer-content>
  </div>
  <div slot="three">
      <bsk-footer-content title="Legal">
          <ul class="mb-0" slot="content">
            <li><a href="/pages/terms-and-conditions/cookie-policy/">Cookie Policy</a></li>
            <li><a href="/pages/terms-and-conditions/data-protection-policy/" data-anchor="#">Data Protection Policy</a></li>
            <li><a href="/pages/terms-and-conditions/terms-and-conditions/" data-anchor="#">Terms &amp; Conditions</a></li>
            </ul>
        </bsk-footer-content>
  </div>
  <div slot="bottom">
      <bsk-footer-bottom>
          <span slot="text-content">
            &copy; <%=Year(Now)%> <%=Website_Name.Text%>, Automotive website provided by <a
              href="https://www.blueskyinteractive.co.uk" target="_blank" rel="noopener">Bluesky Interactive Ltd</a>
          </span>
        </bsk-footer-bottom>
  </div>
</bsk-footer>
```
## :green_circle: Footer Links

The bsk-footer-links element is used to display a list of links in the footer section of a webpage.

### Optional Attributes:

- title: The title to be displayed above the list of links

### Slots:

- list: A slot where the list of links can be inserted

Example:

```html
<bsk-footer-links title="Useful Links">
  <ul slot="list">
    <li><a href="#">Link 1</a></li>
    <li><a href="#">Link 2</a></li>
    <li><a href="#">Link 3</a></li>
  </ul>
</bsk-footer-links>
```
## :green_circle: Header

The bsk-header element is used to display a header for a website or application. The header includes a logo or brand name, navigation links or buttons, and a hamburger (collapsed) menu button. The header can be configured to have a centered or left-aligned layout, to include a shortlist icon or to expand.

### Mandatory Attributes:

- img-src: The URL of the image to use as a logo
- img-width: The width of the logo image
- img-height: The height of the logo image

### Optional Attributes:

- is: The layout of the header ('centre' or 'left')
- offcanvas: The ID of a Bootstrap offcanvas element to use as the navigation menu
- expand: the breakpoint at which the header nav should expand from a hamburger menu to the nav
- hamburger: The type of hamburger menu to use ( eg 'arrow', 'slide', 'spin', or 'elastic')
  - To change the hamburger
    - uncomment the **one** hamburger style you want to use from ```src\scss\app\theme\components\hamburger\index.scss```
    - add that hamburger style to the ```hamburger``` attribute of the ```bsk-header``` element eg ```hamburger="spin"```

#### Slots:

- left-nav: Navigation links to display on the left (for 'centre' layout only)
- nav: Navigation links to display (you could use an include inside this slot to keep your code clean)
- shortlist: A slot designed for the shortlist global-heart component icon

Example:

```html
 <bsk-header hamburger="spin" expand="navbar-expand-xl"
    img-src="https://bluesky.sirv.com/Websites/cog_boilerplate/images/logo.png" img-width="183" img-height="40">
    <span slot="shortlist">
      <bsk-shortlist-global-heart child-class="text-dark"></bsk-shortlist-global-heart>
    </span>
    <span slot="nav" class="ms-auto">
      <!--#include file="/inc/components/nav.aspx" -->
    </span>
  </bsk-header>
```
## :green_circle: Header Top

The bsk-header-top element is used to display a top header bar on large screens where the left and right sections can be customized as slots.


### Slots:

- left-nav: The contents of the left section of the header
- right-nav: The contents of the right section of the header

### Logic:

No mandatory or optional attributes are required for this component.

### Example:

```html
<bsk-header-top>
  <div slot="left-nav"><a href="/">Home</a></div>
  <div slot="right-nav">
    <ul class="list-inline">
      <li class="list-inline-item"><a href="/login">Log in</a></li>
      <li class="list-inline-item"><a href="/register">Register</a></li>
    </ul>
  </div>
</bsk-header-top>
```## :green_circle: Header Top Socials

The bsk-header-top-socials element is used to display a list of social media icons in the top header section of a webpage. These icons link to the corresponding social media profiles or pages.

### Mandatory Attributes:

None.

### Optional Attributes:
- facebook: The URL for the Facebook page/profile
- twitter: The URL for the Twitter page/profile
- linkedin: The URL for the LinkedIn page/profile
- youtube: The URL for the Youtube channel/profile
- instagram: The URL for the Instagram page/profile

Note: At least one of the optional social media URLs must be provided to display the social media icons in the header.

Example:

```html
<bsk-header-top-socials
  facebook="https://www.facebook.com/myFBpage"
  twitter="https://twitter.com/myTwitter"
  linkedin="https://www.linkedin.com/in/myLinkedIn"
  youtube="https://www.youtube.com/myYouTubeChannel"
  instagram="https://www.instagram.com/myInstagram"
>
</bsk-header-top-socials>
```
## :green_circle: Grid Masonry

The bsk-grid-masonry element is a container used to create responsive grid layouts with a masonry effect for 5 items. The grid can be reorganized into a slick carousel on smaller screens by setting the slick-mob boolean attribute to true.

### Optional Attributes:

- slick-mob: Boolean attribute, set to true to reorganize the grid into a slick carousel on smaller screens

### Slots:

- grid: The items to be displayed in the grid. Each item will automatically span 1 row and 1 column at all breakpoints.

Example:

```html
<bsk-grid-masonry slick-mob="true">
  <div>Item 1</div>
  <div>Item 2</div>
  <div>Item 3</div>
  <div>Item 4</div>
  <div>Item 5</div>
  <!-- ... -->
</bsk-grid-masonry>
```
## :green_circle: Page Hero Image

The bsk-page-hero-img component is used to display a hero image at the top of a page, along with a title and body text. This component is designed to be responsive and includes two versions lg and default. The lg variant also includes css animation on load.

### Mandatory Attributes:

- img-src: The URL for the hero image
- title: The title to display on the hero image
- body-text: The body text to display on the hero image

### Optional Attributes:

- is set to 'lg' to use the lg version of the hero image (default is false)
- hero-height: Set the height of the hero image when using the is="lg" variant. Set in 'vh' units (default is 75vh)

Example:

```html
<bsk-page-hero-img is="lg" title="Insurance"
    body-text="All our staff are given first class training and resources to ensure that we provide customers with an exceptional experience, whether you are buying a car, having a service, looking for parts and accessories or using our manufacturer approved body shops."
    img-src="https://cogcms.co.uk/media/h0ibudi2/tyre-bg.jpg" hero-height="50vh" class="d-block mb-5">
</bsk-page-hero-img>
```
## :green_circle: Page Hero

The bsk-page-hero element is used to create a hero section at the top of a page. The hero section includes a title and two slots for body copy. Using slot, the hero component can be used in tandem with cogcms data sources (see example below).

### Mandatory Attributes:

- title: The main title of the hero section.

### Optional Attributes:

None

### Slots:

- body-copy-one: The first body copy slot for additional text content.
- body-copy-two: The second body copy slot for additional text content.

### Example (using component to create a hero section for offers list page):

```html
  <bsk-page-hero
    title="<%= _cogCmsOffersSection.Title %>"
    offer-count="<%=offerCount%>"
  >

  <span slot="body-copy-one">
    <%= _cogCmsOffersSection.Body.replace("<p>", "<p class='mb-2'>") %>
  </span>

  <span slot="body-copy-two">
      We have <strong class="text-primary"><%=offerCount%></strong> offers available
      <% If Request.QueryString("filter") <> "" Then %>
      that match your search category
      <% End If %>
  </span>

</bsk-page-hero>
```
## :green_circle: Shortlist Ajax

The bsk-shortlist-ajax element is used to display a list of vehicles that a user has shortlisted. The list is dynamically generated using an AJAX request to the server and allows the user to easily remove items from their shortlist. After the ajax request, the component will add the shortlisted cars into the DOM.

### Mandatory Attributes:

No mandatory attributes are required.

### Optional Attributes:

No optional attributes are available.

Example:

```html
<bsk-shortlist-ajax></bsk-shortlist-ajax>
```
## :green_circle: Shortlist Comparison Table

The bsk-shortlist-compare element is used to display a table comparing multiple vehicles that have been shortlisted. The array of these shortlisted cars is housed in the the shortlist store ```src\js\app\bluesky-elements\store\shortlist.js```. A row is added to the table for each shortlised car using vue template syntax ```v-for="car in store.sl.cars"```

The table includes columns for an image, vehicle information, and specifications.

Vehicles can be removed via the trash-can icon. An event listener  ```@click.prevent="store.sl.rmFromSummary(car, $el)"```, triggers the remove method in the shortlist global store ```src\js\app\bluesky-elements\store\shortlist.js``` when the icon is clicked.

### Attributes:

This component does not require any attributes.

### Example:

```html
<bsk-shortlist-compare></bsk-shortlist-compare>
```

#### *Note: This component requires data to be provided from the store, which is not shown here.
## :blue_circle: Shortlist Summary

The bsk-shortlist-summary element is used to display a summary of the cars saved in the user's shortlist. If no cars are in the shortlist, the element displays a message indicating how to add cars to the shortlist. With cars in the shortlist, the element displays the car image, title, version, and a button to view the car by default. The template can be customized ```inc\bluesky-elements\shortlist\bsk-shortlist-summary.html```.

### Conditional Rendering:
- When no cars are in the shortlist, render a message indicating how to add cars to the shortlist
- When there are cars in the shortlist, render a card for each car in the shortlist.

### Optional Attributes:

- None

### :

```html
<bsk-shortlist-summary></bsk-shortlist-summary>
```
## :red_circle: Grid Slick-to-Row

The bsk-grid-slick-to-row element is used to display all child elements in a grid, and automatically adjusts to a carousel on mobile / smaller screens.
The component initializes a slick slider if the window width is less than 992px by default. This can be updated in
```/src/js/app/bluesky-elements/state-objects/grid/slick-or-grid.js```

### Slots:

- grid: The slot for the elements to be displayed in the grid.

### Optional Attributes:

- is="large": By default, each grid-child takes up 3 columns of a 12 col grid. With this attribute, each element takes up 6 columns when the screen size is greater than 992px.

Example:

```html
<bsk-grid-slick-to-row>
  <div v-for="item in items" class="card">
    <!-- card content -->
  </div>
</bsk-grid-slick-to-row>
```

```html
<bsk-grid-slick-to-row is="large">
  <div v-for="item in items" class="card">
    <!-- card content -->
  </div>
</bsk-grid-slick-to-row>
```
## :green_circle: Grid Section Spacer

The bsk-grid-section-spacer element is used to create vertical gaps between sections in a grid layout.

### CSS Custom Properties:

- --component-gap: Determines the size of the gap between sections (default is 3rem)

### Usage:

The bsk-grid-section-spacer element should contain any elements that need to be spaced apart in a grid layout. By default, a gap of 3rem is added between each child element. To exclude an element from the gap, add the class "exclude-from-gap" to that element.

Example:

```html
<bsk-grid-section-spacer>
  <div>Section 1</div>
  <div>Section 2</div>
  <div class="exclude-from-gap">Section 3 (with no gap below)</div>
  <div>Section 4</div>
</bsk-grid-section-spacer>
```
## :blue_circle: Thumbnail

The bsk-thumbnail element is used to display a clickable image. The 'hover' variant that presents additional information in a hover state. The thumbnail is designed to be responsive and includes optional logo-links eg for use on multi-franchise sites.

### Mandatory Attributes:

- link-url: The URL to navigate to when the thumbnail is clicked
- img-src: The URL of the thumbnail image
- title: The title of the thumbnail information

### Optional Attributes:
- is="hover": Enables the hover variant of the thumbnail component
- body : The synopsis text to display below the title on hover (used only in the hover variant)
- img-src-medium: The medium-sized URL of the thumbnail image
- img-src-large: The large-sized URL of the thumbnail image
- line-clamp-length: The number of lines to display in the synopsis text (default is 2)

### Slots:

Additional links can be included below the title using the slot `logo-links`. This can be used with any html but is designed to be used with the ```<thumbnial-logo-links>``` component.

Example:

```html
 <bsk-thumbnail is="hover" link-url="/new-cars/"
   img-src="https://bluesky-cogcms.cdn.imgeng.in/media/vw5b5nnl/new-cars.jpg" title="Thumbnail Title"
   body="Thumbnail Body Text">

   <span slot="logo-links">
     <bsk-thumbnail-logo-links
       logo-link-one="audi, /audi/new-cars/, https://bluesky.sirv.com/Websites/Mon%20Motors/logos/audi.png"
       logo-link-two="ford, /ford/new-cars/, https://bluesky.sirv.com/Websites/Mon%20Motors/logos/ford.png"
       logo-link-three="seat,/seat/new-cars/, https://bluesky.sirv.com/Websites/Mon%20Motors/logos/seat.png"
       logo-link-four="skoda, /skoda/new-cars/, https://bluesky.sirv.com/Websites/Mon%20Motors/logos/skoda.png"
       logo-link-five="volkswagen, /volkswagen/new-cars/, https://bluesky.sirv.com/Websites/Mon%20Motors/logos/volkswagen.png"
       logo-link-six="volvo, /volvo/new-cars/, https://bluesky.sirv.com/Websites/Mon%20Motors/logos/volvo.png">
     </bsk-thumbnail-logo-links>
   </span>

 </bsk-thumbnail>
```
## :green_circle: Thumbnail Logo Links

The bsk-thumbnail-logo-links element is used to display a row of logos with associated links in a thumbnail format.
The row is designed to be responsive, displaying a maximum of 6 logos per row, with the logoCols attribute controlling the number of columns displayed.

### Mandatory Attributes:

- logo-link-one: The CSV-format string representing the link details for the first logo
- logo-link-two: The CSV-format string representing the link details for the second logo
- logo-link-three: The CSV-format string representing the link details for the third logo

### Optional Attributes:

- logo-link-four: The CSV-format string representing the link details for the fourth logo
- logo-link-five: The CSV-format string representing the link details for the fifth logo
- logo-link-six: The CSV-format string representing the link details for the sixth logo

- logo-cols: The number of columns to display in the row (default is 6)

**Note**: The CSV-format string for each logo link should have the following structure: ```"alt text,image URL,link URL".``` For example :
```logo-link-one="audi,/audi/new-cars/,https://bluesky.sirv.com/Websites/Mon%20Motors/logos/audi.png"```

Example:

```html
 <bsk-thumbnail is="hover" link-url="/new-cars/"
   img-src="https://bluesky-cogcms.cdn.imgeng.in/media/vw5b5nnl/new-cars.jpg" title="Thumbnail Title"
   body="Thumbnail Body Text">

   <span slot="logo-links">
     <bsk-thumbnail-logo-links
       logo-link-one="audi, /audi/new-cars/, https://bluesky.sirv.com/Websites/Mon%20Motors/logos/audi.png"
       logo-link-two="ford, /ford/new-cars/, https://bluesky.sirv.com/Websites/Mon%20Motors/logos/ford.png"
       logo-link-three="seat,/seat/new-cars/, https://bluesky.sirv.com/Websites/Mon%20Motors/logos/seat.png"
       logo-link-four="skoda, /skoda/new-cars/, https://bluesky.sirv.com/Websites/Mon%20Motors/logos/skoda.png"
       logo-link-five="volkswagen, /volkswagen/new-cars/, https://bluesky.sirv.com/Websites/Mon%20Motors/logos/volkswagen.png"
       logo-link-six="volvo, /volvo/new-cars/, https://bluesky.sirv.com/Websites/Mon%20Motors/logos/volvo.png">
     </bsk-thumbnail-logo-links>
   </span>

 </bsk-thumbnail>
```
