# Bluesky Elements CLI Docs

## Boilerplate CLI :

## :green_circle: How to pull in the latest version of the components from bluesky-elements into BP
On BP, after creating your new branch run `npm run elements 'pull'`
This will bring the latest version of the components directories from bluesky-elements into your current BP branch.

## :green_circle: How to push changes back to bluesky-elements repo from BP
The workflow for component development is to work on bluesky-elements repo, and then bring the changes into BP to test them.
But, if, for whatever reason, you needed to make an edit to a component or its logic while you're working on BP you can still push those changes back to the bluesky-elements repo.
You can do that and run `npm run elements 'push'`
This will push the changes from BP to the bluesky-elements repo to be held in a special `'sync'` branch, ready for testing and merging.

## :green_circle: How to check what all the component names are
To avoid creating duplicate component names, you might need to check what the names of all the existing components are.
You can run `npm run elements 'list'` to get a list of all the component names in the terminal.

## :green_circle: How to quickly turn a snippet of code into a component
Its likley that if you're working on a build you will end up writing code that would be a good case for re-use but that isn't covered in the core component library. For example, a spotlight or text section that is used in various places on the site.

You can quickly and automatically turn any snippet into a component in 3 steps :

1. wrap the snippet in a template tag,
2. cut or copy the snippet
3. run `npm run elements 'paste'`.

Thats it!

### Heres' an example of the full process :

For this example, we'll imagine the build dev had created this snippet :

```html
<div>
    <h2>Title</h2>
    <p>Lorem ipsum dolor sit amet consectetur adipisicing elit.</p>
</div>
```

#### Step 1. Wrap the snippet

The first step would be to wrap the snippet in a template tag and give it a name using the bsk-element attribute like this :

```html
<template bsk-element="bsk-spotlight">
    <div>
        <h2>Title</h2>
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit.</p>
    </div>
</template>
```

#### Step 2. Cut the snippet with ctrl + x

#### Step 3. Run `npm run elements 'paste'`

The snippet will automatically be added into the correct include directory, ready for use across the site like this :

`<bsk-spotlight></bsk-spotlight>`


## bluesky-elements CLI :

## :green_circle: How to intergrate components pushed from BP into the bluesky-elements repo
If there are changes that were pushed from BP to the bluesky-elements repo, you can bring those changes into your current branch.
After creating your new branch run `npm run elements 'sync'`
This will overwrite the components directories in your current branch with the version from the `'sync'` branch.