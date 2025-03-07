
# 300 Site Generator - Technical Documentation 📝

## Overview 📖
The 300 Site Generator is a powerful tool designed to manage and generate multiple car dealership websites from a shared codebase. It uses a template-based approach where a master codebase is customized for individual dealership sites based on their specific configurations and requirements.

## Core Components 📂

### 1. Watcher System 👀
- Located in `/watcher`
- Contains the shared codebase template files
- These files are monitored for changes and this triggers recompilation

### 2. Sites Directory 🏢
- Located in `/sites`
- Contains compiled individual template sites
- Each site (e.g., `/sites/star-cars`) is a unique instance
- Generated from shared templates with site-specific data

### 3. Translation Layer 🔄
- Manages data transformation between formats
- Handles site-specific configurations
- Supports both development and production data sources
- Located in `src/scripts/translation-layer`

### 4. Automated Workflows 🤖
- GitHub Actions for automated deployments
- Handles site generation and deployment
- Manages repository creation and updates

## Key Features 🎯

### Template System
- Uses JavaScript template expressions
- Supports dynamic content injection
- Access to global site data via `data.global`
- Configurable components and layouts

### Core Compilation Engine
- Translation layer converts site configurations to build data
- File watcher system for real-time compilation
- Intelligent template processing:
  - Parses JavaScript expressions
  - Resolves dependencies
  - Handles conditional includes
- Multi-site compilation support:
  - Parallel processing of site builds
  - Site-specific asset management
  - Maintains separate build contexts
- Build output management:
  - Clean directory handling
  - Asset copying and optimization
  - Repository structure maintenance

### Site Customization
- Theme customization
- Optional features (eg finance, third-parties, etc.)
- Flexible page configurations

## Maintenance Guide 🛠️

### Adding New Features to Templates
1. Modify shared codebase in `/watcher`
2. Test changes on dev template
3. Use template expressions for dynamic content
4. Follow the dev → production workflow

### Adding New Features to Template Compiler
1. Navigate to `src/scripts/watcher` directory
2. Identify the appropriate module to modify:
   - `index.mjs` for core compilation logic
   - `logic/modules/` for specific compilation features
1. Add new compilation logic:
   - Follow existing error handling patterns
   - Add appropriate logging
   - Document any new template expressions
1. Test the compiler changes:
   - Verify compilation output in `/sites`
   - Check error handling with invalid inputs
5. Update related documentation:
   - Add new features to README
   - Document any new configuration options
   - Update template expression guide if needed

### Debugging Tips
- Check compilation logs
- Verify template expressions
- Test on dev site first
- Monitor workflow execution

### Common Tasks

#### Adding New Site Components
1. Add template file to `/watcher`
2. Include necessary data bindings
3. Test in dev environment
4. Deploy through normal workflow

#### Modifying Site Configuration
1. Update data source JSON
2. Test changes on dev template
3. Verify across different site types
4. Deploy to production

## Extension Guide 📚

### Adding New Templates
1. Create template in `/watcher`
2. Add configuration options to data schema
3. Implement template expressions
4. Test across different site configurations

### Creating Custom Features
1. Add feature flag in site configuration
2. Implement conditional rendering
3. Add necessary assets and components
4. Document in template expressions

## Data Schema Reference 📋

### Available Global Properties
- `hasMultipleDealers`
- `showStockCarousel`
- `hasVisitorChat`
- `theme`
- `socialMediaLinks`
- `headerOption`
- And many more (see README for full list)

## Best Practices 💡

1. **Template Development**
   - Use clear template expressions
   - Keep templates modular

2. **Testing**
   - Test changes on dev first
   - Verify across different site types using different themes

3. **Deployment**
   - Follow the branching workflow
   - Monitor automated deployments
   - Verify site functionality post-deployment
