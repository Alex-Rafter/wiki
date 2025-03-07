
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

## Workflow Architecture 📂

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

### Common Issues and Solutions 🚨

#### Deployment Failures
- Check BSK API endpoint accessibility
- Verify site data format
- Ensure FTP credentials are correct

#### Generation Issues
- Verify template integrity
- Review build logs for errors

