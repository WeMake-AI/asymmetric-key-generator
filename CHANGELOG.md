# 📋 Changelog

All notable changes to the **Asymmetric Key Generator** project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/), and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [Unreleased]

### 🔄 In Development

- Enhanced documentation with WeMake standards alignment
- Improved security guidelines and best practices
- Extended API documentation and examples

---

## [1.1.4] - 2025-08-30

### ✨ Added

- **CLI Interface**: Complete command-line support for automated key generation
- **Batch Generation**: Generate multiple key pairs in a single operation
- **Custom Naming**: Configurable output file prefixes and naming conventions
- **Passphrase Protection**: AES-256-CBC encryption for private keys
- **Progress Tracking**: Real-time generation status in both CLI and GUI

### 🔄 Changed

- **UI/UX Improvements**: Enhanced interface layout and user experience
- **Error Handling**: Comprehensive validation and error reporting
- **Dependencies**: Updated all packages to latest stable versions
  - Build: electron-builder v26, @electron/notarize v3
  - Lint: ESLint v9 (+ plugins)
  - Runtime: electron-util v0.18
- **Performance**: Optimized key generation algorithms for better speed

### 🐛 Fixed

- **Progress Display**: Accurate progress indicators during batch operations
- **File Dialogs**: Resolved save dialog issues on macOS systems
- **Memory Usage**: Optimized memory consumption for large batch operations
- **Cross-Platform**: Improved compatibility across Windows, macOS, and Linux

### 🔒 Security

- Enhanced entropy collection for key generation
- Improved passphrase validation and strength checking
- Secure memory handling for sensitive operations

### 📝 Notes

- CI/tooling may require Node ≥ 18.18 (ESLint 9) and updated Apple notarization config (electron-builder 26/@electron/notarize 3)
- If you still use .eslintrc, migrate to flat config (eslint.config.js)

---

## [1.1.3] - 2025-08-30

### ✨ Added

- **RSA-4096 Support**: High-security 4096-bit RSA key generation
- **Progress Indicators**: Real-time visual feedback during operations
- **Key Validation**: Enhanced cryptographic key integrity checks
- **Export Options**: Multiple output formats and locations

### 🔄 Changed

- **Code Quality**: Refactored formatting with consistent indentation, quote styles, and line breaks
- **UI Components**: Modernized interface with better accessibility
- **Security Measures**: Strengthened cryptographic implementations
- **Build System**: Enhanced cross-platform build reliability
- **macOS Notarization**: Implemented app notarization for macOS distribution

### 🐛 Fixed

- **Platform Compatibility**: Resolved issues across different operating systems
- **Key Export**: Fixed export functionality and file format consistency
- **Memory Leaks**: Addressed memory management in long-running operations
- **Code Cleanup**: Removed unused imports and improved code readability

---

## [1.0.0]

### ✨ Added

- **Passphrase Support**: Optional passphrase parameter for enhanced security
- **Stable API**: First stable release with backward compatibility guarantee

### 🔄 Changed

- **Version Scheme**: Adopted semantic versioning for stable releases
- **Documentation**: Comprehensive user and developer documentation

---

## [0.5.3]

### 🔄 Changed

- **Dependencies**: Updated all dependencies to latest versions
- **Security**: Applied security patches and vulnerability fixes

---

## [0.5.2]

### 🔄 Changed

- **Dependencies**: Updated all dependencies to latest versions
- **Performance**: Minor performance improvements and optimizations

---

## [0.5.1]

### 🔄 Changed

- **Dependencies**: Updated all dependencies to latest versions
- **Stability**: Enhanced application stability and error handling

---

## [0.5.0]

### ✨ Added

- **Ed25519 Default**: Set Ed25519 as default key generation algorithm
- **Branding**: Updated application name and branding

### 🔄 Changed

- **Algorithm Priority**: Prioritized modern cryptographic algorithms
- **User Experience**: Simplified key type selection process

---

## [0.4.0]

### ✨ Added

- **Ed25519 Support**: Added support for Ed25519 elliptic curve keys
- **Algorithm Selection**: Multiple cryptographic algorithm options

### 🔄 Changed

- **Cryptographic Options**: Expanded key generation capabilities
- **Security**: Enhanced cryptographic algorithm support

---

## [0.3.1]

### 🐛 Fixed

- **UI Feedback**: Fixed tooltip display on canceled save operations
- **User Experience**: Improved feedback for user actions

### 🔄 Changed

- **Dependencies**: Updated dependencies to latest versions

---

## [0.3.0]

### ✨ Added

- **Error Messaging**: Added comprehensive error messages for unsaved keys
- **User Guidance**: Enhanced user feedback and guidance system

### 🔄 Changed

- **Project Structure**: Restructured files for better organization
- **Code Architecture**: Improved modular design and maintainability

---

## [0.2.0]

### ✨ Added

- **Key Size Validation**: Restricted key generation to secure 2048 and 4096 bit sizes
- **Download Management**: Enhanced file download dialog handling

### 🐛 Fixed

- **macOS Compatibility**: Fixed window reopening error on macOS systems
- **File Operations**: Improved file save and download reliability

### 🔒 Security

- **Key Standards**: Enforced minimum security standards for key generation

---

## [0.1.1]

### 🎉 Initial Release

### ✨ Added

- **Core Functionality**: Basic asymmetric key generation capability
- **RSA Support**: Initial RSA key pair generation
- **File Export**: Basic key export functionality
- **Cross-Platform**: Windows, macOS, and Linux support

### 📚 Documentation

- Basic README with installation and usage instructions
- MIT License implementation
- Initial project documentation

---

## 🔗 Links

- **Repository**: [GitHub](https://github.com/WeMake-AI/asymmetric-key-generator)
- **Releases**: [GitHub Releases](https://github.com/WeMake-AI/asymmetric-key-generator/releases)
- **Issues**: [Bug Reports & Feature Requests](https://github.com/WeMake-AI/asymmetric-key-generator/issues)
- **WeMake AI**: [Official Website](https://wemake.cx)

---

<div align="center">

_This changelog is maintained according to [WeMake AI](https://wemake.cx) documentation standards_

</div>
