

## Bring Over BSK 1.0 Components to BP Static and Refactor

### 🧭 Introduction

Because we are using many of the same core dependencies in our current boilerplate and the new BP Static codebase, we should (in most cases) be able to convert components from our current BSK in-house UI library into BP-Static-compatible components.
Because we no longer have the same constraints as the existing codebase, we have a good opportunity to refactor the transferred components to make the templates simpler, and easier to reason about.

### 📝 Brief 

- For each template file within the folder `inc/bluesky-elements` follow the steps below, to bring over all the components we need
- Once working and tested, refactor the component in line with the steps laid out in the brief
- Once the components have been refactored and tested, create a new demo page under `./src/pages/examples/bsk` demoing each component and variation in use

### 🔁 Step 1 - Bring Over BSK 1.0 Components


For each component within the target directory in the current boilerplate: 

- create a new .astro file for the new component
- name this in PascalCase using the same naming as the existing bsk component minus the 'bsk' namespace eg
Current Boilerplate  
 `inc/bluesky-elements/spotlights/bsk-spotlight-item.html` 
 
 New File Location
 `./src/features/spotlights/SpotlightItem.astro
 
- Copy over the existing BP 1.0 template file's contents exactly as it is initially to the new .astro component
- if there is a style tag nested under the template tag, move the whole style tag to the top level - so that it is no longer a child of the template tag but instead sits as a sibling to the template tag eg

from 

```html
<template>
    <style></style>
</template>
```

to

```html
<template></template>
<style></style>
```

- create a new script tag inside the .astro component

- add the bsk import statement at the top of the new script tag 
eg `import { bsk } from "@bsk";`

- navigate to the corresponding JavaScript state object file in BP 1.0

for template 

 `inc/bluesky-elements/spotlights/bsk-spotlight-item.html` 

you would navigate to 

 `src/js/app/bluesky-elements/state-objects/spotlights/bsk-spotlight-item.js` 
 
- copy the variable declaration (minus any export statement) and the object assigned to that variable. eg 
  
```JS
export const bskSpotlightItem = {}; 
```

minus any export statement

```JS
export 
```

leaves this to copy 

```js
const bskSpotlightItem = {}; 
```
   
- Paste the component logic you just copied into the new .astro component, inside the script tag you previously created
- In the same script tag, below the pasted component logic, call the bsk function, passing the component variable name inside an object as the only argument to that function
  
```js
bsk({ bskSpotlightItem })
````
  
- Next, we need to replace the outer template tag in your .astro component.  To do so, in place of the template tag, create a custom element tag, with the tag name matching the previous template tag's bsk-element attribute value. eg

from
  
```html
<template bsk-element="bsk-spotlight-item"></template>  
```

to
```html
<bsk-spotlight-item></bsk-spotlight-item>
```
  

- Next, replace all Vue double mustache syntax to custom delimiter double parentheses.

from

```html
<p>{{ text }}</p>
```

to 
```html
<p>(( text ))</p>
```

At this point you should have an astro component with : 

- markup wrapped in a bsk custom element tag 
- a single style tag with component styles
- a single script tag with the component logic and a call to the bsk function registering the component
  
Example of Top Level Tags

```html
<bsk-spotlight-item></bsk-spotlight-item>
<script></script>
<style></style>
```

At this point you should be able to use the component. You can easily test this by : 
passing hardcoded values via attributes set on the custom element tag

```html
<bsk-spotlight-item text="hello world">
	<p>(( text ))</p>
</bsk-spotlight-item>

```

----
### 🧼 Step 2- Refactor BSK 1.0 Components for BP Static

####  🧩 Refactor - Text Interpolation

To do this: 
- start with simple text Interpolation cases (these should have been updated to use double parentheses in the previous step)
- in the .astro file front matter, create a new variable of the same name to that of the  component property, destructuring from Astro.props eg

```JS
const { text } = Astro.props; 
```

- assign a default value to the variable
  
```JS
const { text = "Hello world" } = Astro.props; 
```
  
- In BP Static reactive data is handled by Petite Vue-driven BSK Components. We use the double parentheses syntax for this use case. But for rendering Dynamic build-time data with Astro, we need to use single moustache syntax. eg
  
  client side reactive data (used with scopes and BSK components)
   
```html
<p>(( text ))</p>
```

build time data (handled by Astro)
 
