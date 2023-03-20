# Draft New Docs

# Components Notes

---

bsk-gallery

The bsk-gallery component is a responsive image gallery with optional thumbnail navigation. It supports both full-width and standard display modes, and uses the Slick Carousel library for sliding functionality.

Attributes
- thumbs: (Boolean) Determines whether to display thumbnail navigation or not. Default: true.
- thumbsToShow: (Number) Specifies the number of thumbnails to show in the navigation. Default: 4.
- imgCount: (Number) The total number of images in the gallery. Default: 0.
- images: (String) A comma-separated list of image names.
- manufacturer: (String) The name of the vehicle's manufacturer.
- model: (String) The name of the vehicle's model.
- version: (String) The name of the vehicle's version.
- mileage: (String) The vehicle's mileage.

Methods
- galleryClick(el): Navigates to the slide corresponding to the thumbnail clicked.
- init(el): Initializes the gallery component based on the display mode (is) and sets the total image count.
- Utility Functions
- fullWidthInit(el): Initializes the full-width gallery and thumbnail navigation with Slick Carousel.
- standardInit(el, thumbsToShow): Initializes the standard gallery and thumbnail navigation with Slick Carousel.

Usage
To use the bsk-gallery component, include the custom bsk-element tag in your HTML:

<template bsk-element="bsk-gallery">
  <!-- Gallery component code -->
</template>


---

Hero Banner Video
The bsk-hero-banner-video element is used to display a responsive full-screen video background with an optional headline, synopsis, and call-to-action button. The video is played using YouTube's embedded player.

Attributes:

- youtubeId: The YouTube video ID for the background video
- heroBgHeight (default: '100vh'): The height of the hero banner on desktop
- heroBgHeightMobile (default: 'calc(100vh - 93px)'): The height of the hero banner on mobile devices
- headline: The headline text displayed on top of the video
- synopsis: The synopsis text displayed below the headline
- buttonText: The text displayed on the call-to-action button
- buttonUrl: The URL the button will link to
Example:
<bsk-hero-banner-video
youtubeId="your_youtube_id"
headline="Sample Headline"
synopsis="Sample Synopsis"
buttonText="Click me"
buttonUrl="https://example.com"

</bsk-hero-banner-video>
Detailed explanation:

The component displays a full-screen video background using YouTube's embedded player.
The video automatically plays and is set to loop.
The hero banner video can have an optional headline, synopsis, and call-to-action button displayed on top of the video.
The component is responsive and adjusts its dimensions based on the screen size and aspect ratio of the video.
CSS:

Media queries are used to adjust the video and text dimensions and positioning for different screen sizes and aspect ratios.
The headline and synopsis text use responsive font sizes and line heights.
The video is displayed with a slightly reduced opacity (0.8) to improve text readability.
Methods:

init(el): Initializes the YouTube player by calling the 'ytInitMain()' function provided by the YouTube API.

---

Hero Banner Slider
The bsk-hero-banner-slider element is used to display a responsive slider of hero banners. The slider uses the Slick Carousel library to create a fading slide transition with navigation arrows and optional dots for navigation.

Optional attributes:

dots (default: false)
Example:
<bsk-hero-banner-slider dots="true"></bsk-hero-banner-slider>

Detailed explanation:

The component utilizes the Slick Carousel library to create a responsive and adaptive slider with a fading transition effect.
The dots attribute can be set to "true" to enable dot navigation at the bottom of the slider. By default, the dots are disabled.
The slider contains next and previous arrows for navigation between slides.
The slider supports lazy loading for better performance with the 'ondemand' option.
The component uses the 'adaptiveHeight' option to adjust the height of the slider based on the height of the current slide.
CSS:

If the dots attribute is set to "true", the position of the slick-dots element is set to absolute, and the bottom is set to 1rem.
Methods:

init(el): Initializes the Slick Carousel with the specified options and binds it to the '.slider' element.

---
Hero Banner Slide
The bsk-hero-banner-slide element is used to display a hero banner with an optional video or image background. The component supports a headline, synopsis, and a button with a link.

Mandatory attributes:

imgSrc
Optional attributes:

headline
synopsis
buttonText
linkUrl
overlay (default: true)
youtubeId
Example:
<bsk-hero-banner-slide imgSrc="path/to/image.jpg" headline="Your Headline" synopsis="Your synopsis" buttonText="Click Here" linkUrl="https://example.com"></bsk-hero-banner-slide>

