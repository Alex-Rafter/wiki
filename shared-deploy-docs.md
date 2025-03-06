# Shared Workflows - Technical Documentation 📝

## Overview 🌟
This repository serves as a centralized location for reusable GitHub Actions workflows and composite actions. It's designed to provide standardized CI/CD processes that can be shared across multiple repositories within the organization.

## Repository Structure 🏗️

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

## Dependencies 📦

### Production Dependencies 🎯
- `@actions/artifact (v2.1.11)`: GitHub Actions artifact handling
- `@actions/core (v1.11.1)`: Core GitHub Actions functionality
- `@actions/exec (v1.1.1)`: Command execution utilities
- `@actions/github (v6.0.0)`: GitHub API integration
- `just-compare (v2.3.0)`: Comparison utilities
- `shelljs (v0.8.5)`: Shell command execution

### Development Dependencies 🛠️
- `esbuild (v0.24.0)`: JavaScript bundler
- `eslint (v9.15.0)`: Code linting
- Various ESLint plugins and configurations

## Development Guide 📚

### Setting Up the Development Environment 🌱
- Clone the repository
- Install dependencies:

### Building Actions 🏗️
- To build JavaScript actions:
- For development with watch mode:

### Code Style ✍️
The project uses ESLint for code style enforcement. Configuration is in `eslint.config.mjs`.

## Usage Guide 📖

### Using Reusable Workflows 🚀
To use a reusable workflow in another repository:

### Using Composite Actions 🧩
Composite actions can be referenced in workflows:

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

### Testing 🧪
Currently, there is no automated testing setup (`"test": "echo \"Error: no test specified\" && exit 1"`). Consider implementing:
- Unit tests for JavaScript actions
- Integration tests for workflows
- Workflow syntax validation

## Version Control 📜
- Main branch protection should be enabled
- Changes should be reviewed through pull requests
- Version tags should be used for stable releases

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

### Access Control 🚪
- Maintain strict branch protection rules
- Review workflow permissions regularly
- Monitor action version pinning

## Future Improvements 🚀
### Consider implementing:
- Automated testing framework
- Better documentation generation
- Version management system
- Workflow validation tools
- Performance monitoring

## Support and Contact 📞
- For issues and support:
- Create an issue in the repository
- Contact the maintainers team
- Reference the GitHub Actions documentation

**Note**: This documentation should be updated whenever significant changes are made to the codebase or when new features are added.

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

### Common Patterns 🎨

#### Error Handling 🚨
- All modules use `core.setFailed()` for error reporting
- Consistent try-catch blocks around main operations
- Detailed error messages with context

#### State Management 📊
- Global state object for codebase information
- Shared configuration through environment variables
- Consistent state updates and checks

#### Logging and Monitoring 📈
- Consistent use of `core.info()` for logging
- Start/End markers for each action
- Detailed operation logging

### Configuration Requirements ⚙️

#### Each module may require specific inputs:

##### Server Configuration 🖥️
- `dev_server`
- `uat_server`
- `live_server`
- Associated directory configurations

##### Build Configuration 🛠️
- Package.json presence
- Build script definitions
- Artifact paths and retention policies

##### Environment Settings 🌐
- Branch-specific configurations
- Environment-specific robot.txt files
- Runner configurations

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

#### Testing Changes 🧪
- Test across all supported environments
- Verify input validation
- Check error handling
- Validate summary generation