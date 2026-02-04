⚠️ **For detailed technical architecture, cryptographic design, and security analysis, please refer to the [Whitepaper](https://github.com/zephyrus-development/zephyrus-cli/wiki/WHITEPAPER).**

---

# Zephyrus CLI

A secure, encrypted file vault backed by GitHub. Store your sensitive files with confidence using end-to-end encryption and git-based version control.

## What is Zephyrus CLI?

Zephyrus CLI is a command-line tool that transforms your GitHub repository into a private, encrypted file vault. Your files are encrypted locally before being uploaded, ensuring that even if your GitHub repository is compromised, your data remains secure.

Want an interactive demo of our sharing capabilities, [click here](https://zephyrus-development.github.io/shared/#zephyrus-development:SPgkup:password:RG93bmxvYWRNZS50eHQ=) to download a demo txt file, or click the link: [https://zephyrus-development.github.io/shared/#zephyrus-development:SPgkup:password:RG93bmxvYWRNZS50eHQ=](https://zephyrus-development.github.io/shared/#zephyrus-development:SPgkup:password:RG93bmxvYWRNZS50eHQ=)

**Key Features:**
- 🔐 **End-to-End Encryption**: Files are encrypted with AES-256-GCM before leaving your computer
- 🔑 **Per-File Encryption Keys**: Each file has its own unique encryption key for secure sharing
- ☁️ **GitHub-Backed Storage**: Uses a private GitHub repository as distributed storage
- 🗂️ **Hierarchical Organization**: Create folders and organize files with full path support
- 🔍 **Search Functionality**: Quickly find files by name or path
- 📝 **Version Control**: Full git history of all vault operations
- 💻 **Cross-Platform**: Works on Windows, macOS, and Linux
- 🎯 **Stateless Mode**: Use with `-u` flag to authenticate without persistent sessions
- 🔄 **Interactive Shell**: REPL mode for multiple commands without re-authentication
- 📤 **Secure File Sharing**: Share individual files without exposing your entire vault
  - Generate shareable links with unique encryption keys
  - Share via command-line or browser-based download page
  - Recipients decrypt files in their browser (zero-knowledge sharing)
  - Complete file metadata and history in share links

## Getting Help

- **GitHub Issues**: Report bugs at [zephyrus-development/zephyrus-cli/issues](https://github.com/zephyrus-development/zephyrus-cli/issues)
- **Documentation**: See the [docs folder](./docs/) for detailed module documentation
- **Security Issues**: Email instead of opening public issues

## Contributing

Contributions are welcome! Please:

1. Fork the repository
2. Create a feature branch
3. Submit a pull request

## License

Zephyrus CLI is released under the MIT License. See LICENSE file for details.

## Disclaimer

Zephyrus CLI is provided as-is. While we've implemented industry-standard encryption, we recommend:

- Testing with non-critical files first
- Maintaining separate backups of important data
- Keeping your vault password secure
- Regularly updating to the latest version

Data loss or security issues may occur. Use at your own risk.