```html
<p>{ text }</p>
```
  
  
- Change any simple text interpolation cases from BSK `(())` to Astro `{}` 
- At this point you should see the default value set in the Astro front matter being rendered instead of the default bsk value set in the component logic in the script tag (you might want to try changing the default in the front matter briefly to confirm that the data is pulling from that source)
- You can now test passing new values as [props](https://docs.astro.build/en/basics/astro-components/#component-props) to the Astro component instance 
- After you have finished you will need to clean up the component logic so as to remove the unused property in the bsk component logic found in the .astro file script tag

#### 🏷️ Refactor - use Astro dynamic attributes over Vue attribute binding

In some cases we want to use Petite Vue to control reactive data sources that will define attributes and their values at runtime - eg we may want our class names to react and update based on component state. But in many cases, we can simplify the bsk components we have brought over by using [Astro dynamic attributes](https://docs.astro.build/en/reference/astro-syntax/#dynamic-attributes) instead of [Vue's attribute binding](https://vuejs.org/guide/essentials/template-syntax#attribute-bindings).

To do this: 
- find instances in the markup of use of `v-bind` or the shorthand `:` syntax
- update from the Vue attribute binding syntax to Astro dynamic attribute syntax

  
```html
<span :id="specialID"></span>
```  

```html
<span id={specialID}></span>
```  

- create a new variable in Astro front matter, of the same name to that referenced inside previous v-bind eg
  
```js
const specialID = "primaryID"; 
```

- at this point you should see the default value set in the Astro front matter being rendered instead of the default bsk value set in the component logic in the script tag (you might want to try changing the default in the front matter briefly to confirm that the data is pulling from that source)
- You can now test passing new values as props to the Astro component instance as covered previously
- You should be able to use this for simple cases where we do not need to use reactive data such as data attributes, class names, ids, etc that are set once only when the component is mounted. (*If you are not sure if an attribute should be refactored to use dynamic attributes or not - leave these for now - note them and we can review prior to PR.*)
- After you have finished you will need to clean up the component logic so as to remove the property that had been used as the reactive data source in attribute binding.

It is quite possible at this point that the component's runtime JavaScript requirement is so small that we may be able to refactor to an even simpler component by using a scope instead of a full bsk component. This is great! Generally, wherever we can do this we should favour the simplest and most lightweight solution.  
#### 🎨 Refactor styles - using Astro component scoping over bsk namespacing
- Because Astro uses it's own scoping method, we do not need to namespace our css using the custom element tag name. This allows us to clean up a lot of noise in the component styles.
- If the css rule is targeting the custom element tag itself then do not remove the style. 
  
  Keep this

```css
bsk-tabs {
	display: block;
}
```
  
  If the style is targeting a child of the custom element tag, its very likely we don't need that namespacing. eg
  
update this   

```css
bsk-tabs p {
	margin-bottom: 0.2rem;
}
```

to the simpler

```css
p {
	margin-bottom: 0.2rem;
}
```

#### 🧬 Refactor Template - Use Template Inheritance over Template Logic

If the component logic is simple enough that it can be handled with a scope instead of bsk component, we can further simplify the component with the use of template inheritance:

["Template inheritance is an approach to managing templates that resembles object-oriented programming techniques.... you can inherit the contents of one template to another... and change blocks of content therein... This keeps template management minimal and efficient, since each template only contains the differences from the template it extends."](https://www.smarty.net/docs/en/advanced.features.template.inheritance.tpl)


In the BSK UI library, component variations are configured using the 'is' property. 

```html
<bsk-tabs is="slim"></bsk-tabs>
```

Variations in markup, classes and other attributes; and targeting of some style rules, are handled via the value of the is property. Examples: 

```html
<p :class="is">Hello World</p>
```

```html
<p :data-style="is">Hello World</p>
```

```html
<style>

bsk-tabs[is="slim"] p {
	font-weight: 200;
}

</style>
```

While this works, and has enabled us to make use of component variations within the constraints of the COG platform, it adds complexity to our templates. For example, we may need to use additional template logic (v-if, v-else-if, etc) to define what markup should render for each variant. This can quickly add complexity, and make the template harder to reason about.

Because we do not have the same limitation with the new codebase, we now have a chance to reduce that complexity. We reduce the complexity by using template inheritance instead of template logic.

###### 🔧 Refactoring steps 
- Create a copy of the .astro component you want to simplify (prior to any refactoring).- We will use this for reference as we go. 
- The other file will be used for our base instance.
- Go through the template and remove any markup that is not specific to the default version of the components. For example, all mark up in the related conditional logic (v-if).
- Mark these default sections of the template that are left using a named slot - this will now form the fallback content that will render by default.
- Repeat for all areas of conditional rendering used to handle variants (notable by the use of the 'is' property)
- You should now have a functioning base component.
- You can now import that base component into any variant. 
- By creating new markup as children of the base component and making use of the slot attribute, it is possible to override chunks of the base instance's markup. 
- Identify any areas of the template where attribute binding, class binding,  etc is used to set values based on the value of the 'is' property (only those using the 'is' property as the sole condition are suitable for refactoring)
- These sections should be updated to hardcoded values, or use Astro's dynamic attributes and Astro props to set values.
- identify any styles targeting the is attribute on the custom element `[is="variant-name"]`. These should be moved out to the base style tag and moved inside the variant' .astro component that inherits the base template.
  
  When all the steps are complete you should have 
  - your base astro component with base styles etc, using named slots with fallback (default) content
  - variants as their own astro components, importing the base component and overriding sections of the template with named slots

### 🎭 Step 3 - Demo Pages

Once all refactoring is done, create a demo of the component use in a sub-page of the Astro examples folder

Notes
All components using Slick JS or other JQuery plugins need to be re-written. Note these down for now and move on, We can do these as a second batch after the majority are brought over.