# Bluesky Elements Vehicle Card Docs

## Vehicle Card

- The bsk-vehicle-card is the main container element for the vehicle card custom elements, with the ability to switch between a grid view and a list view
- The v-wrap directive used in the template causes all elements nested inside the component to be wrapped in the component's article tag.
- CSS classes are dynamically set based on the variant and whether the grid type is set to 'list' or 'grid' (stored in variable - store.ucr.gridType). This allows the element and components nested within it to be styled properly for list view.

##### Mandatory attributes :

No mandatory attributes are required for this portion.

##### Optional attributes :

No optional attributes for this portion.

##### Example:

html```
<bsk-vehicle-card theme="bp"></bsk-vehicle-card>
```

