# Example Prompts for Figma MCP Server / Figma MCP 服务器示例提示

[English](#english) | [中文](#中文)

---

## English

### Basic Analysis Prompts

#### 1. Design System Analysis
```
Analyze this Figma file and extract all design tokens including:
- Colors (with hex codes)
- Typography (fonts, sizes, weights)
- Spacing values
- Border radius values
- Shadow styles

Figma URL: https://www.figma.com/design/[your-file-id]/Design-System
```

#### 2. Component Inventory
```
Please examine this Figma file and create an inventory of all components:
- List all component names
- Describe their variations and states
- Identify the main component vs instances
- Note any missing states or variants

Figma URL: https://www.figma.com/design/[your-file-id]/Component-Library
```

#### 3. Icon Extraction
```
From this Figma file, please:
1. Identify all icon components
2. Download them as SVG files
3. Organize them by category
4. Provide usage recommendations

Figma URL: https://www.figma.com/design/[your-file-id]/Icon-Set
```

### Code Generation Prompts

#### 4. React Component Generation
```
Based on this Figma design, generate React components with:
- TypeScript definitions
- Styled-components for styling
- Props interface for customization
- Storybook stories for documentation

Figma URL: https://www.figma.com/design/[your-file-id]/Button-Component
```

#### 5. CSS Generation
```
Convert this Figma design to CSS:
- Use CSS Grid for layout
- Include responsive breakpoints
- Extract all color variables
- Add hover and focus states

Figma URL: https://www.figma.com/design/[your-file-id]/Landing-Page
```

#### 6. Tailwind CSS Classes
```
Analyze this Figma design and provide equivalent Tailwind CSS classes:
- Layout utilities
- Color classes
- Typography utilities
- Spacing classes

Figma URL: https://www.figma.com/design/[your-file-id]/Card-Component
```

### Design Review Prompts

#### 7. Accessibility Audit
```
Review this Figma design for accessibility issues:
- Color contrast ratios
- Text readability
- Touch target sizes
- Focus states
- Alternative text needs

Figma URL: https://www.figma.com/design/[your-file-id]/Mobile-App
```

#### 8. Consistency Check
```
Compare these Figma designs and identify inconsistencies:
- Color usage variations
- Typography inconsistencies
- Spacing irregularities
- Component usage differences

Figma URLs:
- Page 1: https://www.figma.com/design/[file-1]/Home
- Page 2: https://www.figma.com/design/[file-2]/About
```

### Asset Management Prompts

#### 9. Image Optimization
```
From this Figma file, download all images and:
- Optimize them for web use
- Provide multiple formats (WebP, PNG, JPG)
- Generate different sizes for responsive design
- Create a manifest file with metadata

Figma URL: https://www.figma.com/design/[your-file-id]/Image-Gallery
```

#### 10. Export for Development
```
Prepare this Figma design for development handoff:
- Export all assets in required formats
- Document spacing and measurements
- List all fonts and weights used
- Provide interaction specifications

Figma URL: https://www.figma.com/design/[your-file-id]/Product-Page
```

---

## 中文

### 基础分析提示

#### 1. 设计系统分析
```
分析这个 Figma 文件并提取所有设计令牌，包括：
- 颜色（附十六进制代码）
- 排版（字体、大小、字重）
- 间距值
- 边框圆角值
- 阴影样式

Figma URL: https://www.figma.com/design/[your-file-id]/Design-System
```

#### 2. 组件清单
```
请检查这个 Figma 文件并创建所有组件的清单：
- 列出所有组件名称
- 描述它们的变体和状态
- 识别主组件与实例
- 注意任何缺失的状态或变体

Figma URL: https://www.figma.com/design/[your-file-id]/Component-Library
```

#### 3. 图标提取
```
从这个 Figma 文件中，请：
1. 识别所有图标组件
2. 将它们下载为 SVG 文件
3. 按类别组织它们
4. 提供使用建议

Figma URL: https://www.figma.com/design/[your-file-id]/Icon-Set
```

### 代码生成提示

#### 4. React 组件生成
```
基于这个 Figma 设计，生成包含以下内容的 React 组件：
- TypeScript 定义
- 用于样式的 Styled-components
- 用于自定义的 Props 接口
- 用于文档的 Storybook 故事

Figma URL: https://www.figma.com/design/[your-file-id]/Button-Component
```

#### 5. CSS 生成
```
将这个 Figma 设计转换为 CSS：
- 使用 CSS Grid 进行布局
- 包含响应式断点
- 提取所有颜色变量
- 添加悬停和焦点状态

Figma URL: https://www.figma.com/design/[your-file-id]/Landing-Page
```

#### 6. Tailwind CSS 类
```
分析这个 Figma 设计并提供等效的 Tailwind CSS 类：
- 布局工具类
- 颜色类
- 排版工具类
- 间距类

Figma URL: https://www.figma.com/design/[your-file-id]/Card-Component
```

### 设计审查提示

#### 7. 无障碍审计
```
审查这个 Figma 设计的无障碍问题：
- 颜色对比度
- 文本可读性
- 触摸目标大小
- 焦点状态
- 替代文本需求

Figma URL: https://www.figma.com/design/[your-file-id]/Mobile-App
```

#### 8. 一致性检查
```
比较这些 Figma 设计并识别不一致之处：
- 颜色使用变化
- 排版不一致
- 间距不规律
- 组件使用差异

Figma URLs:
- 页面 1: https://www.figma.com/design/[file-1]/Home
- 页面 2: https://www.figma.com/design/[file-2]/About
```

### 资产管理提示

#### 9. 图像优化
```
从这个 Figma 文件下载所有图像并：
- 为网络使用优化它们
- 提供多种格式（WebP、PNG、JPG）
- 为响应式设计生成不同尺寸
- 创建包含元数据的清单文件

Figma URL: https://www.figma.com/design/[your-file-id]/Image-Gallery
```

#### 10. 开发交接导出
```
为开发交接准备这个 Figma 设计：
- 以所需格式导出所有资产
- 记录间距和测量值
- 列出所有使用的字体和字重
- 提供交互规格说明

Figma URL: https://www.figma.com/design/[your-file-id]/Product-Page
```

### 高级用例

#### 11. 设计令牌生成
```
从这个设计系统 Figma 文件生成设计令牌：
- JSON 格式的令牌文件
- CSS 自定义属性
- SCSS 变量
- JavaScript 对象
- 为不同平台（iOS、Android、Web）格式化

Figma URL: https://www.figma.com/design/[your-file-id]/Design-Tokens
```

#### 12. 原型分析
```
分析这个 Figma 原型并文档化：
- 所有交互流程
- 转场动画规格
- 用户路径映射
- 状态变化
- 微交互细节

Figma URL: https://www.figma.com/proto/[your-file-id]/User-Flow
```

#### 13. 多平台适配
```
基于这个 Figma 设计，提供多平台实现建议：
- Web（React/Vue/Angular）
- iOS（SwiftUI）
- Android（Jetpack Compose）
- Flutter
- React Native

注意各平台的设计规范差异和最佳实践。

Figma URL: https://www.figma.com/design/[your-file-id]/Cross-Platform-App
```
