
# Refactor Template and Component Logic Files Into a Single .astro file

## Overview 
This document lays out the instructions you will need to refactor template files, and related component logic files Into single .astro files.

## Context for This Work
The codebase contains 2 collections of files relevant to this work. These collections are nested under: 
- inc/bluesky-elements
- src/js/app/bluesky-elements/state-objects

I am in the process of moving these components over to our new Astro codebase. 
### inc/bluesky-elements

The .html files nested under this dir are template files using petite vue template syntax.
The .aspx files should be ignored. 
### src/js/app/bluesky-elements/state-objects 

the .js files nested under this dir are component logic files.

### How these work
We use an in-house fork of petite vue to merge the template files with the component logic to make lightweight web components drive by Petite Vue. 

## Brief for Your Work

For each pair of .html template and js component logic files, i want you to create a new .astro file to the spec laid out below: 


Replace the template tag in the .html file, with a custom-element tag, with the custom element's tag name being the value of the bsk-element attribute on the template tag that is to be removed
eg this template tag

```html
<template bsk-element="bsk-article-full-width-cta"></template>
```

Would be replaced with this custom element tag

```html
<bsk-article-full-width-cta></bsk-article-full-width-cta>
```


Add the object containing the component logic to a script tag within the .astro file
The script tag should have an this import statement at the top 

```js
import { bsk } from "@bsk";
```

The imported bsk function should be called with one argument: and object with the component passed as a property of that object. eg 

```js
bsk({ bskArticleFullWidthCta });
```

If there is a style tag nested within the .html file, it should be pulled out and added to the new .astro file as a top level style tag. 


Where there is vue syntax for rendering text, rendering lists, etc that can be moved to server-side template syntax so as to be handled at build time - creating static html - this should be the done as first preference. Where it is unclear if this can be handled effectively with .astro, leave the current set up (with this being handed by petite vue)

Example template file: 

```html
<template bsk-element="bsk-article-icon">
    <style>
        bsk-article-icon .card {
            background-color: transparent;
        }

        bsk-article-icon .card-body {
            grid-template-columns: auto 1fr;
            grid-template-rows: 1fr 1fr;
            column-gap: var(--bsk-spacer-3);
            row-gap: var(--bsk-spacer-2);
            align-items: center;
            padding: var(--bsk-spacer-2);
        }

        bsk-article-icon svg {
            grid-column: 1;
            grid-row: 1 / span 2;
        }

        bsk-article-icon .card-title {
            grid-column: 2;
        }

        bsk-article-icon p {
            grid-column: 2;
            grid-row: 2;
        }
    </style>
    <div class="card border-0 col-12 col-md-auto">
        <div class="card-body text-start d-grid">
            <img :src="imgSrc"
                :alt="imgAlt"
                class="mb-0" />
            <h5 class="card-title mb-0">{{title}}</h5>
            <p v-if="cardText"
                class="card-text mb-0">
                {{cardText}}
            </p>
            <a v-if="linkUrl"
                href="#"
                class="stretched-link"></a>
        </div>
    </div>
</template>
```

Example after conversion for .astro file: 

```html

---
interface Props {
    title: string;
    cardText?: string;
    imgSrc: string;
    imgAlt: string;
    linkUrl?: string;
}

const { title, cardText, imgSrc, imgAlt, linkUrl } = Astro.props;
---

<div class="card border-0 col-12 col-md-auto">
    <div class="card-body text-start d-grid">
        <img
            src={imgSrc}
            alt={imgAlt}
            class="mb-0"
        />
        <h5 class="card-title mb-0">{title}</h5>
        {cardText && <p class="card-text mb-0">{cardText}</p>}
        {
            linkUrl && (
                <a
                    v-if="linkUrl"
                    href={linkUrl}
                    class="stretched-link"
                />
            )
        }
    </div>
</div>

<style>
    .card {
        background-color: transparent;
    }

    .card-body {
        grid-template-columns: auto 1fr;
        grid-template-rows: 1fr 1fr;
        column-gap: var(--bsk-spacer-3);
        row-gap: var(--bsk-spacer-2);
        align-items: center;
        padding: var(--bsk-spacer-2);
    }

    svg {
        grid-column: 1;
        grid-row: 1 / span 2;
    }

    .card-title {
        grid-column: 2;
    }

    p {
        grid-column: 2;
        grid-row: 2;
    }
</style>


```

The new .astro file should be saved in matching nested dir location under 
inc\astro-versions 

for example
the pair of files
inc\bluesky-elements\accordion\bsk-accordion-group.html
src\js\app\bluesky-elements\state-objects\accordion\bsk-accordion-group.js

would be used for the content of a new .astro 
inc\astro-versions\accordion\AccordionGroup.astro

