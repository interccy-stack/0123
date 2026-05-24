---
name: zero-one-two-three
description: 知识架构师智能体技能——深度阅读与结构化提取、跨平台知识库连接与碰撞分析(IMA/语雀/飞书/Notion)、AES-256笔记加密与阅后即焚、风格克隆(20+维语言指纹)与语音分身(9种中文音色)、数字分身胶囊部署变现。当用户说"深度读"、"同步知识库"、"锁住笔记"、"克隆我的风格"、"语音朗读"、"知识创生"、"发芽联想"时触发。
license: MIT
compatibility: Python 3.9+, 需要网络访问（模型下载），推荐使用国内镜像加速
allowed-tools: "Bash(python:) Bash(pip:) Read Write Glob Grep"
metadata:
  version: "16.0.0"
  author: C叔 115886@
  category: knowledge-management
  tags:
    - knowledge-extraction
    - knowledge-graph
    - encryption
    - digital-twin
    - voice-clone
    - style-clone
    - langchain
    - faiss
---

# Zero-One-Two-Three 知识架构师

## 概述

Zero-One-Two-Three (0+1+2≠3) 是一个基于第一性原理的知识管理智能体技能，覆盖知识全生命周期：采集→连接→创生→保护→变现。核心方法论：零基建模(0)、极致原子提取(1)、跨平台碰撞连接(2)、涌现创生(≠3)。

## 触发条件

当用户表达以下意图时激活本技能：

| 用户意图 | 触发词示例 |
|---------|-----------|
| 深度阅读与结构化提取 | "深度读一下《XXX》"、"帮我分析这篇文章"、"提取关键信息" |
| 知识库连接与同步 | "同步我的IMA知识库"、"连接语雀/飞书"、"知识碰撞分析" |
| 知识加密保护 | "锁住这份笔记"、"加密这个文件"、"阅后即焚" |
| 风格克隆 | "克隆我的写作风格"、"分析我的文风"、"用我的语气改写" |
| 语音分身 | "用我的声音朗读"、"语音播报这篇笔记"、"生成播客音频" |
| 知识创生 | "找找知识空白"、"生成补全提案"、"知识发芽" |
| 数字分身 | "生成我的数字分身"、"创建AI人格"、"部署到微信小程序" |
| 个人图书馆 | "扫描我的笔记"、"搜索知识库"、"整理知识目录" |

## 前置条件

- Python ≥ 3.9
- 安装依赖：`pip install -r requirements.txt`（或使用清华镜像 `-i https://pypi.tuna.tsinghua.edu.cn/simple`）
- 首次运行需下载嵌入模型（~400MB），国内推荐设置 `HF_ENDPOINT=https://hf-mirror.com` 加速
- 环境变量（按需设置）：
  - `ZOT_MAIL_USER` / `ZOT_MAIL_PASS`：灵感信箱 IMAP/SMTP 邮箱配置
  - `ZOT_AUTHOR_EMAIL`：体验报告接收邮箱
  - `ZOT_IMA_API_KEY`：IMA 知识库 API 密钥

## 工具脚本

### 知识加密 (`knowledge_lock.py`)
```
python knowledge_lock.py lock <文件路径> <密码> [--preview 30]   # AES-256加密，preview=公开试读百分比
python knowledge_lock.py unlock <文件路径> <密码>                 # 解密
python knowledge_lock.py peek <文件路径>                          # 查看加密文件头信息
python knowledge_lock.py recover <文件路径> <12词助记词>           # 助记词恢复
```
密码要求：≥8位，含大小写字母和数字。加密前自动备份。密码丢失不可恢复。

### 阅后即焚 (`ephemeral_share.py`)
生成一次性分享链接，查看后自动销毁。

### 风格克隆 (`style_clone.py`)
```
python style_clone.py analyze <文件夹路径>                          # 分析写作风格，生成20+维语言指纹JSON
python style_clone.py profile <指纹.json> [--html]                 # 查看风格报告（可选HTML可视化输出）
python style_clone.py mimic "待改写内容" --fingerprint <指纹.json>  # 将文本改写成目标风格
```
分析维度：句子长度、标点习惯、表情密度、正式度、词汇多样性、人称偏好、节奏感、人格标签等。

### 语音分身 (`voice_clone.py`)
```
python voice_clone.py list                                         # 列出9种中文音色
python voice_clone.py speak "文本"                                  # 文本转语音
python voice_clone.py speak-style "文本" --fingerprint <指纹.json>  # 风格指纹自动匹配音色+语速+音调
python voice_clone.py narrate <文件.md> [--fingerprint <指纹.json>] # 用风格匹配声音朗读文件
```
基于 Microsoft Edge TTS，免费无需 API Key。支持温柔女声、沉稳男声、新闻播报、方言等。

### 灵感信箱 (`mailbox_tool.py`)
```
python mailbox_tool.py --config           # AI引导配置邮箱（IMAP/SMTP）
python mailbox_tool.py --watch            # 启动收件箱监听，自动解析邮件
python mailbox_tool.py --report           # 发送体验报告
```

### 个人图书馆 (`personal_library.py`)
```
python personal_library.py --scan <目录>          # 扫描Markdown笔记并编目入库
python personal_library.py --browse               # 浏览书架
python personal_library.py --search "关键词"       # 全文检索
python personal_library.py --read "标题" --status done   # 标记阅读状态
```

### 系统入口 (`main.py`)
```
python main.py    # 启动系统，加载核心引擎与扩展工具
```

## 典型工作流

### 流程 1：深度阅读提取
```
用户："帮我深度读一下《生酮饮食入门》"
→ 读取文件 → 10维度结构化提取（目录/机制/数据/证据等级等）
→ 输出结构化 Markdown 笔记
```

### 流程 2：跨平台知识碰撞
```
用户："同步我的 IMA 知识库，找找生酮相关的知识空白"
→ 连接多平台数据源 → 向量化存储(FAISS) → TF-IDF碰撞检测
→ 知识图谱分析(NetworkX) → 生命力评分 → 空白探测
→ 生成补全提案 → 用户审批 → 执行补全入库
```

### 流程 3：风格克隆 + 语音输出
```
python style_clone.py analyze ./我的笔记
python style_clone.py profile style_fingerprint.json --html
python voice_clone.py narrate 文章.md --fingerprint style_fingerprint.json
```

### 流程 4：加密保护与分享
```
python knowledge_lock.py lock 核心笔记.md MyP@ss123 --preview 30
# 输出：核心笔记.md.locked（公开试读前30% + 核心70%加密）
# 复制 .locked 文件分享，对方需密码解锁
```

## 限制与边界

- 默认 CPU 模式运行 MiniLM 小模型，大模型推理需自行部署
- 仅连接用户已有权限的数据源，不绕过付费墙
- AES-256 加密无后门，密码丢失则文件永久不可读
- 纯命令行工具模式，不提供 Web GUI
- 内容生成需人工复核后再入库，本技能作为"提案者"而非"裁决者"