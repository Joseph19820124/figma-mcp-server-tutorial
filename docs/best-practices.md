# Best Practices for Figma MCP Server / Figma MCP 服务器最佳实践

[English](#english) | [中文](#中文)

---

## English

### Security Best Practices

#### 1. Token Management
- **Never commit tokens to version control**
- Use environment variables or secure configuration files
- Rotate tokens regularly (every 90 days recommended)
- Use read-only tokens when possible
- Monitor token usage and revoke unused tokens

#### 2. Access Control
```json
{
  "mcpServers": {
    "figma": {
      "command": "npx",
      "args": ["@modelcontextprotocol/server-figma"],
      "env": {
        "FIGMA_ACCESS_TOKEN": "${FIGMA_TOKEN}",
        "FIGMA_ALLOWED_TEAMS": "team1,team2",
        "FIGMA_MAX_FILE_SIZE": "50MB"
      }
    }
  }
}
```

### Performance Optimization

#### 3. Caching Strategy
```json
{
  "env": {
    "FIGMA_ACCESS_TOKEN": "your_token",
    "FIGMA_CACHE_TTL": "3600",
    "FIGMA_CACHE_SIZE": "100MB",
    "FIGMA_ENABLE_COMPRESSION": "true"
  }
}
```

#### 4. Rate Limiting
- Respect Figma API rate limits (1000 requests/hour)
- Implement exponential backoff for retries
- Batch requests when possible
- Use pagination for large datasets

```json
{
  "env": {
    "FIGMA_RATE_LIMIT": "100",
    "FIGMA_RATE_WINDOW": "3600",
    "FIGMA_MAX_RETRIES": "3",
    "FIGMA_RETRY_DELAY": "1000"
  }
}
```

### File Organization

#### 5. Structured Naming Convention
```
Design Files:
- [Project]-[Component]-[Version].fig
- Example: "EcommApp-Button-v1.2.fig"

Assets:
- [Component]-[State]-[Size].[format]
- Example: "button-primary-large.svg"
```

#### 6. Component Library Structure
```
Components/
├── Atoms/
│   ├── Button/
│   ├── Input/
│   └── Icon/
├── Molecules/
│   ├── Card/
│   ├── Form/
│   └── Navigation/
└── Organisms/
    ├── Header/
    ├── Footer/
    └── ProductGrid/
```

### Development Workflow

#### 7. CI/CD Integration
```yaml
# .github/workflows/figma-sync.yml
name: Sync Figma Assets
on:
  schedule:
    - cron: '0 9 * * 1'  # Every Monday at 9 AM
jobs:
  sync:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Setup Node.js
        uses: actions/setup-node@v3
        with:
          node-version: '18'
      - name: Install Figma MCP
        run: npm install -g @modelcontextprotocol/server-figma
      - name: Sync Assets
        env:
          FIGMA_ACCESS_TOKEN: ${{ secrets.FIGMA_TOKEN }}
        run: |
          # Your sync script here
```

#### 8. Version Control
- Tag design versions in Figma
- Maintain changelog for design updates
- Use semantic versioning for design systems
- Create branches for experimental designs

### Error Handling

#### 9. Graceful Degradation
```json
{
  "env": {
    "FIGMA_ACCESS_TOKEN": "your_token",
    "FIGMA_FALLBACK_MODE": "true",
    "FIGMA_OFFLINE_CACHE": "true",
    "FIGMA_ERROR_REPORTING": "true"
  }
}
```

#### 10. Monitoring and Logging
```json
{
  "env": {
    "FIGMA_ACCESS_TOKEN": "your_token",
    "FIGMA_LOG_LEVEL": "info",
    "FIGMA_METRICS_ENABLED": "true",
    "FIGMA_HEALTH_CHECK": "true"
  }
}
```

---

## 中文

### 安全最佳实践

#### 1. 令牌管理
- **绝不将令牌提交到版本控制系统**
- 使用环境变量或安全配置文件
- 定期轮换令牌（建议每90天）
- 尽可能使用只读令牌
- 监控令牌使用情况并撤销未使用的令牌

#### 2. 访问控制
```json
{
  "mcpServers": {
    "figma": {
      "command": "npx",
      "args": ["@modelcontextprotocol/server-figma"],
      "env": {
        "FIGMA_ACCESS_TOKEN": "${FIGMA_TOKEN}",
        "FIGMA_ALLOWED_TEAMS": "team1,team2",
        "FIGMA_MAX_FILE_SIZE": "50MB"
      }
    }
  }
}
```

### 性能优化

#### 3. 缓存策略
```json
{
  "env": {
    "FIGMA_ACCESS_TOKEN": "your_token",
    "FIGMA_CACHE_TTL": "3600",
    "FIGMA_CACHE_SIZE": "100MB",
    "FIGMA_ENABLE_COMPRESSION": "true"
  }
}
```

#### 4. 速率限制
- 遵守 Figma API 速率限制（1000 请求/小时）
- 实施指数退避重试策略
- 尽可能批量处理请求
- 对大数据集使用分页

```json
{
  "env": {
    "FIGMA_RATE_LIMIT": "100",
    "FIGMA_RATE_WINDOW": "3600",
    "FIGMA_MAX_RETRIES": "3",
    "FIGMA_RETRY_DELAY": "1000"
  }
}
```

### 文件组织

#### 5. 结构化命名约定
```
设计文件：
- [项目]-[组件]-[版本].fig
- 示例："EcommApp-Button-v1.2.fig"

资产：
- [组件]-[状态]-[尺寸].[格式]
- 示例："button-primary-large.svg"
```

#### 6. 组件库结构
```
Components/
├── Atoms/
│   ├── Button/
│   ├── Input/
│   └── Icon/
├── Molecules/
│   ├── Card/
│   ├── Form/
│   └── Navigation/
└── Organisms/
    ├── Header/
    ├── Footer/
    └── ProductGrid/
```

### 开发工作流程

#### 7. CI/CD 集成
```yaml
# .github/workflows/figma-sync.yml
name: 同步 Figma 资产
on:
  schedule:
    - cron: '0 9 * * 1'  # 每周一上午9点
jobs:
  sync:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: 设置 Node.js
        uses: actions/setup-node@v3
        with:
          node-version: '18'
      - name: 安装 Figma MCP
        run: npm install -g @modelcontextprotocol/server-figma
      - name: 同步资产
        env:
          FIGMA_ACCESS_TOKEN: ${{ secrets.FIGMA_TOKEN }}
        run: |
          # 您的同步脚本在这里
```

#### 8. 版本控制
- 在 Figma 中标记设计版本
- 维护设计更新的变更日志
- 为设计系统使用语义版本控制
- 为实验性设计创建分支

### 错误处理

#### 9. 优雅降级
```json
{
  "env": {
    "FIGMA_ACCESS_TOKEN": "your_token",
    "FIGMA_FALLBACK_MODE": "true",
    "FIGMA_OFFLINE_CACHE": "true",
    "FIGMA_ERROR_REPORTING": "true"
  }
}
```

#### 10. 监控和日志记录
```json
{
  "env": {
    "FIGMA_ACCESS_TOKEN": "your_token",
    "FIGMA_LOG_LEVEL": "info",
    "FIGMA_METRICS_ENABLED": "true",
    "FIGMA_HEALTH_CHECK": "true"
  }
}
```

### 团队协作

#### 11. 设计交接流程
1. **设计完成检查清单**
   - 所有组件都已标准化
   - 颜色和字体符合设计系统
   - 交互状态已定义
   - 响应式断点已设置

2. **开发者友好的注释**
   - 使用描述性的图层名称
   - 添加开发注释和规格
   - 标记可重用组件
   - 提供交互说明

#### 12. 设计系统维护
```json
{
  "designSystem": {
    "version": "2.1.0",
    "lastUpdate": "2025-06-09",
    "components": {
      "updated": ["Button", "Input", "Card"],
      "deprecated": ["OldButton"],
      "new": ["Tooltip", "Modal"]
    },
    "tokens": {
      "colors": "Updated primary palette",
      "spacing": "Added new spacing scale",
      "typography": "Updated font weights"
    }
  }
}
```

### 质量保证

#### 13. 自动化检查
- 设计令牌一致性验证
- 组件使用情况审计
- 无障碍性检查
- 品牌指南合规性

#### 14. 性能监控
```bash
# 监控脚本示例
#!/bin/bash
echo "检查 Figma API 状态..."
curl -s https://api.figma.com/v1/me \
  -H "X-Figma-Token: $FIGMA_TOKEN" \
  | jq '.id'

echo "检查 MCP 服务器响应时间..."
time npx @modelcontextprotocol/server-figma --version
```

### 文档化

#### 15. 维护文档
- API 使用文档
- 故障排除指南
- 更新日志
- 最佳实践指南
- 团队使用规范

这些最佳实践将帮助您更有效、更安全地使用 Figma MCP 服务器，并确保与团队的良好协作。
