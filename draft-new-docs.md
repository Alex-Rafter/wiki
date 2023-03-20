# Draft New Docs

# Components Notes

---

## Gallery

The bsk-gallery component is a responsive image gallery with optional thumbnail navigation. It supports both full-width and standard display modes, and uses the Slick Carousel library for sliding functionality.

### Mandatory attributes:
- thumbs: (Boolean) Determines whether to display thumbnail navigation or not. Default: true.
- thumbs-to-show: (Number) Specifies the number of thumbnails to show in the navigation. Default: 4.
- img-count: (Number) The total number of images in the gallery. Default: 0.
- images: (String) A comma-separated list of image names.
- manufacturer: (String) The name of the vehicle's manufacturer.
- model: (String) The name of the vehicle's model.
- version: (String) The name of the vehicle's version.
- mileage: (String) The vehicle's mileage.

### Methods
- galleryClick(el): Navigates to the slide corresponding to the thumbnail clicked.
- init(el): Initializes the gallery component based on the display mode (is) and sets the total image count.
- Utility Functions
- fullWidthInit(el): Initializes the full-width gallery and thumbnail navigation with Slick Carousel.
- standardInit(el, thumbsToShow): Initializes the standard gallery and thumbnail navigation with Slick Carousel.

Usage
To use the bsk-gallery component, include the custom bsk-element tag in your HTML:

```html
          <bsk-gallery
            is="full-width"
            manufacturer="SEAT"
            model="IBIZA"
            version="Sport"
            mileage="12,333"
            has-video="true"
            images="fbe73d57-63b1-450b-87f1-88d1ef879908,371d1eb7-e92d-4acd-b9e2-e9b9d4923439,66702a92-fc5d-4af9-9284-f16b757f3df8,f1df53b2-1147-4c16-bbb4-3cf2a833583a,ba642185-eff7-487b-a092-6bc65f4c8fb9,3240b912-9fcd-425c-9869-3878a4c4d280,1faaa042-33ec-451e-985b-db670a704f14,b025ce5d-f135-44b6-877f-06f984498f6a,994c023b-6515-456e-93f7-8ea341cee3da,76500894-ac5f-4e81-8a01-413ca92643bd,277d09ad-9b24-4fcb-b49e-e2b200a0e51c,d0118adb-0ad5-42c1-8262-5b0bba76adb8,cc14599d-f4c3-4112-9997-0a602c5e328e,65d73e76-e89b-4b10-bc47-12f8c64537c2,0f7ea08a-04f1-4689-8a20-75a12b9e9223,6c370740-d120-4518-b557-0400f0d01bf3,b2e20339-83b7-4fdf-a75b-08f799c6742c,d88c374b-15c6-4fba-8624-f4a79c58b88b,bf02b684-8c4c-45ee-a9ff-3415d5cf2b5d,3989f86a-ac85-4c46-b725-54aa47182aa0,983d0f6f-f43a-4099-be84-b41335b33868,f6fecfcf-69ea-4006-b1ed-d1cde519b69e,d33eb065-3086-45d4-9fcb-a73802c2be1e,7348a718-8e10-4091-94d8-5fb2a5c2894b,cc7de382-32d1-4329-997c-08066622f199,45fe2211-d7b1-476c-a7dd-42c4a575d2e1,835b4364-5103-4f90-a655-95ba3c4a369e,5c3964c9-eb8e-4582-bc90-d4ae56b12d3e,185e8128-b54a-47ce-b62a-58352d336e72,8cd12115-1a13-41ba-9be0-1079d4222dce,181f7c42-1efe-48a6-80a3-fd293139e0cd,28ed77c8-597f-4901-8f81-c24396a7684b,46b282af-eb4d-446e-a7c0-d63ddc24de0f,84431141-77db-42af-bebf-ddff59846850,8aa79602-992e-4858-905f-71dcdb56c6a2,527c81a1-1243-4a86-bc96-576a588d4045,ad367f05-dac1-4a08-acc5-835052b8357c,6e117729-5d24-40e3-a0f6-2422c195a755,e5f406d0-0104-4562-9099-8358cac4adc2,ea76e41a-68e8-4ffd-b500-bdc58d918d76,7de3499d-998e-4879-ba12-632eab3582ad,9b7bfc6a-d2fc-4a2d-8e19-199582fad4e5,08e44c33-d446-471a-b45f-6cec5c0fc53f,e7971fce-970b-4a37-9295-96c49dfe4497"
          >
          </bsk-gallery>
```

---

### Hero Banner Video

The bsk-hero-banner-video element is used to display a responsive full-screen video background with an optional headline, synopsis, and call-to-action button. The video is played using YouTube's embedded player.

Attributes:

- youtubeId: The YouTube video ID for the background video
- heroBgHeight (default: '100vh'): The height of the hero banner on desktop
- heroBgHeightMobile (default: 'calc(100vh - 93px)'): The height of the hero banner on mobile devices
- headline: The headline text displayed on top of the video
- synopsis: The synopsis text displayed below the headline
- buttonText: The text displayed on the call-to-action button
- buttonUrl: The URL the button will link to
-
Example:
```html
<bsk-hero-banner-video
youtubeId="your_youtube_id"
headline="Sample Headline"
synopsis="Sample Synopsis"
buttonText="Click me"
buttonUrl="https://example.com"

</bsk-hero-banner-video>
```

Detailed explanation:

- The component displays a full-screen video background using YouTube's embedded player.
- The video automatically plays and is set to loop.
- The hero banner video can have an optional headline, synopsis, and call-to-action button displayed on top of the video.
- The component is responsive and adjusts its dimensions based on the screen size and aspect ratio of the video.

CSS:

