# Figma MCP Server Tutorial / Figma MCP 服务器教程

[English](#english) | [中文](#中文)

> Complete tutorial for Figma MCP Server Community Edition  
> 完整的 Figma MCP 服务器社区版使用教程

---

## 📚 Table of Contents / 目录

- [Quick Start / 快速开始](#quick-start--快速开始)
- [Detailed Documentation / 详细文档](#detailed-documentation--详细文档)
- [Examples / 示例](#examples--示例)
- [Configuration / 配置](#configuration--配置)
- [Troubleshooting / 故障排除](#troubleshooting--故障排除)

---

## English

### What is Figma MCP Server?

The Figma MCP (Model Context Protocol) Server is a community-built server that enables AI assistants like Claude to interact with Figma design files. It allows you to:

- 🎨 Extract design data from Figma files
- 📱 Download images and assets
- 🔍 Analyze design components
- 💻 Generate code from designs
- ⚡ Automate design workflows

### Quick Start / 快速开始

#### Prerequisites

Before setting up the Figma MCP Server, ensure you have:

1. **Node.js** (v18 or higher)
2. **npm** or **yarn** package manager
3. **Figma Personal Access Token**
4. **Claude Desktop** application

#### Installation Steps

1. **Install the Figma MCP Server**
```bash
npm install -g @modelcontextprotocol/server-figma
```

2. **Get Your Figma Access Token**
   - Go to [Figma Settings](https://www.figma.com/settings)
   - Create a new personal access token
   - Copy and save the token securely

3. **Configure Claude Desktop**
   - Edit your Claude Desktop configuration file
   - Add the Figma MCP server configuration
   - Use the provided [configuration templates](config/)

4. **Restart Claude Desktop**
   - Close and restart Claude Desktop
   - Test the integration with a Figma URL

### Detailed Documentation / 详细文档

📖 **[Best Practices Guide](docs/best-practices.md)**
- Security best practices
- Performance optimization
- File organization
- Development workflow

🔧 **[Troubleshooting Guide](docs/troubleshooting.md)**
- Common issues and solutions
- Debug mode instructions
- Performance optimization
- Contact support

### Examples / 示例

💡 **[Example Prompts](examples/prompts.md)**
- Design analysis prompts
- Code generation examples
- Asset management workflows
- Advanced use cases

### Configuration / 配置

⚙️ **Configuration Files:**
- [Basic Configuration](config/claude-desktop-config.json) - Simple setup
- [Advanced Configuration](config/claude-desktop-config-advanced.json) - With proxy and timeout settings

#### Basic Configuration Example
```json
{
  "mcpServers": {
    "figma": {
      "command": "npx",
      "args": ["@modelcontextprotocol/server-figma"],
      "env": {
        "FIGMA_ACCESS_TOKEN": "YOUR_FIGMA_TOKEN_HERE"
      }
    }
  }
}
```

### Available Commands

The Figma MCP Server provides these tools:

1. **get_figma_data** - Fetch design data from Figma files
2. **download_figma_images** - Download images and assets

### Example Usage

```
User: "Please analyze this Figma file: https://www.figma.com/design/abc123/My-Design"

Claude will:
1. Connect to Figma using the MCP server
2. Extract design information
3. Provide analysis of components, colors, typography, etc.
```

---

## 中文

### 什么是 Figma MCP 服务器？

Figma MCP（模型上下文协议）服务器是一个社区构建的服务器，它使 Claude 等 AI 助手能够与 Figma 设计文件进行交互。它允许您：

- 🎨 从 Figma 文件中提取设计数据
- 📱 下载图像和资源
- 🔍 分析设计组件
- 💻 从设计生成代码
- ⚡ 自动化设计工作流程

### 快速开始

#### 前置要求

在设置 Figma MCP 服务器之前，请确保您具备：

1. **Node.js**（v18 或更高版本）
2. **npm** 或 **yarn** 包管理器
3. **Figma 个人访问令牌**
4. **Claude Desktop** 应用程序

#### 安装步骤

1. **安装 Figma MCP 服务器**
```bash
npm install -g @modelcontextprotocol/server-figma
```

2. **获取您的 Figma 访问令牌**
   - 前往 [Figma 设置页面](https://www.figma.com/settings)
   - 创建新的个人访问令牌
   - 复制并安全保存令牌

3. **配置 Claude Desktop**
   - 编辑您的 Claude Desktop 配置文件
   - 添加 Figma MCP 服务器配置
   - 使用提供的[配置模板](config/)

4. **重启 Claude Desktop**
   - 关闭并重启 Claude Desktop
   - 使用 Figma URL 测试集成

### 详细文档

📖 **[最佳实践指南](docs/best-practices.md)**
- 安全最佳实践
- 性能优化
- 文件组织
- 开发工作流程

🔧 **[故障排除指南](docs/troubleshooting.md)**
- 常见问题和解决方案
- 调试模式说明
- 性能优化
- 联系支持

### 示例

💡 **[示例提示](examples/prompts.md)**
- 设计分析提示
- 代码生成示例
- 资产管理工作流程
- 高级用例

### 配置

⚙️ **配置文件：**
- [基础配置](config/claude-desktop-config.json) - 简单设置
- [高级配置](config/claude-desktop-config-advanced.json) - 包含代理和超时设置

#### 基础配置示例
```json
{
  "mcpServers": {
    "figma": {
      "command": "npx",
      "args": ["@modelcontextprotocol/server-figma"],
      "env": {
        "FIGMA_ACCESS_TOKEN": "在此处填入您的_FIGMA_令牌"
      }
    }
  }
}
```

### 可用命令

Figma MCP 服务器提供以下工具：

1. **get_figma_data** - 从 Figma 文件获取设计数据
2. **download_figma_images** - 下载图像和资源

### 使用示例

```
用户："请分析这个 Figma 文件：https://www.figma.com/design/abc123/My-Design"

Claude 将：
1. 使用 MCP 服务器连接到 Figma
2. 提取设计信息
3. 提供组件、颜色、排版等分析
```

---

## 🚀 Advanced Features / 高级功能

### Batch Processing / 批量处理
- Process multiple Figma files simultaneously
- Export assets in batch
- Generate design tokens for entire design systems

### CI/CD Integration / CI/CD 集成
- Automate design asset sync
- Version control for design files
- Continuous deployment of design updates

### Team Collaboration / 团队协作
- Shared configuration templates
- Design handoff automation
- Cross-platform asset generation

---

## 📁 Project Structure / 项目结构

```
figma-mcp-server-tutorial/
├── README.md                          # Main tutorial (this file)
├── config/                           # Configuration templates
│   ├── claude-desktop-config.json    # Basic configuration
│   └── claude-desktop-config-advanced.json # Advanced configuration
├── docs/                             # Detailed documentation
│   ├── best-practices.md             # Best practices guide
│   └── troubleshooting.md            # Troubleshooting guide
└── examples/                         # Example usage
    └── prompts.md                    # Example prompts and use cases
```

---

## 🤝 Contributing / 贡献

We welcome contributions! Please feel free to:
- Submit issues for bugs or feature requests
- Create pull requests for improvements
- Add more example prompts and use cases
- Translate documentation to other languages

欢迎贡献！请随时：
- 提交错误或功能请求的问题
- 创建改进的拉取请求
- 添加更多示例提示和用例
- 将文档翻译成其他语言

---

## 📄 License / 许可证

This tutorial is released under the MIT License.
本教程基于 MIT 许可证发布。

---

## 🔗 Related Links / 相关链接

- [Figma API Documentation](https://www.figma.com/developers/api)
- [MCP Official Documentation](https://modelcontextprotocol.io/)
- [Claude Desktop](https://claude.ai/download)
- [Figma Community](https://www.figma.com/community)

---

## ⭐ Show Your Support / 表示支持

If this tutorial helped you, please consider:
- Starring this repository ⭐
- Sharing it with your team
- Contributing improvements

如果这个教程对您有帮助，请考虑：
- 为此仓库加星 ⭐
- 与您的团队分享
- 贡献改进

---

**Happy designing with AI! 🎨✨**  
**与 AI 愉快设计！🎨✨**
