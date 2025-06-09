# Figma MCP Server Troubleshooting Guide / 故障排除指南

[English](#english) | [中文](#中文)

---

## English

### Common Issues and Solutions

#### 1. "Token Error" or "Authentication Failed"

**Problem:** The Figma access token is invalid or expired.

**Solutions:**
- Verify your token at [Figma Settings](https://www.figma.com/settings)
- Regenerate a new token if needed
- Ensure there are no extra spaces in your config file
- Check that the token has proper permissions

#### 2. "Command not found: npx"

**Problem:** Node.js is not installed or not in PATH.

**Solutions:**
```bash
# Install Node.js from https://nodejs.org/
# Or using a package manager:

# macOS (using Homebrew)
brew install node

# Ubuntu/Debian
sudo apt install nodejs npm

# Windows (using Chocolatey)
choco install nodejs
```

#### 3. "Module not found" Error

**Problem:** The Figma MCP server package is not installed.

**Solutions:**
```bash
# Install globally
npm install -g @modelcontextprotocol/server-figma

# Or check if it's installed
npm list -g @modelcontextprotocol/server-figma
```

#### 4. "Connection timeout" Error

**Problem:** Network issues or slow response from Figma API.

**Solutions:**
- Increase timeout in configuration:
```json
{
  "env": {
    "FIGMA_ACCESS_TOKEN": "your_token",
    "FIGMA_TIMEOUT": "60000"
  }
}
```
- Check your internet connection
- Try again during off-peak hours

#### 5. "Permission denied" for Figma file

**Problem:** The token doesn't have access to the specific file.

**Solutions:**
- Make sure the file is public or shared with your account
- Check if you're the owner or have appropriate permissions
- Try with a file you created yourself

#### 6. Claude Desktop not recognizing MCP server

**Problem:** Configuration file is not in the correct location or format.

**Solutions:**
- Verify config file location:
  - **Windows:** `%APPDATA%\Claude\claude_desktop_config.json`
  - **macOS:** `~/Library/Application Support/Claude/claude_desktop_config.json`
- Validate JSON syntax using [JSONLint](https://jsonlint.com/)
- Restart Claude Desktop completely

### Debug Mode

To enable debug logging, add this to your environment:

```json
{
  "env": {
    "FIGMA_ACCESS_TOKEN": "your_token",
    "DEBUG": "figma:*"
  }
}
```

### Testing Your Setup

1. **Test Token Directly:**
```bash
curl -H "X-Figma-Token: YOUR_TOKEN" https://api.figma.com/v1/me
```

2. **Test MCP Server:**
```bash
npx @modelcontextprotocol/server-figma
```

---

## 中文

### 常见问题和解决方案

#### 1. "令牌错误" 或 "身份验证失败"

**问题：** Figma 访问令牌无效或已过期。

**解决方案：**
- 在 [Figma 设置](https://www.figma.com/settings) 页面验证您的令牌
- 如有需要，重新生成新令牌
- 确保配置文件中没有额外的空格
- 检查令牌是否具有适当的权限

#### 2. "找不到命令：npx"

**问题：** Node.js 未安装或不在 PATH 中。

**解决方案：**
```bash
# 从 https://nodejs.org/ 安装 Node.js
# 或使用包管理器：

# macOS（使用 Homebrew）
brew install node

# Ubuntu/Debian
sudo apt install nodejs npm

# Windows（使用 Chocolatey）
choco install nodejs
```

#### 3. "找不到模块" 错误

**问题：** Figma MCP 服务器包未安装。

**解决方案：**
```bash
# 全局安装
npm install -g @modelcontextprotocol/server-figma

# 或检查是否已安装
npm list -g @modelcontextprotocol/server-figma
```

#### 4. "连接超时" 错误

**问题：** 网络问题或 Figma API 响应缓慢。

**解决方案：**
- 在配置中增加超时时间：
```json
{
  "env": {
    "FIGMA_ACCESS_TOKEN": "your_token",
    "FIGMA_TIMEOUT": "60000"
  }
}
```
- 检查您的网络连接
- 在非高峰时段重试

#### 5. Figma 文件 "权限被拒绝"

**问题：** 令牌无法访问特定文件。

**解决方案：**
- 确保文件是公开的或与您的账户共享
- 检查您是否是所有者或具有适当权限
- 尝试使用您自己创建的文件

#### 6. Claude Desktop 无法识别 MCP 服务器

**问题：** 配置文件位置不正确或格式有误。

**解决方案：**
- 验证配置文件位置：
  - **Windows:** `%APPDATA%\Claude\claude_desktop_config.json`
  - **macOS:** `~/Library/Application Support/Claude/claude_desktop_config.json`
- 使用 [JSONLint](https://jsonlint.com/) 验证 JSON 语法
- 完全重启 Claude Desktop

### 调试模式

要启用调试日志记录，请将以下内容添加到您的环境中：

```json
{
  "env": {
    "FIGMA_ACCESS_TOKEN": "your_token",
    "DEBUG": "figma:*"
  }
}
```

### 测试您的设置

1. **直接测试令牌：**
```bash
curl -H "X-Figma-Token: YOUR_TOKEN" https://api.figma.com/v1/me
```

2. **测试 MCP 服务器：**
```bash
npx @modelcontextprotocol/server-figma
```

### 性能优化

#### 减少 API 调用

```json
{
  "env": {
    "FIGMA_ACCESS_TOKEN": "your_token",
    "FIGMA_CACHE_TTL": "3600",
    "FIGMA_MAX_RETRIES": "3"
  }
}
```

#### 网络配置

如果您在企业网络中，可能需要配置代理：

```json
{
  "env": {
    "FIGMA_ACCESS_TOKEN": "your_token",
    "HTTP_PROXY": "http://proxy.company.com:8080",
    "HTTPS_PROXY": "http://proxy.company.com:8080",
    "NO_PROXY": "localhost,127.0.0.1"
  }
}
```

### 联系支持

如果问题持续存在：

1. 检查 [Figma API 状态](https://status.figma.com/)
2. 查看 [MCP 官方文档](https://modelcontextprotocol.io/)
3. 在 GitHub 上提交问题报告