- Media queries are used to adjust the video and text dimensions and positioning for different screen sizes and aspect ratios.
- The headline and synopsis text use responsive font sizes and line heights.
- The video is displayed with a slightly reduced opacity (0.8) to improve text readability.
Methods:

init(el): Initializes the YouTube player by calling the 'ytInitMain()' function provided by the YouTube API.

---

Hero Banner Slider

The bsk-hero-banner-slider element is used to display a responsive slider of hero banners. The slider uses the Slick Carousel library to create a fading slide transition with navigation arrows and optional dots for navigation.

Optional attributes:

dots (default: false)

Example:
```html
<bsk-hero-banner-slider dots="true"></bsk-hero-banner-slider>
```

Detailed explanation:

- The component utilizes the Slick Carousel library to create a responsive and adaptive slider with a fading transition effect.
- The dots attribute can be set to "true" to enable dot navigation at the bottom of the slider. By default, the dots are disabled.
- The slider contains next and previous arrows for navigation between slides.
- The slider supports lazy loading for better performance with the 'ondemand' option.
- The component uses the 'adaptiveHeight' option to adjust the height of the slider based on the height of the current slide.
-
CSS:

If the dots attribute is set to "true", the position of the slick-dots element is set to absolute, and the bottom is set to 1rem.
Methods:

init(el): Initializes the Slick Carousel with the specified options and binds it to the '.slider' element.

---
## Hero Banner Slide

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

```html
Example:
<bsk-hero-banner-slide imgSrc="path/to/image.jpg" headline="Your Headline" synopsis="Your synopsis" buttonText="Click Here" linkUrl="https://example.com"></bsk-hero-banner-slide>
```

Detailed explanation:

- If the youtubeId attribute is provided, the component will display a YouTube video as the background. The video will only play on larger screens (not xs or sm breakpoints).
- If no youtubeId is provided, an image will be used as the background. The image source is set with the imgSrc attribute.
- The overlay attribute is used to enable or disable the hero overlay. If it's set to true (default), a div element containing the headline, synopsis, and button will be shown on top of the background.
- The headline attribute sets the text for the main heading, displayed in uppercase.
- The synopsis attribute sets the text for the secondary heading or paragraph.
- The buttonText attribute sets the text for the button.
- The linkUrl attribute sets the URL for the button link or the entire hero slide if the overlay is disabled.
- The component is responsive, and it adjusts its layout based on the current viewport.
Methods:

wrapInAnchor(el): Wraps the hero slide in an anchor tag if the overlay is disabled and a linkUrl is provided.
initVideo(): Initializes the YouTube video if a youtubeId is provided and the current breakpoint is not xs or sm.
init(el): Calls wrapInAnchor and listens for breakpoint changes to initialize the video if needed.

---

## Inline Offer Card
The bsk-inline-offer-card element is used to display an offer card with relevant information such as the offer title, finance details, offer description, and related images. The card has a responsive design, with separate layouts for desktop and mobile views. The finance details are displayed in a table, and the text content can be truncated using the CSS property --line-clamp to limit the number of visible lines.

Mandatory attributes:

- offerTitle
- offerFinanceDetails
- offerBody
- offerUrl
- offerImage

Optional attributes:

lineClampLength (default is not set)
Example:

```html
<bsk-inline-offer-card
  offerTitle="Sample Offer"
  :offerFinanceDetails="[{'Finance option 1': '£500'}, {'Finance option 2': '£1000'}]"
  offerBody="This is a sample description for the offer."
  offerUrl="/offer-url/"
  offerImage="/path/to/offer-image.jpg">
</bsk-inline-offer-card>
```

The bsk-inline-offer-card component displays an offer card with the provided information. The card has separate layouts for desktop and mobile devices. The offer details are displayed in a table, and the description can be truncated using the CSS property --line-clamp to limit the number of visible lines. The component includes two buttons, one to view all offers and the other to find out more about the specific offer.


---

## Inline Offer Card

The bsk-inline-offer-card element is used to display a special offer in a card format.
The card includes an offer title, finance details, offer description, and buttons for navigation. The card is designed to be responsive, displaying the title and image differently on mobile and desktop screens. The offer description text is truncated using -webkit-line-clamp to control the number of lines displayed, which can be set via the lineClampLength attribute.

Mandatory attributes:

- offerTitle: The title of the offer
- offerBody: The description text of the offer
- offerFinanceDetails: An array of key-value pairs representing the finance details for the offer
- offerUrl: The URL for the 'Find out More' button
- offerImage: The image URL for the offer card

Optional attributes:

lineClampLength: The number of lines to display in the offer description text (default is 3)
Example:

```html
<bsk-inline-offer-card
  offerTitle="Special Offer"
  offerBody="Limited time offer on this amazing vehicle. Don't miss out!"
  offerFinanceDetails="[{'Deposit': '£1,000'}, {'Monthly Payment': '£250'}]"
  offerUrl="/special-offer"
  offerImage="/path/to/image.jpg">
</bsk-inline-offer-card>
```

---

## CTA Section

The bsk-cta-section is a call-to-action (CTA) section element used to encourage user interaction. It features a two-column layout with an image on one side and a title, description, and an action button on the other side. The element is designed to be responsive and can be used for various CTAs, such as a part-exchange form or a simple button to navigate to another page.

Mandatory attributes:

- title: The title text of the CTA section
- bodyText: The description text of the CTA section
- btnText: The text for the action button
- is: The type of CTA, either 'part-exchange' or any other string for a simple button

Optional attributes:

- aspectRatio: The aspect ratio for the image in the CTA section (default is auto)
Example for part-exchange form:

```html
<bsk-cta-section
  title="Get a Part-Exchange Valuation"
  bodyText="Enter your registration below to receive a free valuation for your vehicle."
  btnText="Get Valuation"
  is="part-exchange">
</bsk-cta-section>
```

---
