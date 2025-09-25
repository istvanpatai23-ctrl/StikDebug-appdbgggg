# APPDB Improvements Documentation

## Overview

This document outlines the comprehensive improvements made to **StikDebug-appdb**, a modified version of the original StikJIT project. The application has been enhanced with deep integration of the appdb SDK and services, providing seamless functionality for users installing the app through appdb.

## Major APPDB Improvements

### 1. Automatic Pairing File Import

**Implementation**: `StikJIT/Utilities/AppdbImportManager.swift`

**Key Features**:
- **SDK Integration**: Uses `import AppdbSDK` for seamless appdb service integration
- **Automatic Detection**: Checks if app is installed via appdb using `Appdb.shared.isInstalledViaAppdb()`
- **Secure Authentication**: Retrieves required identifiers from appdb SDK:
  - `getPersistentCustomerIdentifier()`
  - `getPersistentDeviceIdentifier()`
  - `getInstallationUUID()`
- **API Integration**: Makes authenticated requests to `https://api.dbservices.to/v1.7/get_pairing_file/`
- **Automatic File Management**: Downloads and saves pairing files to the correct location
- **Progress Tracking**: Real-time import progress with visual feedback
- **Error Handling**: Comprehensive error messages with user-friendly alerts

**UI Integration**:
- **HomeView**: Displays prominent "Import from appdb" card when no pairing file exists, on the top
- **SettingsView**: Provides manual import option in pairing file section
- **Progress Indicators**: Shows import progress with animated progress bars
- **Auto UI Updates**: Automatically refreshes pairing file status after successful import

### 2. Credits for APPDB Team

**Developer Profiles**:

Adds "appdb" developer profile with icon https://appdb.to/favicon-appdb.png

### 3. Support Link Integration

**Implementation**: Multiple locations throughout the app

**Support Links Changed**:
- **APPDB Guide**: `https://appdb.to/enable-jit` (Pairing file setup guide)
- **APPDB Support**: `https://appdb.to/my/support` (General support, replaces Discord)

**Integration Points**:
- **Settings Help Card**: Links to `https://appdb.to/enable-jit` for pairing file guide and `https://appdb.to/my/support` for general support
- **HomeView Tips**: Links to APPDB JIT enablement guide
- **Info.md**: Dedicated support section with link to `https://appdb.to/enable-jit`

### 4. APPDB Version Checking via APPDB SDK

**Version Checking System**:

Uses `isAppUpdateAvailable()` method from appdb framework, redirects to opens `https://appdb.to/details/45a698af5360560fd8a522a8ebbc634da8f55df4` in case of new version available

### 5. Usage of APPDB SDK

**SDK Integration**: `AppdbFramework` version 1.6.2

**Package Configuration**: 
- **Source**: `https://dbservices.to/lib-dist/AppdbFramework-1.6.2.xcframework.zip`
- **Checksum**: `673fd13ee2a4b9f39328af175bd8b6b5322fee104c0dc823644c1891ff1b668d`
- **Platforms**: iOS 15+, tvOS 15+

**SDK Methods Utilized**:
- `isInstalledViaAppdb()`: Validates appdb installation
- `getPersistentCustomerIdentifier()`: Retrieves customer authentication
- `getPersistentDeviceIdentifier()`: Device-specific identification
- `getInstallationUUID()`: Installation tracking
- `getAppleBundleIdentifier()`: App bundle identification
- `getAppleAppGroupIdentifier()`: Shared container access
- `isAppUpdateAvailable()`: Checks for app update available on appdb

**Security Features**:
- **App Group**: `group.to.appdb.jit-ios` for secure data sharing
- **Entitlements**: Proper iOS security model integration
- **Authentication**: Secure API communication with appdb services


### Dependencies
- **AppdbSDK**: Core appdb service integration

### Build Configuration
- **Bundle ID**: `to.appdb.jit-ios`
- **App Group**: `group.to.appdb.jit-ios`
- **Minimum iOS**: 17.4+
- **Architecture**: arm64 (iOS devices)
- **Version naming**: Follows upstream, but with a-z variants, e.g. `2.0.0` -> `2.0.0a`

## Comparison with Upstream

### APPDB-Enhanced Features
- **Automatic pairing file import** from appdb services
- **Added appdb credits**
- **Links to appdb support insteead of original one**
- **Automated version checking** with user notifications from appdb


### Upstream to-dos

 - **Integrate appdb pairing file import**
 - **Replace version checking with appdb one**
 - **Change bundle IDs and version numbers***

### Sample code

See `appdb_sample.swift`