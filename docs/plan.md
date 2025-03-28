# Kindle2Anki 项目规划

## 项目概述

Kindle2Anki 是一个网络应用，旨在帮助用户将电子书阅读笔记转换为高质量的 Anki 记忆卡片。通过智能处理和整合用户的阅读笔记，生成更有效的学习材料。

## 核心功能

### 1. 文件上传和解析
- 支持多种电子书格式（epub/mobi/pdf）的上传和解析
- 支持 Kindle 笔记导出文件的上传和解析
- 文件格式验证和错误处理

### 2. 内容提取和匹配
- 从电子书中提取文本内容
- 从笔记文件中提取标注内容和章节信息
- 建立电子书内容和笔记之间的对应关系
- 处理跨段落标注的情况

### 3. 笔记优化
- 合并相邻或重复的笔记
- 根据上下文补充必要的信息
- 精简冗长的笔记内容
- 智能分割过长的笔记

### 4. Anki 卡片生成
- 将优化后的笔记转换为 Anki 卡片格式
- 支持多种卡片模板
- 自动生成问答对
- 添加相关上下文信息
- 导出为 Anki 可导入的格式

## 技术架构

### 前端 (Next.js)
- TypeScript 作为开发语言
- 使用 Next.js 13+ App Router
- 文件上传组件 (使用 uppy 或 react-dropzone)
- 笔记预览和编辑界面
- 卡片预览功能
- Tailwind CSS 用于样式设计
- 响应式设计

### 后端 (FastAPI)
- Python 3.11+
- FastAPI 框架
- 异步处理
- WebSocket 支持（用于长时间运行的任务）
- 文件处理服务
  - PyMuPDF (用于 PDF)
  - EbookLib (用于 EPUB)
  - Mobi (用于 Kindle 格式)
- 文本分析和处理
  - NLTK/SpaCy 用于 NLP
  - Pandas 用于数据处理
  - LLM (如 OpenAI API 或 Hugging Face 模型) 用于智能内容处理和优化
- API 接口
  - RESTful API
  - OpenAPI/Swagger 文档
- 后台任务队列 (Celery)

### 数据存储
- PostgreSQL
  - 用户数据
  - 电子书元数据
  - 笔记数据
  - 生成的卡片数据
- Redis
  - 缓存
  - 会话管理
  - 任务队列
- MinIO/S3
  - 文件存储

## 开发路线图

### 第一阶段：基础功能
1. 搭建项目框架
   - 设置 FastAPI 项目结构
   - 配置 Next.js 项目
   - 设置数据库和存储服务
2. 实现文件上传功能
   - 前端上传界面
   - 后端文件处理
3. 开发基本的文件解析功能
   - PDF 解析
   - Kindle 笔记解析
4. 实现简单的笔记提取

### 第二阶段：核心功能
1. 开发内容匹配算法
2. 实现笔记优化功能
3. 开发 Anki 卡片生成功能
4. 添加基本的用户界面

### 第三阶段：优化和扩展
1. 改进用户界面和体验
2. 优化处理算法
3. 添加更多电子书格式支持
4. 实现高级卡片模板

## 技术难点

1. 不同格式电子书的解析
   - PDF 布局分析
   - EPUB 结构提取
   - Mobi 格式处理
2. 笔记与原文的精确匹配
   - 文本相似度算法
   - 上下文分析
3. 智能分割和合并笔记
   - NLP 处理
   - 语义分析
4. 生成高质量的问答对
5. 处理大文件的性能优化
   - 流式处理
   - 异步操作
   - 分块处理

## 后续功能规划

1. 用户账户系统
2. 笔记分享功能
3. 自定义卡片模板
4. 批量处理功能
5. 导出数据备份
6. 社区功能（分享笔记和卡片）

## 注意事项

1. 版权问题处理
2. 用户数据安全
3. 系统性能优化
4. 错误处理机制
5. 用户隐私保护

## 开发环境设置

1. 使用 Docker Compose 配置开发环境
2. 使用 Cursor IDE 作为开发工具
3. 配置对应的 .cursorrules, .cursorignore 文件