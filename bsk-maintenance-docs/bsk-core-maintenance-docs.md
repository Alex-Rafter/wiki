# BSK Core - Codebase Maintenance 📝

## Overview 🌟
BSK (Bluesky Elements) is a web component library built on petite-vue that provides a lightweight framework for creating reactive web components. The core library handles component registration, lifecycle management, and state management through a custom web component implementation.

## Core Architecture 📂

### Key Features 🔑

1. **BSK Core Library**
   - Built on petite-vue
   - Provides component registration system
   - Includes global state management
   - Supports ES modules

2. **Component System**
   - Custom elements architecture
   - Automatic component registration
   - Built-in v-cloak support
   - Modular component structure

3. **State Management**
   - Centralized store system
   - Module-based state organization
   - Reactive state updates
   - Shared state across components

### Base Component System 🛠️

1. **BSKElement Class**
   - Extends HTMLElement for web component functionality
   - Handles attribute processing and state management
   - Manages v-scope attributes for petite-vue integration
   - Implements slot management system

2. **Component Creation System**
   - Uses makeComponent factory function
   - Handles component registration and lifecycle
   - Integrates with petite-vue's createApp
   - Manages component state merging

3. **State Management**
   - Global reactive store using petite-vue
   - Single store instance enforcement
   - Reactive state propagation

## Core Modules 📦

### 1. base-class.js 🔧
Core web component base class with features:
```javascript
class BSKElement extends HTMLElement {
  // State initialization
  state = {
    is: 'default',
    icon: null,
    icons: ''
  }
  
  // Core methods
  manageVScopeAttr()     // Handles v-scope attribute processing
  processAttributes()     // Converts HTML attributes to state
  slots()                // Manages slot replacement
}
```

### 2. make-component.js 🏭
Component factory with features:
```javascript
makeComponent(state = {}) {
  // Lifecycle hooks
  connectedCallback()    // Component mounting
  disconnectedCallback() // Cleanup
  mountEl()             // petite-vue integration
}
```

### 3. create-store.js 📊
Global state management:
```javascript
bskStore(obj) {
  // Single store enforcement
  // Reactive state creation
  window.store = reactive(obj)
}
```

## Internal Workflows 🔄

### Component Lifecycle

1. **Registration**
   - Component class creation
   - Custom element definition
   - State initialization

2. **Mounting**
   - Attribute processing
   - State merging
   - Template mounting
   - Slot management

3. **Updates**
   - Reactive state changes
   - Template re-rendering
   - Slot updates

### State Flow

1. **Component State**
   - Local state in BSKElement
   - Attribute-based state
   - v-scope integration

2. **Global State**
   - Single store instance
   - Reactive updates
   - Component access

## Maintenance Guide 🛠️

Running the Software 🚀

### Development Setup

1. **Install Dependencies**
```bash
npm install
```

2. **Start Development Server**
```bash
npm start
# or
npm run demo
```

3. **Watch for Changes**
```bash
npm run watch
```

### Building for Production

1. **Create Production Build**
```bash
npm run build
```

The build output will be in `dist/bsk@v2.js

### Adding Core Features

1. **Extending BSKElement**
```javascript
// Add new base functionality
class BSKElement {
  newFeature() {
    // Implementation
  }
}
```


### Debugging Tips

1. **Components Not Rendering**
   - Check import map configuration
   - Verify component registration - check [registered custom elements](https://developer.mozilla.org/en-US/docs/Web/API/CustomElementRegistry)
   - Monitor lifecycle hooks
   - Check for console errors

2. **State Not Updating**
   - Ensure store is initialized n (you should be able to log the with console.log(window.store) to check the properties on the Proxy)
   - Check components are using correct syntax (eg `store.ucd.someProperty`)

3. **Build Issues**
   - Clear node_modules and reinstall
   - Check esbuild configuration
   - Verify import paths

### Best Practices 📋

1. **Component Design**
   - Keep BSKElement lean
   - Document internal API changes here

2. **State Management**
   - Minimize global state!

3. **Performance**
   - Minimize DOM operations, lean on Petite Vue wherever poss rather than customising further

