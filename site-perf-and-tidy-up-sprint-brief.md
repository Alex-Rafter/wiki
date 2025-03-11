# Performance Improvement & Codebase Cleanup Template

This template outlines steps taken to optimize performance and tidy up a codebase. Use this as a guide to replicate the process on similar projects. Follow each section carefully, adapting to the specific codebase as needed.

---

## 🧹 General Cleanup
- **Remove unused assets from the root directory:**
  - Delete all images stored in the project root.
  - Remove any unused service workers or redundant files (e.g., old images, miscellaneous files).
- **Delete unused pages:**
  - Identify and remove any pages no longer in use, including redirected pages not serving a purpose.

---

## 📜 Scripts
- **Tidy up JavaScript includes:**
  - **Head Section (`js-head`):**
    - Remove unused scripts.
    - Ensure only globally required scripts remain in global includes.
  - **Footer Section (`js-foot`):**
    - Remove unused scripts.
    - Ensure only globally required scripts remain in global includes.
- **Optimize script loading:**
  - Use Webpack to split JavaScript into chunks and load page-specific scripts dynamically.
  - For third-party scripts not needed on page load (e.g., used further down the page), consider lazy-loading with Intersection Observer.
  - Prevent main thread blocking by adding the `defer` attribute to scripts (e.g., jQuery).
- **Remove unused script dependencies:**
  - Delete unused JavaScript files from the codebase.
- **Remove unused code in scripts:**
  - For each script in the `js` directory:
    - Copy its relative filepath and check if it is being used anywhere on the site. If not, remove it from the codebase.
  - For each remaining script:
    - Review and ensure all functions are necessary and correctly used (e.g., remove `querySelector` calls for IDs or classes that don’t exist in the codebase).
    - Test thoroughly after any changes to confirm functionality.

---

## 🎨 Styles
- **Clean up SCSS and CSS:**
  - Identify and remove unused styles:
    - For each SCSS module in the `src` directory:
      - Use VS Code global search to check if main style rules are used in template files (e.g., `.aspx`, `.ascx`, `.bsk`, `.html`) or CMS grid.
      - If unused, comment out initially for testing, then remove permanently.
      - *Note:* For SCSS modules using SASS ampersand (`&`) syntax, adjust search strings to match the compiled full selector.
  - Organize styles by scope:
    - Ensure only truly global styles remain in the global stylesheet.
    - For non-global SCSS modules:
      - Compile the SCSS module to CSS.
      - Move the resulting CSS file to the `css` directory.
      - Load these smaller CSS modules on relevant pages only.
- **Optimize Bootstrap usage:**
  - Remove unused Bootstrap variables and styles (e.g., eliminate unnecessary table variants if not used).
  - Delete unused Bootstrap modules or plugins.
- **Remove unused fonts:**
  - Check and remove fonts not in use across the site.

---

## 🖼️ Images
- **Clean up image assets:**
  - Remove unused images (e.g., ensure no images remain in the project root).
  - Verify image sizes:
    - Ensure images are appropriately sized for their display area.
    - Optimize images using the ImgEngine CDN with correct query string parameters for size and compression.
  - **Enhance image delivery:**
    - Use the Sirv profile to set sizing and cache times for Sirv-hosted assets.
    - Add appropriate `fetchpriority` attributes (e.g., `fetchpriority="high"` for the first banner image).
- **Preconnect to image resources:**
  - Add preconnect tags for key image CDNs, e.g., `<link rel="preconnect" href="https://bluesky.sirv.com">`.

---

## 🌐 Globally Included Assets
- **Validate global assets:**
  - Ensure globally included assets (e.g., fonts, icons, third-party scripts) are actually used site-wide.
  - If an asset is only used on specific pages, remove it from global includes and load it only where needed.

---

## ⭐ Icons
- **Remove unused icon libraries and imports:**
  - Check and delete any icon libraries or specific icon imports not in use across the site.
  - Ensure globally included assets are actually used globally. If not, include only on pages used. 

---

## ⚡ Additional Optimizations
- **Preconnect to main resources:**
  - Add `<link rel="preconnect">` tags for critical external resources (e.g., CDNs like Sirv) to improve loading times.

---

## 📝 Notes for Execution
- Always test changes incrementally
- Use branching in git to track / compare changes and revert if necessary.
- Validate performance improvements post-cleanup using tools like Lighthouse or browser DevTools.
