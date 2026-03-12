# Claude Code + Codex Collaborative Development Environment

> This project explores collaborative AI development workflows using Codex and Claude Code.

> 🚀 3-step setup, 5-minute onboarding, making AI-powered collaborative development simple

**[中文](README-zh.md) | English**

## 📋 Quick Start

### 🎯 Step 1: Run the One-Click Installer
```bash
curl -sSL https://raw.githubusercontent.com/Pluviobyte/Claude-Codex/main/install.sh | bash
```

Or download and run manually:
```bash
# Download the install script
curl -O https://raw.githubusercontent.com/Pluviobyte/Claude-Codex/main/install.sh
chmod +x install.sh
./install.sh
```

### 📋 Step 2: Choose a Configuration Type
The script offers three configuration options:
- Simple: Basic collaboration features
- Standard: Complete development environment
- Advanced: Enterprise-grade features (optional Exa search requires API key)

### ✅ Step 3: Restart and Verify
1. Restart the Claude Code application
2. Type in chat: `/available-tools`
3. Confirm that codex-related tools are visible

### Examples
<img width="606" height="540" alt="image" src="https://github.com/user-attachments/assets/52c60cb3-7e4c-4e56-aec8-ee4f4f1e4af7" />
<img width="746" height="507" alt="image" src="https://github.com/user-attachments/assets/510453cc-cc2d-4163-8865-178763411384" />


## 🛠️ Configuration Options

### Simple Configuration (Recommended for Beginners)
- Claude Code + Codex basic collaboration
- Sequential-thinking for deep analysis
- Ideal for quick exploration and learning

### Standard Configuration (Recommended for Daily Use)
- Complete collaborative development environment
- Task management and code indexing
- Ideal for everyday development work

### Advanced Configuration (Recommended for Power Users)
- Enterprise-grade development environment
- Browser debugging and web search
- Ideal for complex project development

## 🎯 Core Features

### 🤖 AI Collaboration Modes
- **Claude Code**: Project management and code execution
- **Codex**: Deep code analysis and generation
- **Smart Delegation**: Simple tasks handled directly by Claude, complex logic delegated to Codex

### 🔧 Intelligent Workflow
1. **Requirement Understanding** → Deep thinking analysis
2. **Context Collection** → Comprehensive code retrieval
3. **Task Planning** → Intelligent task decomposition
4. **Code Execution** → Incremental iterative development
5. **Quality Verification** → Automated testing and review

### ⚡ Core Advantages
- **Zero Learning Curve**: Built on the familiar Claude Code interface
- **Smart Defaults**: Pre-configured best practices, fewer configuration decisions
- **Progressive Enhancement**: Scale from simple to advanced as needed
- **High Reliability**: Complete error handling and automatic recovery

## 📚 Usage Examples

### Basic Conversation
```
User: Help me create a React component that displays a user list

Claude: I'll help you create a React component for displaying a user list. Let me first invoke Codex for deep analysis, then implement this feature.
```

### Complex Tasks
```
User: Implement a complete user management system including authentication, CRUD operations, and permission management

Claude: This is a complex multi-module task. Let me use sequential-thinking for deep analysis, then create a detailed implementation plan.
```

## 🔍 Troubleshooting

### Common Issues

**Q: Can't see codex tools?**
A: Make sure the configuration file is correctly installed, then restart Claude Code

**Q: Codex connection failed?**
A: Make sure Codex is properly installed and you can run the `codex mcp-server` command

**Q: MCP server connection failed?**
A: Run the install script for repair, or manually install the required dependencies

For a detailed troubleshooting guide, see: [troubleshooting.md](troubleshooting.md)

## 📖 More Documentation

- [Configuration File Guide](README-config.md)
- [Troubleshooting Guide](troubleshooting.md)
- [Advanced Configuration Guide](advanced.md)
- [API Reference](api.md)

## 🤝 Contributing

Contributions and improvement suggestions are welcome!

## 📄 License

MIT License - See [LICENSE](LICENSE) file for details

---

**Start your AI collaborative development journey!** 🚀
