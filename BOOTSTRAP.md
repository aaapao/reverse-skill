# Full Auto-Configuration Guide (AI Client Only)

> This file works with the root `README.md`. After reading README, AI clients follow this file to complete **all tool installation, environment configuration, and MCP registration**.
>
> **Target machine**: Windows x64
> **Install base directory**: `D:\wangluo` (all tools consolidated here)
> **Python**: 3.14.5 (`C:\Python314`)
> **Node.js**: v24.16.0
> **pnpm**: 11.2.2
> **Last updated**: 2026-05-26

---

## Current Status Overview

| Component | Status | Version | Path |
|-----------|--------|---------|------|
| Java JDK | ✅ | 21.0.11 | `D:\wangluo\jdk-21.0.11+10` |
| Python | ✅ | 3.14.5 | `C:\Python314` |
| Node.js | ✅ | v24.16.0 | `C:\Program Files\nodejs` |
| pnpm | ✅ | 11.2.2 | npm global |
| jadx | ✅ | 1.5.5 | `D:\wangluo\jadx` |
| apktool | ✅ | 3.0.2 | `D:\wangluo\apktool` |
| adb | ✅ | 1.0.41 | `D:\wangluo\platform-tools` |
| apksigner | ✅ | — | `D:\wangluo\bin\apksigner.bat` |
| zipalign | ✅ | — | `D:\wangluo\bin\zipalign.bat` |
| Frida | ✅ | 17.9.10 | `%APPDATA%\Python\Python314\Scripts` |
| radare2 | ✅ | 5.9.8 | `D:\wangluo\r2` |
| nmap | ✅ | 7.80 | `C:\Program Files (x86)\Nmap` |
| agent-browser | ✅ | 0.27.0 | npm global |
| playwright | ✅ | 1.60.0 | npm global |
| Ghidra | ✅ | 12.1 PUBLIC | `D:\wangluo\ghidra_12.1_PUBLIC` |
| GhidraMCP plugin | ✅ | 1.4 | Installed via Ghidra GUI |
| SecLists | ✅ | — | `D:\wangluo\SecLists-master` |
| ProxyCat | ✅ | — | `D:\wangluo\ProxyCat` |
| IDA Pro | ✅ | 9.3 | `D:\idapro` |
| ida-pro-mcp | ✅ | 2.0.0 | pip package |
| BurpSuite Pro | ✅ | 2026.4.2 | `D:\BurpSuite V2026.4.2` |
| BurpSuite MCP Extension | ✅ | 2.0.0 | `burp-mcp-full.jar` (63 tools) |
| Anything Analyzer | ✅ | — | `D:\anthing\Anything Analyzer` |
| jshookmcp | ✅ | latest | via npx |
| Skill Pack | ✅ | — | `D:\reverse-skill-private-main` |
| Claude Global Rules | ✅ | — | `~/.claude/CLAUDE.md` |

> ✅ = Installed & available | ⚠️ = Manual action needed | ❌ = Not installed

---

## Environment Variables

```powershell
# Java
JAVA_HOME = D:\wangluo\jdk-21.0.11+10

# IDA
IDADIR = D:\idapro

# PATH entries (already appended):
# D:\wangluo\jdk-21.0.11+10\bin
# D:\wangluo\bin
# D:\wangluo\platform-tools
# D:\wangluo\jadx\bin
# D:\wangluo\apktool
# D:\wangluo\r2\radare2-5.9.8-w64\bin
# C:\Program Files (x86)\Nmap
# %APPDATA%\Python\Python314\Scripts
```

---

## MCP Registration Summary

```json
{
  "mcpServers": {
    "idapro": {
      "url": "http://127.0.0.1:13337/mcp"
    },
    "anything-analyzer": {
      "url": "http://localhost:23816/mcp"
    },
    "jshook": {
      "command": "npx",
      "args": ["-y", "@jshookmcp/jshook@latest"],
      "env": { "JSHOOK_BASE_PROFILE": "search" }
    },
    "ghidra": {
      "url": "http://localhost:8765/mcp"
    },
    "burpsuite": {
      "command": "node",
      "args": ["D:\\reverse-skill-private-main\\burp-mcp-full\\mcp-bridge.js"]
    }
  }
}
```

---

## Verification Commands

```powershell
java -version
node -v
python --version
frida --version
radare2 -v
adb --version
nmap --version
agent-browser --version
playwright --version
```

---

## Manual Actions Pending

| Step | Status | Note |
|------|--------|------|
| GhidraMCP plugin | ✅ Done | Installed via Ghidra GUI |
| IDA Pro MCP plugin | ✅ Done | `ida-pro-mcp --install` executed, service online (13337) |
| Anything Analyzer | ✅ Done | Desktop app running, MCP on 23816 |
| BurpSuite MCP | ✅ Done | Extension loaded, service on 9876 |
| Claude MCP registration | ⚠️ TODO | Create `~/.claude/mcp.json` with above config |
| Restart terminal | ⚠️ TODO | PATH changes need new terminal to take effect |
