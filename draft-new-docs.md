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

## :green_circle: Hero Banner Video

The bsk-hero-banner-video element is used to display a responsive full-screen video background with an optional headline, synopsis, and call-to-action button. The video is played using YouTube's embedded player. You can use this in conjunction with a cms banner to populate the attributes such as video id and headline etc.

### Mandatory Attributes

- youtube-id: The YouTube video ID for the background video

### Optional Attributes:

- hero-bg-height (default: '100vh'): Set the height of the hero banner on desktop - useful for setting the height to fill the viewport while accomodating the header nav above e.g ```hero-bg-height="calc(100vh - 135px)"```
- hero-bg-height-mobile (default: 'calc(100vh - 93px)'): Set the height of the hero banner on mobile devices. Same as above, but accomodates the mobile header nav e.g ``` hero-bg-height-mobile="calc(100vh - 66px)"```
- headline: The headline text displayed on top of the video
- synopsis: The synopsis text displayed below the headline
- button-text: The text displayed on the call-to-action button
- button-url: The URL the button will link to

### Detailed explanation:

- The component displays a full-screen video background using YouTube's embedded player.
- The video automatically plays and is set to loop.
- The hero banner video can have an optional headline, synopsis, and call-to-action button displayed on top of the video.
- The component is responsive and adjusts its dimensions based on the screen size and aspect ratio of the video.

### CSS:

- Media queries are used to adjust the video and text dimensions and positioning for different screen sizes and aspect ratios.
- The headline and synopsis text use responsive font sizes and line heights.
- The video is displayed with a slightly reduced opacity (0.8) to improve text readability.

#### Methods:

init(el): Initializes the YouTube player by calling the 'ytInitMain()' function which wraps the code used with the YT-Player and YouTube APIs.

### Example:

```html
<bsk-hero-banner-video
youtube-id="ywFnUyzBb6I"
hero-bg-height="calc(100vh - 135px)"
hero-bg-height-mobile="calc(100vh - 66px)"
headline="I am a headline"
synopsis="I am a test synopsis"
button-text="Search Our Stock"
button-url="https://www.blueskyinteractive.com"
>
</bsk-hero-banner-video>
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

The bsk-cta-section is a call-to-action (CTA) section element used to encourage user interaction. It features a two-column layout with an image on one side and a title, description, and an action button on the other side. The element is designed to be responsive and can be used for various CTAs. The default set up is provides a simple button to navigate to another page. There is also a part-exchange varianyt that outputs form fields and will redirect to a valuation page with vehicle reg passed in the url as a query string parameter.

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
  is="part-exchange"
>
</bsk-cta-section>
```

## :green_circle: Inline Offer Card

The bsk-inline-offer-card element is used to display an offer card with relevant information such as the offer title, finance details, offer description, and related images. The card has a responsive design, with separate layouts for desktop and mobile views. The finance details are displayed in a table, and the text content can be truncated using the CSS property --line-clamp to limit the number of visible lines.

The bsk-inline-offer-card component displays an offer card with the provided information. The card has separate layouts for desktop and mobile devices. The offer details are displayed in a table, and the description can be truncated using the CSS property --line-clamp to limit the number of visible lines. The component includes two buttons, one to view all offers and the other to find out more about the specific offer.

### Mandatory Attributes:

- offer-title
- offer-finance-details
- offer-body
- offer-url
- offer-image

### Optional Attributes:

line-clamp-length (default is not set)

### Example:

```html
<bsk-inline-offer-card
  offerTitle="Sample Offer"
  :offerFinanceDetails="[{'Finance option 1': '£500'}, {'Finance option 2': '£1000'}]"
  offerBody="This is a sample description for the offer."
  offerUrl="/offer-url/"
  offerImage="/path/to/offer-image.jpg"
>
</bsk-inline-offer-card>
```

## :green_circle: Inline Offer Card

The bsk-inline-offer-card element is used to display a special offer in a card format.
The card includes an offer title, finance details, offer description, and buttons for navigation. The card is designed to be responsive, displaying the title and image differently on mobile and desktop screens. The offer description text is truncated using -webkit-line-clamp to control the number of lines displayed, which can be set via the lineClampLength attribute.

### Mandatory Attributes:

- offer-title: The title of the offer
- offer-body: The description text of the offer
- offer-finance-details: An array of key-value pairs representing the finance details for the offer
- offer-url: The URL for the 'Find out More' button
- offer-image: The image URL for the offer card

### Optional Attributes:

- line-clamp-length: The number of lines to display in the offer description text (default is 3)

### Example:

```html
<bsk-inline-offer-card
  offerTitle="Special Offer"
  offerBody="Limited time offer on this amazing vehicle. Don't miss out!"
  offerFinanceDetails="[{'Deposit': '£1,000'}, {'Monthly Payment': '£250'}]"
  offerUrl="/special-offer"
  offerImage="/path/to/image.jpg"
>
</bsk-inline-offer-card>
```