# Figma MCP Server Tutorial / Figma MCP 服务器教程

[English](#english) | [中文](#中文)

---

## English

### What is Figma MCP Server?

The Figma MCP (Model Context Protocol) Server is a community-built server that enables AI assistants like Claude to interact with Figma design files. It allows you to:

- Extract design data from Figma files
- Download images and assets
- Analyze design components
- Generate code from designs
- Automate design workflows

### Prerequisites

Before setting up the Figma MCP Server, ensure you have:

1. **Node.js** (v18 or higher)
2. **npm** or **yarn** package manager
3. **Figma Personal Access Token**
4. **Claude Desktop** application

### Step 1: Install the Figma MCP Server

```bash
# Install globally using npm
npm install -g @modelcontextprotocol/server-figma

# Or install using yarn
yarn global add @modelcontextprotocol/server-figma
```

### Step 2: Get Your Figma Access Token

1. Go to [Figma Settings](https://www.figma.com/settings)
2. Scroll down to "Personal access tokens"
3. Click "Create new token"
4. Give it a name (e.g., "MCP Server")
5. Copy the generated token (keep it secure!)

### Step 3: Configure Claude Desktop

Edit your Claude Desktop configuration file:

**Windows:** `%APPDATA%\Claude\claude_desktop_config.json`
**macOS:** `~/Library/Application Support/Claude/claude_desktop_config.json`

Add the following configuration:

```json
{
  "mcpServers": {
    "figma": {
      "command": "npx",
      "args": [
        "@modelcontextprotocol/server-figma"
      ],
      "env": {
        "FIGMA_ACCESS_TOKEN": "YOUR_FIGMA_TOKEN_HERE"
      }
    }
  }
}
```

### Step 4: Restart Claude Desktop

Close and restart Claude Desktop to load the new configuration.

### Step 5: Test the Integration

In Claude, try asking:
- "Can you analyze the Figma file at [figma-url]?"
- "Extract the colors from this Figma design"
- "Download the icons from this Figma file"

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

### Troubleshooting

**Common Issues:**

1. **Token Error:** Ensure your Figma token is valid and has proper permissions
2. **Connection Failed:** Check your internet connection and Figma status
3. **File Access:** Make sure the Figma file is accessible with your token

---

## 中文

### 什么是 Figma MCP 服务器？

Figma MCP（模型上下文协议）服务器是一个社区构建的服务器，它使 Claude 等 AI 助手能够与 Figma 设计文件进行交互。它允许您：

- 从 Figma 文件中提取设计数据
- 下载图像和资源
- 分析设计组件
- 从设计生成代码
- 自动化设计工作流程

### 前置要求

在设置 Figma MCP 服务器之前，请确保您具备：

1. **Node.js**（v18 或更高版本）
2. **npm** 或 **yarn** 包管理器
3. **Figma 个人访问令牌**
4. **Claude Desktop** 应用程序

### 步骤 1：安装 Figma MCP 服务器

```bash
# 使用 npm 全局安装
npm install -g @modelcontextprotocol/server-figma

# 或者使用 yarn 安装
yarn global add @modelcontextprotocol/server-figma
```

### 步骤 2：获取您的 Figma 访问令牌

1. 前往 [Figma 设置页面](https://www.figma.com/settings)
2. 向下滚动到"个人访问令牌"部分
3. 点击"创建新令牌"
4. 给它一个名称（例如"MCP 服务器"）
5. 复制生成的令牌（请妥善保管！）

### 步骤 3：配置 Claude Desktop

编辑您的 Claude Desktop 配置文件：

**Windows:** `%APPDATA%\Claude\claude_desktop_config.json`
**macOS:** `~/Library/Application Support/Claude/claude_desktop_config.json`

添加以下配置：

```json
{
  "mcpServers": {
    "figma": {
      "command": "npx",
      "args": [
        "@modelcontextprotocol/server-figma"
      ],
      "env": {
        "FIGMA_ACCESS_TOKEN": "在此处填入您的_FIGMA_令牌"
      }
    }
  }
}
```

### 步骤 4：重启 Claude Desktop

关闭并重启 Claude Desktop 以加载新配置。

### 步骤 5：测试集成

在 Claude 中，尝试询问：
- "您能分析这个 Figma 文件吗：[figma-url]？"
- "从这个 Figma 设计中提取颜色"
- "从这个 Figma 文件下载图标"

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

### 故障排除

**常见问题：**

1. **令牌错误：** 确保您的 Figma 令牌有效且具有适当权限
2. **连接失败：** 检查您的网络连接和 Figma 状态
3. **文件访问：** 确保使用您的令牌可以访问 Figma 文件

### 高级用法

#### 批量处理

```json
{
  "mcpServers": {
    "figma": {
      "command": "npx",
      "args": [
        "@modelcontextprotocol/server-figma"
      ],
      "env": {
        "FIGMA_ACCESS_TOKEN": "你的令牌",
        "FIGMA_TIMEOUT": "30000"
      }
    }
  }
}
```

#### 代理设置

如果您在公司网络环境中：

```json
{
  "mcpServers": {
    "figma": {
      "command": "npx",
      "args": [
        "@modelcontextprotocol/server-figma"
      ],
      "env": {
        "FIGMA_ACCESS_TOKEN": "你的令牌",
        "HTTP_PROXY": "http://proxy.company.com:8080",
        "HTTPS_PROXY": "http://proxy.company.com:8080"
      }
    }
  }
}
```

## 许可证

本教程基于 MIT 许可证发布。

## 贡献

欢迎提交问题和拉取请求！

## 相关链接

- [Figma API 文档](https://www.figma.com/developers/api)
- [MCP 官方文档](https://modelcontextprotocol.io/)
- [Claude Desktop](https://claude.ai/download)
