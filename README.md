<div align="center">

# 🔐 Asymmetric Key Generator

**A secure, cross-platform tool for generating cryptographic key pairs**

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT) [![Electron](https://img.shields.io/badge/Electron-28.3.2-47848F.svg)](https://electronjs.org/) [![Bun](https://img.shields.io/badge/Bun-1.2.0+-000000.svg)](https://bun.sh/)

_Built with 💙 by [WeMake AI](https://wemake.cx)_

</div>

## 📋 Overview

Asymmetric Key Generator is a professional-grade, cross-platform desktop application and CLI tool designed for secure generation of cryptographic key pairs. Supporting industry-standard algorithms including Ed25519 and RSA (2048/4096-bit), this tool provides both graphical and command-line interfaces for maximum flexibility.

### ✨ Key Features

- **🔒 Multiple Algorithms**: Ed25519, RSA-2048, and RSA-4096 support
- **🖥️ Cross-Platform**: Native apps for macOS, Windows, and Linux
- **⚡ CLI & GUI**: Both command-line and graphical interfaces
- **🔐 Passphrase Protection**: Optional encryption for private keys
- **📦 Batch Generation**: Generate multiple key pairs simultaneously
- **🛡️ Secure by Design**: PKCS#8 format with AES-256-CBC encryption
- **✅ Integrity Verification**: SHA256 checksums for downloaded packages

## 🚀 Quick Start

Choose your preferred installation method:

### 📥 Option 1: Download Pre-built Application

Get the latest release for your platform:

**[📦 Download from Releases](https://github.com/WeMake-AI/asymmetric-key-generator/releases)**

| Platform | Package Type | Architecture                      |
| -------- | ------------ | --------------------------------- |
| macOS    | `.dmg`       | Universal (Intel + Apple Silicon) |
| Windows  | `.exe`       | x64                               |
| Linux    | `.AppImage`  | x64                               |

#### 🔍 Verify Package Integrity

For security, always verify downloaded packages:

```sh
# Option A: Using provided CHECKSUM file
sha256sum -c AsymmetricKeyGenerator-<VERSION>-universal.dmg.CHECKSUM

# Option B: Manual verification (compare with value in Releases)
sha256sum AsymmetricKeyGenerator-<VERSION>-universal.dmg
```

✅ **Success**: `AsymmetricKeyGenerator-<VERSION>-universal.dmg: OK`

### 🛠️ Option 2: Build from Source

#### Prerequisites

- **Bun**: `>= 1.2.0` ([Install Bun](https://bun.sh/docs/installation))
- **Node.js**: `>= 18.18` (for ESLint 9 compatibility)
- **Git**: For cloning the repository

#### Build Steps

```sh
# Clone the repository
git clone https://github.com/WeMake-AI/asymmetric-key-generator.git
cd asymmetric-key-generator

# Install dependencies
bun install

# Run in development mode
bun run start

# Build for all platforms
bun run dist

# Build for specific platform
bun run pack  # Development build only
```

#### 📁 Build Output

Built applications will be available in the `dist/` directory:

```
dist/
├── AsymmetricKeyGenerator-1.1.4.dmg          # macOS
├── AsymmetricKeyGenerator Setup 1.1.4.exe    # Windows
└── AsymmetricKeyGenerator-1.1.4.AppImage     # Linux
```

## 💻 Usage

### 🖥️ Graphical User Interface (GUI)

Launch the desktop application:

```sh
# From source
bun run start

# Or run the installed application
# macOS: Open AsymmetricKeyGenerator.app
# Windows: Run AsymmetricKeyGenerator.exe
# Linux: Run AsymmetricKeyGenerator.AppImage
```

The GUI provides an intuitive interface with:

- **Algorithm Selection**: Ed25519, RSA-2048, RSA-4096
- **Security Options**: Optional passphrase protection
- **Batch Generation**: Generate multiple key pairs
- **Custom Naming**: Specify output file prefix
- **Progress Tracking**: Real-time generation status
- **Export Options**: Save keys to custom locations

### ⚡ Command Line Interface (CLI)

For automation and scripting, use the CLI:

```sh
bun run cli --help
```

#### CLI Options

```
Usage: cli [options]

Options:
  -t, --type <type>        Key type (choices: "ed25519", "rsa2048", "rsa4096", default: "ed25519")
  -p, --passphrase <pass>  Passphrase for private key encryption (optional)
  -n, --number <number>    Number of key pairs to generate (default: 1)
  -o, --output <file>      Output file prefix (default: "key")
  -h, --help               display help for command
```

#### 📚 CLI Examples

**Basic Usage:**

```sh
# Generate a single Ed25519 key pair (default)
bun run cli
# Output: key_private.pem, key_public.pem
```

**Algorithm Selection:**

```sh
# Generate RSA-4096 key pair
bun run cli --type rsa4096

# Generate RSA-2048 key pair
bun run cli --type rsa2048
```

**Security & Encryption:**

```sh
# Generate encrypted private key with passphrase
bun run cli --type ed25519 --passphrase "my-secure-passphrase-2024"

# Use environment variable for passphrase (recommended)
export KEY_PASSPHRASE="my-secure-passphrase"
bun run cli --passphrase "$KEY_PASSPHRASE"
```

**Batch Generation:**

```sh
# Generate 5 key pairs with custom prefix
bun run cli --number 5 --output "server-key"
# Output: server-key-1_private.pem, server-key-1_public.pem, ...

# Generate multiple RSA keys for different services
bun run cli --type rsa4096 --number 3 --output "service-key"
```

**Advanced Examples:**

```sh
# Generate production keys with maximum security
bun run cli --type rsa4096 --passphrase "$(openssl rand -base64 32)" --output "prod-key"

# Batch generate development keys
for service in api web auth; do
  bun run cli --type ed25519 --output "dev-$service-key"
done
```

### 📋 GUI Usage Guide

1. **Launch Application**: Open the AsymmetricKeyGenerator app
2. **Select Algorithm**: Choose your preferred key type (Ed25519 recommended for most use cases)
3. **Configure Security**: Optionally set a passphrase for private key encryption
4. **Set Output Options**: Specify the number of key pairs and output prefix
5. **Generate Keys**: Click "Generate Key Pair" to create your cryptographic keys
6. **Save Securely**:
   - **Private Key**: Store in a secure location, never share
   - **Public Key**: Can be shared for signature verification

## 🔒 Security Considerations

### 🛡️ Key Management Best Practices

**Private Key Security:**

- **Never share private keys** - They should remain confidential at all times
- **Use strong passphrases** - Minimum 12 characters with mixed case, numbers, and symbols
- **Store securely** - Use encrypted storage solutions (e.g., hardware security modules, encrypted drives)
- **Regular rotation** - Replace keys periodically based on your security policy
- **Backup safely** - Store encrypted backups in multiple secure locations

**Passphrase Guidelines:**

```sh
# Good: Strong passphrase with entropy
bun run cli --passphrase "MySecure!Passphrase2024#KeyGen"

# Better: Use a password manager or environment variable
export SECURE_PASSPHRASE="$(openssl rand -base64 32)"
bun run cli --passphrase "$SECURE_PASSPHRASE"
```

### 🔐 Algorithm Recommendations

| Algorithm    | Use Case                            | Security Level       | Performance |
| ------------ | ----------------------------------- | -------------------- | ----------- |
| **Ed25519**  | Modern applications, APIs, SSH      | ⭐⭐⭐⭐⭐ Excellent | ⚡ Fast     |
| **RSA-4096** | Legacy compatibility, high security | ⭐⭐⭐⭐ Very Good   | 🐌 Slower   |
| **RSA-2048** | Legacy systems, basic compatibility | ⭐⭐⭐ Good          | 🚀 Moderate |

**Recommendation**: Use **Ed25519** for new projects due to its superior security and performance characteristics.

### 🚨 Security Warnings

- **⚠️ Quantum Resistance**: Current algorithms (RSA, Ed25519) are not quantum-resistant. Monitor post-quantum cryptography developments.
- **⚠️ Key Exposure**: If a private key is compromised, immediately revoke and replace it.
- **⚠️ Weak Randomness**: Ensure your system has sufficient entropy when generating keys.
- **⚠️ Side-Channel Attacks**: Be aware of timing attacks and other side-channel vulnerabilities in production environments.

## 🔧 API Reference

### Core Functions

#### `generateKeyPair(options)`

Generates a cryptographic key pair.

**Parameters:**

- `options.type` (string): Key algorithm - `'ed25519'`, `'rsa2048'`, or `'rsa4096'`
- `options.passphrase` (string, optional): Encryption passphrase for private key
- `options.format` (string): Output format - `'pkcs8'` (default)

**Returns:**

- `Promise<{privateKey: string, publicKey: string}>`: PEM-formatted key pair

**Example:**

```javascript
const { generateKeyPair } = require('./src/generate')

const keys = await generateKeyPair({
  type: 'ed25519',
  passphrase: 'secure-passphrase'
})

console.log('Private Key:', keys.privateKey)
console.log('Public Key:', keys.publicKey)
```

## 🛠️ Development

### 🏗️ Project Structure

```
asymmetric-key-generator/
├── src/
│   ├── main.js          # Electron main process
│   ├── preload.js       # Electron preload script
│   ├── generate.js      # Core key generation logic
│   ├── shared.js        # Shared utilities
│   └── cli.js           # Command-line interface
├── assets/
│   ├── html/index.html  # GUI interface
│   └── js/renderer.js   # Frontend logic
├── config/
│   └── electron-builder.js  # Build configuration
├── build/               # Build artifacts
├── dist/                # Distribution packages
└── package.json         # Project dependencies
```

### 🧪 Development Workflow

```sh
# Setup development environment
git clone https://github.com/WeMake-AI/asymmetric-key-generator.git
cd asymmetric-key-generator
bun install

# Development commands
bun run start           # Launch GUI in development mode
bun run cli --help      # Test CLI functionality
bun run lint            # Run ESLint checks
bun run pack            # Create development build
bun run dist            # Create production builds

# Testing
bun test                # Run test suite (if available)
```

### 📋 Contributing Guidelines

**Before Contributing:**

1. **Fork** the repository
2. **Create** a feature branch: `git checkout -b feature/amazing-feature`
3. **Follow** WeMake coding standards and ESLint configuration
4. **Test** your changes thoroughly
5. **Commit** using [Conventional Commits](https://conventionalcommits.org/)
6. **Submit** a Pull Request

**Code Standards:**

- Follow the existing ESLint configuration
- Use meaningful variable and function names
- Add JSDoc comments for public APIs
- Ensure cross-platform compatibility
- Maintain security best practices

**Commit Message Format:**

```
type(scope): description

[optional body]

[optional footer]
```

Examples:

```sh
git commit -m "feat(cli): add batch key generation support"
git commit -m "fix(security): improve passphrase validation"
git commit -m "docs(readme): update installation instructions"
```

## 🐛 Troubleshooting

### Common Issues

**Issue: "Command not found: bun"**

```sh
# Solution: Install Bun
curl -fsSL https://bun.sh/install | bash
# Or visit: https://bun.sh/docs/installation
```

**Issue: "Permission denied" on Linux/macOS**

```sh
# Solution: Make AppImage executable
chmod +x AsymmetricKeyGenerator-*.AppImage
```

**Issue: "App can't be opened" on macOS**

```sh
# Solution: Allow unsigned apps (development builds)
sudo spctl --master-disable
# Or: Right-click app → Open → Open
```

**Issue: Key generation fails**

- Ensure sufficient system entropy: `cat /proc/sys/kernel/random/entropy_avail`
- Check available disk space for output files
- Verify write permissions in output directory

### 📞 Support

For issues and questions:

- **GitHub Issues**: [Report bugs or request features](https://github.com/WeMake-AI/asymmetric-key-generator/issues)
- **Documentation**: Check this README and inline code comments
- **Security Issues**: Email <security@wemake.cx> (do not use public issues)

## 📄 License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

---

<div align="center">

**Made with 💙 by [WeMake AI](https://wemake.cx)**

_Empowering secure digital communications through robust cryptographic tools_

</div>
