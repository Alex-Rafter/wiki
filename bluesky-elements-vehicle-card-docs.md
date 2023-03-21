# Bluesky Elements Vehicle Card Docs

## Vehicle Card

- The bsk-vehicle-card is the main container element for the vehicle card custom elements, with the ability to switch between a grid view and a list view
- The v-wrap directive used in the template causes all elements nested inside the component to be wrapped in the component's article tag.
- CSS classes are dynamically set based on the variant and whether the grid type is set to 'list' or 'grid' (stored in variable - store.ucr.gridType). This allows the element and components nested within it to be styled properly for list view.

### Mandatory attributes :

No mandatory attributes are required for this portion.

### Optional attributes :

- theme

### Example:

```html
<bsk-vehicle-card theme="bp"></bsk-vehicle-card>
```

Vehicle Card Img
----------------

- The img tag includes a lazyloaded class and is conditionally assigned the list-view class based on the gridType property in the store.
- The href attribute of the anchor tag is bound to a url variable, and the title attribute displays various vehicle information.
- The data-vehicle attributes contain additional vehicle data that can be used for tracking or other purposes.
- The &lt;noscript&gt; tag provides alternative content for browsers that do not support JavaScript.

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



## Vehicle Card Body


- The bsk-vehicle-card-img-body element creates a container element for the vehicle card text components.
- It makes use of the v-wrap directive to ensure all children are placed inside the component's html rather than outside of it.
- CSS classes are dynamically set on card-body element for both list view and grid view.
- This ensures the child components sit correctly inside the container for both of these views.
-

### Mandatory attributes :

No mandatory attributes are required for this portion.

### Optional attributes :

No optional attributes for this portion.

### Example:

```html
<bsk-vehicle-card-body></bsk-vehicle-card-body>
```

## Vehicle Card Titles

- The bsk-vehicle-card-titles element defines the vehicle card's title and sub-title, and allows them to be styled differently for both grid view and a list view.
- CSS classed are dynamically set based on the variant and whether the grid type is set to 'list' or 'grid' (variable - store.ucr.gridType).

### Mandatory attributes :

- manufacturer
- model
- version

### Optional attributes :

No optional attributes for this portion.

### Example:

```html
<bsk-vehicle-card-body></bsk-vehicle-card-body>
```

## Vehicle Card Pricing

- The bsk-vehicle-card-pricing element is used to display vehicle pricing information.
- It has has two possible variations : default and was-now-save.
- If the is attribute is set to 'was-now-save', the element will display in a css grid layout using css variables to set col and row positions.
- The values show will be for previous price, current price, and savings, along finance price.
- Otherwise, the component will only show the price and monthly payment and will show these in row layout using flex.
- The vehicle price is formatted to include commas in the thousands place.
- CSS classes are dynamically set based on the variant and whether the grid type is set to 'list' or 'grid' (variable - store.ucr.gridType).

### Mandatory attributes :

- price
- monthly

### Optional attributes :

- is

### Example:

 ```html


```

## Vehicle Card Specs

- The bsk-vehicle-card-specs element is used for displaying vehicle specifications.
- The template uses v-for to iterate over each specification and display it with its associated icon (if specified) in a span element.
- Conditional class bindings are used to set styles for list and grid view, and icon and pills styles.

### Mandatory attributes :

- specs (passed as csv)

### Optional attributes :

- is
- icons (passed as csv)

### Example:

 ```html


```

## Vehicle Card Actions

- The button is linked to a URL that is passed through the 'href' attribute.
- The 'title' attribute displays the car's details.
- The anchor tag with button classes also contains several custom data attributes that hold tracking information about the vehicle.

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


```


