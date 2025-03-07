
# 300 Project GitHub Workflows Documentation 📝

## Overview 📖
This documentation covers the GitHub Actions workflows used in the 300 Project. These workflows automate site generation, deployment, and maintenance tasks across multiple repositories. The system is designed to handle both vanilla deployments and template-based site generation.

## Core Workflows 🔄

### 1. Entry Points 📥

#### Post-Request Site Generation
- **File**: `entry-specific-sites-on-post.yml`
- **Trigger**: Repository dispatch event (`dispatch_300`)
- **Purpose**: Handles site generation and deployment based on POST requests
- **Features**:
  - Supports multiple website IDs
  - Flexible deployment types (vanilla-only, template-only, or both)
  - Integrates with BSK 300 API endpoint

#### Release-Based Deployment
- **File**: `entry-all-sites-on-release.yml`
- **Trigger**: Release events
- **Purpose**: Deploys changes across all sites when releases occur

### 2. Core Processing Workflows 🛠️

#### Vanilla Deployment
- **File**: `called-vanilla-deploy.yml`
- **Purpose**: Handles traditional FTP-based deployments
- **Key Features**:
  - Processes site data in JSON format
  - Supports single or multiple website deployments
  - Uses FTP for file synchronization

#### Site Generator
- **File**: `called-site-generator.yml`
- **Purpose**: Generates sites using templates
- **Key Features**:
  - Clones or creates repositories as needed
  - Compiles sites using watcher
  - Handles automated commits and pushes

## Workflow Architecture 🏗️

### Data Flow
1. Entry workflow receives trigger
2. Site data is fetched and processed
3. Deployment type determines workflow path:
   - Vanilla deployment → FTP sync
   - Template generation → Site compilation
   - Both → Sequential execution

### Security 🔒
- Uses `BSK_REPO_ACCESS` token for repository access
- Implements secure credential handling
- Utilizes repository-specific secrets

## Maintenance Guide 🔧

### Adding New Sites
1. Ensure site data is properly formatted in JSON
2. Add site ID to relevant configuration
3. Test using POST request trigger

### Modifying Workflows
1. Test changes in development environment
2. Update site data schema if needed
3. Verify backwards compatibility
4. Update documentation

### Common Issues and Solutions 🚨

#### Deployment Failures
- Check BSK API endpoint accessibility
- Verify site data format
- Ensure FTP credentials are correct

#### Generation Issues
- Verify template integrity
- Check node version compatibility
- Review build logs for errors

## Extension Guide 🔌

### Creating New Workflows
1. Create workflow file in `.github/workflows/`
2. Define appropriate triggers
3. Specify required inputs and secrets
4. Add error handling and logging

### Adding Features
1. Update site data schema if needed
2. Modify relevant workflow files
3. Test thoroughly before deployment
4. Document changes

## Best Practices 📋

### Code Management
- Use descriptive commit messages
- Follow branching strategy
- Test changes thoroughly

### Security
- Never commit secrets
- Use environment variables
- Review access permissions regularly

### Monitoring
- Check workflow logs regularly
- Monitor deployment success rates
- Track API endpoint performance

## Quick Reference 📚

### Environment Setup
```bash
# Required Node.js version
node -v  # Should be 20.17.0

# Install dependencies
npm ci
```

### Common Commands
```bash
# Trigger specific site deployment
gh workflow run entry-specific-sites-on-post.yml

# Check workflow status
gh run list

# View workflow logs
gh run view [run-id]
```

Remember to keep this documentation updated as workflows evolve and new features are added.