Notice the file naming convention. 
Updated to PascalCase
Removed the BSK namespacing from the filename 
The dir structure matches that used in the previous template and component logic dir structure


Here is a full example of a successfully creation of a new .astro file from the template file and component logic. 

The example template file : 

```html
<template bsk-element="bsk-grid-masonry">
    <style>
        bsk-grid-masonry [slot="grid"]:not(.slick-initialized) {
            display: grid;
            grid-template-columns: repeat(12, 1fr);
            gap: 1rem;
        }

        bsk-grid-masonry [slot="grid"]>* {
            grid-column: 1 / span 12;
        }

        bsk-grid-masonry .slick-slider .slick-dots {
            margin: var(--bsk-spacer-2) auto var(--bsk-spacer-2);
        }

        @media only screen and (min-width: 576px) and (max-width: 991px) {
            bsk-grid-masonry:not([is="alt-one"]) [slot="grid"]:not(.slick-initialized)> :is(:nth-child(1), :nth-child(2)) {
                grid-column: span 6;
            }

            bsk-grid-masonry:not([is="alt-one"]) [slot="grid"]:not(.slick-initialized)> :not(:nth-child(1), :nth-child(2)) {
                grid-column: span 4;
            }
        }

        @media only screen and (min-width: 992px) {
            bsk-grid-masonry:not([is="alt-one"]) [slot="grid"]> :is(:nth-child(1), :nth-child(2)) {
                grid-column: span 6;
            }

            bsk-grid-masonry:not([is="alt-one"]) [slot="grid"]> :not(:nth-child(1), :nth-child(2)) {
                grid-column: span 4;
            }
        }

        @media only screen and (min-width: 1200px) {
            bsk-grid-masonry:not([is="alt-one"])>[slot="grid"] {
                gap: 1.5rem;
            }
        }

        @media only screen and (min-width: 768px) {
            bsk-grid-masonry[is="alt-one"] img {
                object-fit: cover;
            }

            bsk-grid-masonry[is="alt-one"] [slot="grid"] {
                grid-template-columns: repeat(4, 1fr);
                grid-template-rows: repeat(2, 1fr);
                gap: 1.5rem;
            }

            bsk-grid-masonry[is="alt-one"] [slot="grid"]>a {
                grid-column: span 1;
            }

            bsk-grid-masonry[is="alt-one"] [slot="grid"]> :nth-child(1) {
                grid-row: span 2;
            }

            bsk-grid-masonry[is="alt-one"] [slot="grid"]> :nth-child(2) {
                grid-column: span 2;
            }
        }
    </style>
    <div @vue:mounted="init($el)">
        <slot name="grid"></slot>
    </div>
</template>
```

The example component logic : 

```js
export const bskGridMasonry = {
    slickMob: false,
    init(el) {
        console.log("this slick mob: ", this.slickMob);
    }
};

```

The example final .astro file created from the above: 

```html

---
const { items, slickMob } = Astro.props || [];
---

<!-- Slick and Masonry Grid : START -->
<bsk-grid-masonry slick-mob={slickMob}>
    <div @vue:mounted="init($el)">
        <slot name="grid"></slot>
    </div>
</bsk-grid-masonry>
<!-- Slick and Masonry Grid : END -->

<script>
    import { bsk } from "@bsk";

    const bskGridMasonry = {
        init(el) {
            console.log("this slick mob: ", this.slickMob);
        },
    };

    bsk({ bskGridMasonry });
</script>

<style>
    span:not(.slick-initialized) {
        display: grid;
        grid-template-columns: repeat(12, 1fr);
        gap: 1rem;
    }

    span > * {
        grid-column: 1 / span 12;
    }

    .slick-slider .slick-dots {
        margin: var(--bsk-spacer-2) auto var(--bsk-spacer-2);
    }

    @media only screen and (min-width: 576px) and (max-width: 991px) {
        span:not(.slick-initialized) > :is(:nth-child(1), :nth-child(2)) {
            grid-column: span 6;
        }

        span:not(.slick-initialized) > :not(:nth-child(1), :nth-child(2)) {
            grid-column: span 4;
        }
    }

    @media only screen and (min-width: 992px) {
        span > :is(:nth-child(1), :nth-child(2)) {
            grid-column: span 6;
        }

        span > :not(:nth-child(1), :nth-child(2)) {
            grid-column: span 4;
        }
    }

    @media only screen and (min-width: 1200px) {
        > span {
            gap: 1.5rem;
        }
    }
</style>


```



### Final Notes
It is important to stick to the brief, and follow the examples given of successful new .astro files created, and their contents. 

I have created the empty dirs under inc\astro-versions for you. 
You only need to create the new files and their contents. 

