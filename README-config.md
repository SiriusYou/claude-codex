# Claude Code + Codex Configuration Guide

**[中文](README-config-zh.md) | English**

## 📁 Configuration File Selection

### 1. Simple Configuration (Recommended for Beginners)
- **File**: `config-simple.json`
- **Features**: Claude Code + Codex basic collaboration
- **Includes**: Sequential-thinking (deep analysis)
- **Best for**: Quick exploration and basic development

### 2. Standard Configuration (Recommended for Daily Use)
- **File**: `claude-desktop-config.json`
- **Features**: Complete collaborative development environment
- **Includes**: Task management + code indexing
- **Best for**: Everyday development work

### 3. Advanced Configuration (Recommended for Power Users)
- **File**: `config-advanced.json`
- **Features**: Enterprise-grade development environment
- **Includes**: Browser debugging + web search
- **Best for**: Complex projects and advanced development

## 🔧 Configuration Steps

### Step 1: Choose a Configuration File
Select the configuration file that best suits your needs.

### Step 2: Set API Keys
Edit the configuration file and replace the following:
```json
"OPENAI_API_KEY": "your-openai-api-key-here"
```
Replace with your actual OpenAI API key.

Optional configuration:
```json
"EXA_API_KEY": "your-exa-api-key-here"
```
If using the advanced configuration, you can add an Exa search API key.

### Step 3: Copy to the Correct Location
**macOS**:
```bash
cp claude-desktop-config.json ~/Library/Application\ Support/Claude/claude_desktop_config.json
```

**Windows**:
```cmd
copy claude-desktop-config.json %APPDATA%\Claude\claude_desktop_config.json
```

**Linux**:
```bash
cp claude-desktop-config.json ~/.config/claude/claude_desktop_config.json
```

### Step 4: Restart Claude Code
Restart the Claude Code application and the configuration will take effect automatically.

## ✅ Verify Configuration

After restarting, type in Claude Code:
```
/available-tools
```

If you see codex-related tools, the configuration is successful!
