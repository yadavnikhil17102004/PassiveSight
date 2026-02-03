# TRACEGUARD AI - Community Edition

<div align="center">

![TRACEGUARD Logo]([REDACTED_URL])
[![License: MIT]([REDACTED_URL])](LICENSE)
[![Burp Suite]([REDACTED_URL])]([REDACTED_URL])
[![Python]([REDACTED_URL])]([REDACTED_URL])

### 🔗 ⛓️ 🔒

**AI-Powered Passive Vulnerability Analysis for Burp Suite**

*Intelligent • Silent • Adaptive • Comprehensive*

[🚀 Getting Started](#-quick-start) • [📖 Documentation](#-documentation) • [🔧 Configuration](#-configuration) • [⬆️ Upgrade to Pro](#-upgrade-to-professional)

</div>

---

## 🌟 Overview

**TRACEGUARD AI - Community Edition** is a free, open-source Burp Suite extension that brings the power of artificial intelligence to web application security testing. Using advanced AI models, TRACEGUARD performs intelligent passive analysis of HTTP traffic to identify OWASP Top 10 vulnerabilities, security misconfigurations, and potential attack vectors.

### Why TRACEGUARD?

Traditional security scanners rely on predefined signatures and patterns. **TRACEGUARD AI** goes beyond with:

- **🧠 AI-Powered Analysis**: Leverages state-of-the-art language models (Ollama, OpenAI, Claude, Gemini) for intelligent vulnerability detection
- **🎯 Context-Aware Detection**: Understands application logic and business context, not just pattern matching
- **⚡ Real-Time Scanning**: Analyzes traffic as it flows through Burp's proxy
- **📊 Professional Reporting**: Generates detailed findings with CWE, OWASP mappings, and remediation guidance
- **🔄 Zero False Positives**: AI validation reduces noise and focuses on real vulnerabilities
- **🆓 100% Free**: Community edition provides full passive analysis capabilities

---

## ✨ Features

### Core Capabilities

#### 🔍 **Passive AI Analysis**
- Real-time traffic analysis through Burp Proxy
- OWASP Top 10 vulnerability detection
- CWE-mapped security findings
- Intelligent confidence scoring

#### 🎨 **Professional UI**
- Modern, intuitive dashboard
- Live findings panel with severity color-coding
- Task tracking and management
- Integrated console logging

#### 🤖 **Multi-AI Support**
- **Ollama** (Local, free, privacy-focused)
- **OpenAI** (GPT-4, GPT-3.5)
- **Claude** (Anthropic)
- **Gemini** (Google)

#### 📋 **Smart Reporting**
- Detailed vulnerability descriptions
- Affected parameters identification
- CWE and OWASP mappings
- Remediation recommendations
- Direct links to security resources

### Vulnerability Detection

TRACEGUARD AI detects a wide range of security issues including:

| Category | Vulnerabilities |
|----------|----------------|
| **Injection** | SQL Injection, NoSQL Injection, Command Injection, LDAP Injection, XPath Injection |
| **Cross-Site Scripting** | Reflected XSS, Stored XSS, DOM-based XSS |
| **Authentication** | Broken Authentication, Session Management Issues, Credential Exposure |
| **Access Control** | IDOR, Broken Authorization, Privilege Escalation |
| **Cryptography** | Weak Encryption, Insecure SSL/TLS, Sensitive Data Exposure |
| **Configuration** | Security Misconfigurations, Default Credentials, Debug Enabled |
| **XXE** | XML External Entity Attacks |
| **Deserialization** | Insecure Deserialization |
| **Components** | Vulnerable Dependencies, Outdated Libraries |

---

## 🚀 Quick Start

### Prerequisites

- **Burp Suite** (Community or Professional)
- **Java 8+** (required by Burp)
- **Python 2.7** (Jython, included with Burp)
- **AI Provider** (one of the following):
  - [Ollama]([REDACTED_URL]) (Free, local)
  - OpenAI API key
  - Claude API key
  - Gemini API key

### Installation

1. **Download the Extension**
   ```bash
   git clone [REDACTED_URL]
   cd traceguard-ai
   ```

2. **Load in Burp Suite**
   - Open Burp Suite
   - Go to `Extensions` → `Installed`
   - Click `Add`
   - Set Extension type: `Python`
   - Select `traceguard_ai_community.py`
   - Click `Next`

3. **Configure AI Provider**
   - Go to `TRACEGUARD` tab in Burp
   - Click `⚙ Settings`
   - Configure your AI provider (see [Configuration](#-configuration))
   - Click `Test Connection`
   - Click `Save`

4. **Start Scanning**
   - Set your target scope in Burp (`Target` → `Scope`)
   - Browse the target application through Burp's proxy
   - TRACEGUARD will automatically analyze traffic
   - View findings in the `Findings` panel and Burp's `Issue Activity`

---

## 🔧 Configuration

### AI Provider Setup

#### Option 1: Ollama (Recommended for Beginners)

**Free, local, no API keys required**

1. Install Ollama:
   ```bash
   # macOS/Linux
   curl -fsSL [REDACTED_URL] | sh
   
   # Windows
   # Download from [REDACTED_URL]
   ```

2. Pull a model:
   ```bash
   ollama pull deepseek-r1
   # or
   ollama pull llama3
   ```

3. Configure TRACEGUARD:
   - Provider: `Ollama`
   - API URL: `[REDACTED_URL]`
   - Model: `deepseek-r1:latest`

#### Option 2: OpenAI

1. Get API key from [platform.openai.com]([REDACTED_URL])

2. Configure TRACEGUARD:
   - Provider: `OpenAI`
   - API URL: `[REDACTED_URL]`
   - API Key: `sk-...`
   - Model: `gpt-4` or `gpt-3.5-turbo`

#### Option 3: Claude (Anthropic)

1. Get API key from [console.anthropic.com]([REDACTED_URL])

2. Configure TRACEGUARD:
   - Provider: `Claude`
   - API URL: `[REDACTED_URL]`
   - API Key: Your Anthropic API key
   - Model: `claude-3-5-sonnet-20241022`

#### Option 4: Google Gemini

1. Get API key from [makersuite.google.com]([REDACTED_URL])

2. Configure TRACEGUARD:
   - Provider: `Gemini`
   - API URL: `[REDACTED_URL]`
   - API Key: Your Google API key
   - Model: `gemini-1.5-pro`

### Settings Reference

| Setting | Description | Default |
|---------|-------------|---------|
| **AI Provider** | AI service to use | `Ollama` |
| **API URL** | Provider endpoint | `[REDACTED_URL]` |
| **API Key** | Authentication key | *(empty for Ollama)* |
| **Model** | AI model name | `deepseek-r1:latest` |
| **Max Tokens** | Response length limit | `2048` |
| **Verbose Logging** | Enable detailed logs | `True` |

---

## 📖 Documentation

### How It Works

1. **Traffic Interception**: TRACEGUARD monitors HTTP requests/responses through Burp Proxy
2. **Scope Filtering**: Only analyzes in-scope targets (configure in Burp's Target Scope)
3. **AI Analysis**: Sends request/response data to AI for security analysis
4. **Vulnerability Detection**: AI identifies security issues based on OWASP Top 10 patterns
5. **Finding Generation**: Creates detailed reports with severity, confidence, and remediation
6. **Deduplication**: Prevents duplicate findings for the same URL/parameter combination

### Finding Confidence Levels

| Level | AI Confidence | Meaning |
|-------|---------------|---------|
| **Certain** | 90-100% | High confidence, verified vulnerability pattern |
| **Firm** | 75-89% | Strong indicators, likely vulnerable |
| **Tentative** | 50-74% | Potential issue, requires manual verification |

### UI Components

#### 📊 **Statistics Panel**
- Total Requests: HTTP requests analyzed
- Analyzed: Successfully processed
- Skipped (Duplicate): Prevented redundant analysis
- Findings Created: Total vulnerabilities found
- Errors: Analysis failures

#### 📋 **Active Tasks**
- Shows currently processing requests
- Status tracking (Queued, Analyzing, Completed)
- Duration timing

#### 🔍 **Findings Panel**
- All detected vulnerabilities
- Severity-based color coding:
  - 🔴 **High** - Critical vulnerabilities
  - 🟠 **Medium** - Important security issues
  - 🟡 **Low** - Minor vulnerabilities
  - 🔵 **Information** - Security notes
- Confidence levels
- Discovery timestamps

#### 🖥️ **Console**
- Real-time logging
- AI connection status
- Analysis progress
- Error messages

---

## 🎯 Usage Examples

### Basic Workflow

1. **Set Target Scope**
   ```
   Burp → Target → Scope → Add
   Example: [REDACTED_URL]
   ```

2. **Browse Application**
   - Configure browser proxy to Burp (127.0.0.1:8080)
   - Navigate through the target application
   - TRACEGUARD analyzes in the background

3. **Review Findings**
   - Check `TRACEGUARD` → `Findings` panel
   - Or `Target` → `Issue Activity` (integrated with Burp)

### Context Menu Analysis

Right-click any request in:
- Proxy History
- Site Map
- Repeater

Select: `TRACEGUARD - Analyze Request`

This forces analysis even if the URL was previously scanned.

### Manual Verification

1. Select a finding in the Findings panel
2. Review the detailed description
3. Check affected parameters
4. Follow CWE/OWASP links for more information
5. Manually test using Burp Repeater/Intruder

---

## 🆚 Community vs Professional

| Feature | Community (Free) | Professional |
|---------|------------------|--------------|
| **AI-Powered Passive Analysis** | ✅ | ✅ |
| **OWASP Top 10 Detection** | ✅ | ✅ |
| **Multi-AI Support** | ✅ | ✅ |
| **Professional UI** | ✅ | ✅ |
| **CWE/OWASP Mapping** | ✅ | ✅ |
| **Deduplication** | ✅ | ✅ |
| **Phase 2 Active Verification** | ❌ | ✅ |
| **Advanced Payload Libraries** | ❌ | ✅ |
| **WAF Detection & Evasion** | ❌ | ✅ |
| **Out-of-Band (OOB) Testing** | ❌ | ✅ |
| **Burp Intruder Integration** | ❌ | ✅ |
| **Automatic Fuzzing** | ❌ | ✅ |
| **Priority Support** | ❌ | ✅ |

### ⬆️ Upgrade to Professional

**TRACEGUARD Professional** adds active verification capabilities:

- 🎯 **Phase 2 Verification**: Automatically validates findings with exploit payloads
- 🛡️ **WAF Detection**: Identifies and adapts to web application firewalls
- 📚 **Curated Payload Libraries**: Battle-tested OWASP payloads
- 🌐 **OOB Testing**: Detects blind vulnerabilities (SSRF, XXE, etc.)
- 🔄 **Burp Intruder Integration**: Auto-configures fuzzing attacks
- ⚡ **Smart Fuzzing**: AI-generated payloads for maximum coverage

**[Learn More & Upgrade →]([REDACTED_URL])**

---

## 🛠️ Troubleshooting

### Common Issues

#### "AI connection test failed"

**Solution:**
- Check AI provider is running (Ollama: `ollama list`)
- Verify API URL is correct
- For cloud providers, confirm API key is valid
- Check network connectivity

#### "No findings detected"

**Solution:**
- Verify target is in scope (`Target` → `Scope`)
- Ensure traffic is flowing through Burp Proxy
- Check Console for errors
- Try manual analysis (right-click → `TRACEGUARD - Analyze Request`)

#### "Extension fails to load"

**Solution:**
- Verify Burp Suite version (Community/Pro)
- Check Python environment (Jython 2.7)
- Review `Extender` → `Errors` tab
- Ensure file permissions are correct

#### High Memory Usage

**Solution:**
- Reduce Max Tokens setting (Settings → AI Provider)
- Clear completed tasks regularly
- Use lighter AI models (e.g., `llama3` instead of `deepseek-r1`)

### Debug Mode

Enable verbose logging:
1. `Settings` → `Advanced`
2. Check `Verbose Logging`
3. Review Console for detailed output

---

## 🤝 Contributing

We welcome contributions! Here's how you can help:

### Reporting Bugs

1. Check [existing issues]([REDACTED_URL])
2. Create a new issue with:
   - Burp Suite version
   - TRACEGUARD version
   - AI provider/model
   - Steps to reproduce
   - Error messages (from Console)

### Feature Requests

Open an issue with tag `enhancement`:
- Describe the feature
- Explain use case
- Provide examples if possible

### Code Contributions

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit changes (`git commit -m 'Add amazing feature'`)
4. Push to branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Development Guidelines

- Follow existing code style
- Add comments for complex logic
- Test with multiple AI providers
- Update documentation

---

## 📄 License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

```
MIT License

Copyright (c) 2025 TRACEGUARD AI

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all
copies or substantial portions of the Software.
```

---

## 🔒 Security & Privacy

### Data Handling

- **Local Processing**: TRACEGUARD runs entirely within Burp Suite
- **No Data Collection**: We don't collect or transmit usage data
- **AI Provider Privacy**:
  - **Ollama**: Completely local, no external communication
  - **Cloud Providers**: Data sent to respective AI services (OpenAI, Claude, Gemini)

### Best Practices

1. **Use Ollama** for sensitive testing (100% local, private)
2. **Review AI Provider Terms** before using cloud services
3. **Never test production** without authorization
4. **Sanitize Data** if sharing logs/findings

---

## 💬 Support & Community

### Get Help

- 📚 **Documentation**: [traceguard.ai/docs]([REDACTED_URL])
- 💬 **Discord**: [Join our community]([REDACTED_URL])
- 🐛 **Issues**: [GitHub Issues]([REDACTED_URL])
- ✉️ **Email**: [REDACTED_EMAIL]

### Stay Updated

- ⭐ **Star** this repository
- 👁️ **Watch** for updates
- 🐦 **Twitter**: [@TraceGuardAI]([REDACTED_URL])
- 📧 **Newsletter**: [Subscribe]([REDACTED_URL])

---

## 🙏 Acknowledgments

Built with:
- [Burp Suite]([REDACTED_URL]) by PortSwigger
- [Ollama]([REDACTED_URL]) for local AI
- [OpenAI]([REDACTED_URL]) for GPT models
- [Anthropic]([REDACTED_URL]) for Claude
- [Google]([REDACTED_URL]) for Gemini

Inspired by the security community's dedication to making the web safer.

---

## 📈 Roadmap

### Upcoming Features

- [ ] Enhanced UI/UX improvements
- [ ] Export findings to PDF/CSV
- [ ] Integration with CI/CD pipelines
- [ ] Support for custom AI models
- [ ] Collaborative team features
- [ ] Mobile app companion

### Professional Edition Roadmap

- [ ] Advanced WAF fingerprinting
- [ ] ML-powered false positive reduction
- [ ] Custom payload templates
- [ ] Automated exploit generation
- [ ] Vulnerability chaining detection

---

<div align="center">

### 🔗 ⛓️ 🔒

**TRACEGUARD AI** - *Intelligent Security Testing for the Modern Web*

[Website]([REDACTED_URL]) • [Documentation]([REDACTED_URL]) • [Professional Edition]([REDACTED_URL])

Made with ❤️ by the TRACEGUARD team

</div>
