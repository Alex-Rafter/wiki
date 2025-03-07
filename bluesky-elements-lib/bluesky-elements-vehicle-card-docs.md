# Bluesky Elements Vehicle Card Docs

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

## :car: Vehicle Card Image Count
The bsk-vehicle-card-img-count element is used to display the image and video count on a vehicle card. The component is designed to be positioned absolutely, appearing at the bottom left corner of the vehicle card image. The image and video count are displayed as badges with icons and text, indicating the total number of images and whether there is a video available for the vehicle.

### Mandatory Attributes:
- imgCount: The number of images for the vehicle
- hasVideo: A boolean indicating if there is a video available for the vehicle

### Example:

```html
<bsk-vehicle-card-img-count
  img-count="32"
  has-video="true"
></bsk-vehicle-card-img-count>
```

