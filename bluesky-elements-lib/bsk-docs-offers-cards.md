# BSK Docs Offers Cards


## :green_circle: Inline Offer Card

The bsk-inline-offer-card element is used to display an offer card with relevant information such as the offer title, finance details, offer description, and related images. The card has a responsive design, with separate layouts for desktop and mobile views. The finance details are displayed in a table, and the text content can be truncated using the CSS property --line-clamp to limit the number of visible lines.

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

The bsk-inline-offer-card component displays an offer card with the provided information. The card has separate layouts for desktop and mobile devices. The offer details are displayed in a table, and the description can be truncated using the CSS property --line-clamp to limit the number of visible lines. The component includes two buttons, one to view all offers and the other to find out more about the specific offer.

---
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