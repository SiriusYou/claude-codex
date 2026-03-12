# Claude Code + Codex Collaborative Development Environment

**[中文](INDEX-zh.md) | English**

> This project explores collaborative AI development workflows using Codex and Claude Code.

## 📁 Project Structure

```
claude+codex/
├── README.md                    # Main guide (English, default)
├── README-zh.md                 # Main guide (Chinese)
├── README-config.md             # Configuration details (English)
├── README-config-zh.md          # Configuration details (Chinese)
├── troubleshooting.md           # Troubleshooting guide (English)
├── troubleshooting-zh.md        # Troubleshooting guide (Chinese)
├── INDEX.md                     # Project overview (English, default)
├── INDEX-zh.md                  # Project overview (Chinese)
├── install.sh                   # One-click install script
├── verify-config.sh             # Configuration verification script
├── claude-desktop-config.json   # Standard configuration template
├── config-simple.json           # Simple configuration template
└── config-advanced.json         # Advanced configuration template
```

## 🚀 Quick Start

### 3-Step Setup, 5-Minute Onboarding

1. **One-Click Install**
   ```bash
   curl -sSL https://raw.githubusercontent.com/Pluviobyte/Claude-Codex/main/install.sh | bash
   ```

2. **Set API Key**
   - Prepare your OpenAI API key
   - Enter the key during installation

3. **Restart and Verify**
   - Restart Claude Code
   - Type `/available-tools` to verify

## 📋 Documentation

| Document | Description | Audience |
|----------|-------------|----------|
| [README.md](README.md) | Main guide | All users |
| [README-config.md](README-config.md) | Configuration details | Users needing custom config |
| [troubleshooting.md](troubleshooting.md) | Troubleshooting guide | Users with issues |

## 🛠️ Tool Scripts

| Script | Function | Usage |
|--------|----------|-------|
| [install.sh](install.sh) | One-click install | `./install.sh` |
| [verify-config.sh](verify-config.sh) | Verify configuration | `./verify-config.sh` |

## ⚙️ Configuration Templates

| Config File | Complexity | Use Case |
|-------------|------------|----------|
| [config-simple.json](config-simple.json) | Simple | Quick start, basic development |
| [claude-desktop-config.json](claude-desktop-config.json) | Standard | Everyday development |
| [config-advanced.json](config-advanced.json) | Advanced | Complex projects, enterprise use |

## 🎯 Core Features

- **Zero Learning Curve**: Built on the familiar Claude Code interface
- **Smart Collaboration**: Claude Code + Codex dual-AI collaboration
- **One-Click Setup**: Automated installation and configuration
- **Multiple Complexity Levels**: Choose from simple to advanced as needed
- **Cross-Platform Support**: Windows/macOS/Linux

## 🤝 Collaboration Modes

### Claude Code (Primary AI)
- ✅ Project management and task planning
- ✅ Simple code writing and execution
- ✅ User interaction and final decisions
- ✅ Configuration management and environment setup

### Codex (Support AI)
- ✅ Deep code analysis and generation
- ✅ Complex algorithm design and optimization
- ✅ Code quality review and assessment
- ✅ Context collection and knowledge retrieval

## 📞 Getting Help

If you encounter issues:

1. **First run**: `./verify-config.sh` to check configuration
2. **See**: [troubleshooting.md](troubleshooting.md) troubleshooting guide
3. **Submit**: a GitHub Issue for community support

---

Start your AI collaborative development journey! 🚀
