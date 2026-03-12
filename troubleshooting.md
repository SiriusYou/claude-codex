# Troubleshooting Guide

**[中文](troubleshooting-zh.md) | English**

## 🔧 Common Issues

### ❌ Can't See Codex Tools

**Problem**: Typing `/available-tools` in Claude Code doesn't show codex-related tools

**Possible Causes**:
1. Configuration file not correctly installed
2. Claude Code not restarted
3. MCP server not started

**Solutions**:
```bash
# 1. Verify configuration file
./verify-config.sh

# 2. Check configuration file location
ls -la ~/Library/Application\ Support/Claude/claude_desktop_config.json  # macOS
ls -la ~/.config/claude/claude_desktop_config.json  # Linux
ls -la %APPDATA%/Claude/claude_desktop_config.json  # Windows

# 3. Reinstall configuration
./install.sh
```

### 🔑 API Key Issues

**Problem**: API calls fail with authentication errors

**Possible Causes**:
1. Incorrect API key format
2. Expired API key
3. Insufficient account balance

**Solutions**:
```bash
# 1. Check API key format
grep "OPENAI_API_KEY" ~/.config/claude/claude_desktop_config.json

# 2. Test API key
curl -H "Authorization: Bearer YOUR_API_KEY" https://api.openai.com/v1/models

# 3. Update API key
# Edit the configuration file and replace the API key
```

**API Key Format Requirements**:
- Starts with `sk-`
- Total length of 51 characters
- Contains letters and numbers

### 🌐 Network Connection Issues

**Problem**: Unable to connect to OpenAI API

**Possible Causes**:
1. Network firewall blocking
2. Proxy configuration issues
3. DNS resolution issues

**Solutions**:
```bash
# 1. Test network connection
curl -I https://api.openai.com/v1/models

# 2. Check proxy settings
echo $HTTP_PROXY
echo $HTTPS_PROXY

# 3. Use a proxy (if needed)
export HTTPS_PROXY=http://your-proxy:port
```

### 📦 Dependency Installation Failures

**Problem**: npm or pip package installation fails

**Possible Causes**:
1. Insufficient permissions
2. Network issues
3. Version conflicts

**Solutions**:
```bash
# 1. Install with sudo (Linux/macOS)
sudo npm install -g @modelcontextprotocol/server-sequential-thinking

# 2. Clear npm cache
npm cache clean --force

# 3. Use alternative registry
npm config set registry https://registry.npmjs.org

# 4. Manually install Python packages
pip3 install --user uv
```

### 🚀 MCP Server Startup Failures

**Problem**: MCP server fails to start properly

**Possible Causes**:
1. Incompatible Node.js version
2. Python environment issues
3. Port already in use

**Solutions**:
```bash
# 1. Check Node.js version
node --version  # Requires >= 16.0.0

# 2. Check Python version
python3 --version  # Requires >= 3.8

# 3. Manually test MCP servers
npx @modelcontextprotocol/server-sequential-thinking --version
codex --version

# 4. View error logs
tail -f ~/.claude/logs/*.log
```

## 🔍 Diagnostic Tools

### Configuration Verification Script
```bash
# Run full configuration check
./verify-config.sh
```

### Manual Check Steps
```bash
# 1. Check configuration file syntax
python3 -m json.tool ~/.config/claude/claude_desktop_config.json

# 2. Test MCP servers
npx -y @modelcontextprotocol/server-sequential-thinking --help
codex mcp-server --help

# 3. Check Claude Code version
# Type in Claude Code: /version
```

## 📋 System Requirements

### Minimum Requirements
- **OS**: Windows 10+, macOS 10.15+, Ubuntu 18.04+
- **Node.js**: 16.0.0+
- **Python**: 3.8+
- **RAM**: 4GB
- **Storage**: 1GB free space

### Recommended Configuration
- **OS**: Latest version of Windows/macOS/Linux
- **Node.js**: 18.0.0+
- **Python**: 3.10+
- **RAM**: 8GB+
- **Storage**: 2GB+ free space
- **Network**: Stable internet connection

## 🔄 Reset Configuration

### Full Reset
```bash
# 1. Backup existing configuration
cp ~/.config/claude/claude_desktop_config.json ~/.config/claude/claude_desktop_config.json.backup

# 2. Delete configuration file
rm ~/.config/claude/claude_desktop_config.json

# 3. Reinstall
./install.sh
```

### Clean Up Dependencies
```bash
# Uninstall npm packages
npm uninstall -g @modelcontextprotocol/server-sequential-thinking
npm uninstall -g mcp-shrimp-task-manager
npm uninstall -g chrome-devtools-mcp
npm uninstall -g exa-mcp-server

# Uninstall Python packages
pip uninstall uv
```

## 📞 Getting Help

### Community Support
- **GitHub Issues**: https://github.com/Pluviobyte/Claude-Codex/issues
- **Discussions**: https://github.com/Pluviobyte/Claude-Codex/discussions

### Log Collection
```bash
# Collect system information
./collect-logs.sh

# Manually collect logs
echo "=== System Info ===" > debug.log
uname -a >> debug.log
node --version >> debug.log
python3 --version >> debug.log
echo "" >> debug.log

echo "=== Config File ===" >> debug.log
cat ~/.config/claude/claude_desktop_config.json >> debug.log
echo "" >> debug.log

echo "=== Network Test ===" >> debug.log
curl -I https://api.openai.com/v1/models >> debug.log
```

## 🎯 Performance Optimization

### API Call Optimization
- Use the appropriate model (gpt-4 is more expensive but more accurate than gpt-3.5)
- Set reasonable call limits
- Cache frequently used results

### Local Optimization
- Ensure sufficient memory
- Use SSD storage
- Close unnecessary background applications

### Network Optimization
- Use a stable network connection
- Consider using CDN acceleration
- Set reasonable timeout values

---

If none of the above solutions resolve your issue, please create a GitHub Issue with detailed error information and system environment details.
