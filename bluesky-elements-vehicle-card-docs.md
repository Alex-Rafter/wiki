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

##### Mandatory attributes :

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

##### Optional attributes :

No optional attributes for this portion.

##### Example:

 ```


```



Vehicle Card Body
-----------------

- The bsk-vehicle-card-img-body element creates a container element for the vehicle card text components.
- It makes use of the v-wrap directive to ensure all children are placed inside the component's html rather than outside of it.
- CSS classes are dynamically set on card-body element for both list view and grid view.
- This ensures the child components sit correctly inside the container for both of these views.
-

##### Mandatory attributes :

No mandatory attributes are required for this portion.

##### Optional attributes :

No optional attributes for this portion.

##### Example:

 ```


```

Vehicle Card Titles
-------------------

- The bsk-vehicle-card-titles element defines the vehicle card's title and sub-title, and allows them to be styled differently for both grid view and a list view.
- CSS classed are dynamically set based on the variant and whether the grid type is set to 'list' or 'grid' (variable - store.ucr.gridType).

##### Mandatory attributes :

- manufacturer
- model
- version

##### Optional attributes :

No optional attributes for this portion.

##### Example:

 ```


```


