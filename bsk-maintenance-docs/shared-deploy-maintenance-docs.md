# Shared-Deploy - Codebase Maintenance 📝

## Overview 📖
This repository serves as a centralized location for reusable GitHub Actions workflows and composite actions. It's designed to provide standardized CI/CD processes that can be shared across multiple repositories within the organization.

## Repository Structure 📂

### Core Components 🛠️
1. **Reusable Workflows**
   - Located in `.github/workflows/`, these workflows are designed to be called from other repositories.
   - **Current workflows:**
     - `deploy-main.yml`: Main deployment workflow

2. **Composite Actions**
   - Source code for composite actions is located in `src/actions/`. These are compiled and output to `.github/actions/`.

3. **Build System**
   - The project uses esbuild for bundling JavaScript actions:
     - **Configuration file**: `esbuild.config.mjs`
     - **Build script**: `npm run js-action`
     - **Watch mode**: `npm run watch`

## Source Code Modules (src/actions/) 🗂️

### Core Action Modules 🌟

1. **check-inputs/** ✅
   - **Purpose**: Validates deployment server configurations
   - **Features**:
     - Validates server inputs against allowed values (DEV1, WEB1, WEB2, WEB3, WEB4)
     - Ensures proper configuration of development, UAT, and live servers
     - Fails the workflow if invalid server configurations are detected

2. **set-creds/** 🔐
   - **Purpose**: Manages deployment credentials and environment settings
   - **Features**:
     - Sets server credentials based on branch/environment (dev/uat/main)
     - Configures server directories for deployment
     - Handles environment-specific configurations
     - Outputs server information and runner configurations

3. **create-state/** 📊
   - **Purpose**: Analyzes and establishes the codebase state
   - **Features**:
     - Performs various codebase checks:
     - Package.json presence and configuration
     - Hypersearch directory structure (both modern and legacy)
     - Build script availability
     - BSK component presence
     - Creates a global codebase state object
     - Generates deployment summaries

4. **pre-deploy/** 🚀
   - **Purpose**: Orchestrates pre-deployment tasks
   - **Features**:
     - Coordinates multiple actions:
     - Input validation
     - State creation
     - Model assignment
     - Credentials setup
     - Robots.txt configuration
     - Acts as a workflow coordinator for deployment preparation

### Utility Modules 🛠️

5. **utils/** 🧰
   - **Purpose**: Shared utility functions
   - **Features**:
     - Provides common bash execution utilities
     - Handles command output processing
     - Contains reusable helper functions

6. **summary/** 📝
   - **Purpose**: Deployment summary generation
   - **Features**:
     - Creates structured summaries of deployment processes
     - Maintains deployment state information
     - Generates deployment reports

### Specialized Actions 🎯

7. **create-robots/** 🤖
   - **Purpose**: Manages robots.txt file deployment
   - **Features**:
     - Handles environment-specific robots.txt configurations
     - Detects changes in robots.txt files
     - Copies appropriate robots.txt based on deployment environment
     - Supports both development and production configurations

8. **upload-artifact/** 📤
   - **Purpose**: Handles artifact management
   - **Features**:
     - Manages build artifact uploads
     - Configures artifact retention policies
     - Handles various file patterns for different build scenarios
     - Supports multiple build output configurations

9. **assign-model/** 🧩
   - **Purpose**: Workflow model assignment
   - **Features**:
     - Contains base workflow classes
     - Manages workflow configurations
     - Handles artifact path definitions
     - Configures working directory settings

10. **lint/** ✅
    - **Purpose**: Code quality checks
    - **Features**:
      - Performs linting operations
      - Ensures code quality standards
      - Validates code against defined rules

### Module Interactions 🤝
The actions are designed to work together in a pipeline:
- Initial Setup
- Deployment Preparation
- Build and Deploy

## Development Guide 📚

### Setting Up the Development Environment 🌱
- Clone the repository
- Install dependencies:

### Version Control 📜
- Main branch protection should be enabled at all times for this repo
- Changes should be reviewed through pull requests with a senior
- Version tags should be used for stable releases

### Branching, Testing, and Releasing Changes 🧪
- Always test changes on their own named branch. For example, rather than test on `dev` test on `maintenance/new-feature`
- When testing your new version of the deployment workflow, choose a site to test on, point the site's dev branch `deployment_caller.yml` to the your new version of shared-deploy eg 

 From
 
```yml
uses: MBBluesky/shared-workflows/.github/workflows/deploy-main.yml@v2.2.3
``` 

To

```yml
uses: MBBluesky/shared-workflows/.github/workflows/deploy-main.yml@maintenance/new-feature
``` 

- You can now test your new version of shared-deploy. The workflow will start whenever you push changes to the test site's `origin dev` 
- When you are happy with your workflow changes, and have tested everything fully, create a PR
- After the PR has been approved, merge your changes an normal
- At this point create a new release, following [basic semver conventions](https://semver.org/#summary):
 
	1. MAJOR version when you make incompatible API changes
	   
```text
	2.0.0
```
  
  2. MINOR version when you add functionality in a backward compatible manner

```text
	1.9.0
```
    
  3. PATCH version when you make backward compatible bug fixes
     
```text
	1.8.9
```

- After the new release, re-point the site you have been testing on to use the new release tag, and test again. Eg update 

 From
 
```yml
uses: MBBluesky/shared-workflows/.github/workflows/deploy-main.yml@maintenance/new-feature
``` 

To

```yml
uses: MBBluesky/shared-workflows/.github/workflows/deploy-main.yml@v2.2.4
``` 

- At this point you should be ready to test your release on other sites by re-pointing to the latest tagged version of shared-deploy

## Maintenance Guidelines 🛠️

### Adding New Workflows ➕
- Create new workflow file in `.github/workflows/`
- Use `workflow_call` trigger
- Document inputs, outputs, and secrets
- Update this documentation

### Adding New Actions ➕
- Create new action source in `src/actions/`
- Update `esbuild.config.mjs` if needed
- Build the action using `npm run js-action`
- Create action metadata in `.github/actions/`
- Document the action's purpose and usage


## Troubleshooting 🔍

### Common issues and solutions ❓

#### Build Failures 🛑
- Verify esbuild configuration
- Check for syntax errors in source files
- Ensure all dependencies are installed

#### Workflow Failures 🚨
- Check workflow logs for error messages
- Verify input parameters
- Ensure required secrets are configured

#### Action Compilation Issues ⚙️
- Clear the build directory
- Rebuild using `npm run js-action`
- Check for JavaScript syntax errors

## Security Considerations 🔒

### Secrets Management 🕵️
- Never commit secrets to the repository
- Use GitHub Secrets for sensitive data
- Review secret usage in workflows

**Note**: This documentation should be updated whenever significant changes are made to the codebase or when new features are added.

### Best Practices for Module Maintenance 🛠️

#### Adding New Functionality ➕
- Follow existing error handling patterns
- Maintain consistent logging
- Update summary generation
- Add appropriate validation

#### Modifying Existing Modules ✏️
- Preserve error handling
- Maintain backward compatibility
- Update documentation
- Test all affected workflows

### Code Style ✍️
The project uses ESLint for code style enforcement. Configuration is in `eslint.config.mjs`.