Detailed explanation:

If the youtubeId attribute is provided, the component will display a YouTube video as the background. The video will only play on larger screens (not xs or sm breakpoints).
If no youtubeId is provided, an image will be used as the background. The image source is set with the imgSrc attribute.
The overlay attribute is used to enable or disable the hero overlay. If it's set to true (default), a div element containing the headline, synopsis, and button will be shown on top of the background.
The headline attribute sets the text for the main heading, displayed in uppercase.
The synopsis attribute sets the text for the secondary heading or paragraph.
The buttonText attribute sets the text for the button.
The linkUrl attribute sets the URL for the button link or the entire hero slide if the overlay is disabled.
The component is responsive, and it adjusts its layout based on the current viewport.
Methods:

wrapInAnchor(el): Wraps the hero slide in an anchor tag if the overlay is disabled and a linkUrl is provided.
initVideo(): Initializes the YouTube video if a youtubeId is provided and the current breakpoint is not xs or sm.
init(el): Calls wrapInAnchor and listens for breakpoint changes to initialize the video if needed.

---

Inline Offer Card
The bsk-inline-offer-card element is used to display an offer card with relevant information such as the offer title, finance details, offer description, and related images. The card has a responsive design, with separate layouts for desktop and mobile views. The finance details are displayed in a table, and the text content can be truncated using the CSS property --line-clamp to limit the number of visible lines.

Mandatory attributes:

offerTitle
offerFinanceDetails
offerBody
offerUrl
offerImage
Optional attributes:

lineClampLength (default is not set)
Example:

<bsk-inline-offer-card
  offerTitle="Sample Offer"
  :offerFinanceDetails="[{'Finance option 1': '£500'}, {'Finance option 2': '£1000'}]"
  offerBody="This is a sample description for the offer."
  offerUrl="/offer-url/"
  offerImage="/path/to/offer-image.jpg">
</bsk-inline-offer-card>

The bsk-inline-offer-card component displays an offer card with the provided information. The card has separate layouts for desktop and mobile devices. The offer details are displayed in a table, and the description can be truncated using the CSS property --line-clamp to limit the number of visible lines. The component includes two buttons, one to view all offers and the other to find out more about the specific offer.


---

Inline Offer Card
The bsk-inline-offer-card element is used to display a special offer in a card format.
The card includes an offer title, finance details, offer description, and buttons for navigation. The card is designed to be responsive, displaying the title and image differently on mobile and desktop screens. The offer description text is truncated using -webkit-line-clamp to control the number of lines displayed, which can be set via the lineClampLength attribute.

Mandatory attributes:

offerTitle: The title of the offer
offerBody: The description text of the offer
offerFinanceDetails: An array of key-value pairs representing the finance details for the offer
offerUrl: The URL for the 'Find out More' button
offerImage: The image URL for the offer card
Optional attributes:

lineClampLength: The number of lines to display in the offer description text (default is 3)
Example:

<bsk-inline-offer-card
  offerTitle="Special Offer"
  offerBody="Limited time offer on this amazing vehicle. Don't miss out!"
  offerFinanceDetails="[{'Deposit': '£1,000'}, {'Monthly Payment': '£250'}]"
  offerUrl="/special-offer"
  offerImage="/path/to/image.jpg">
</bsk-inline-offer-card>

---

CTA Section

The bsk-cta-section is a call-to-action (CTA) section element used to encourage user interaction. It features a two-column layout with an image on one side and a title, description, and an action button on the other side. The element is designed to be responsive and can be used for various CTAs, such as a part-exchange form or a simple button to navigate to another page.

Mandatory attributes:

title: The title text of the CTA section
bodyText: The description text of the CTA section
btnText: The text for the action button
is: The type of CTA, either 'part-exchange' or any other string for a simple button
Optional attributes:

aspectRatio: The aspect ratio for the image in the CTA section (default is auto)
Example for part-exchange form:

<bsk-cta-section
  title="Get a Part-Exchange Valuation"
  bodyText="Enter your registration below to receive a free valuation for your vehicle."
  btnText="Get Valuation"
  is="part-exchange">
</bsk-cta-section>

---