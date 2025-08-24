# Security Policy

## Supported Versions

We currently support the following versions with security updates:

| Version | Supported          |
| ------- | ------------------ |
| 1.x.x   | :white_check_mark: |

## Reporting a Vulnerability

We take security vulnerabilities seriously. If you discover a security vulnerability, please report it privately.

### How to Report

1. **Do not** create a public issue for security vulnerabilities
2. Email security concerns to the project maintainers
3. Include as much detail as possible:
   - Description of the vulnerability
   - Steps to reproduce
   - Potential impact
   - Suggested fix (if any)

### What to Expect

- **Acknowledgment**: We will acknowledge receipt within 24-48 hours
- **Investigation**: We will investigate and assess the vulnerability
- **Timeline**: We aim to provide updates every 72 hours during investigation
- **Resolution**: Critical vulnerabilities will be patched within 7 days
- **Disclosure**: Coordinated disclosure after patch is available

### Security Best Practices

When using this template:

1. **Dependencies**: Regularly update dependencies and run security audits
2. **Secrets**: Never commit API keys, certificates, or sensitive data
3. **CI/CD**: Use the included security scanning in the CI pipeline
4. **Mobile Security**: Follow the security guidelines in `instructions_mobile.md`

### Security Features

This template includes:

- Dependency vulnerability scanning
- Secret detection in CI/CD
- Secure coding guidelines
- Certificate pinning examples
- Secure storage patterns

Thank you for helping keep this project secure!
