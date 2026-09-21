+++
title = 'YAML 与 TOML 详解'
date = '2026-09-21T12:20:29+08:00'
draft = false
tags = ['html', 'css']
ShowToc = true
description = 'YAML 与 TOML 详解'
+++

> 背景：学习 Hugo 搭建博客时，在文章 front matter 和站点配置 `hugo.toml` 中遇到了 YAML 和 TOML 两种格式。

---

## 一、它们到底是什么

YAML 和 TOML 都是**「数据序列化格式」（serialization format）**——用来把「数据」用有规则、人和机器都能读懂的文本写下来，方便程序读取、也方便人修改。

它们和 Markdown 是同类东西：Markdown 是给「文章」定格式，YAML/TOML 是给「配置数据」定格式。

### 常见数据格式一览

| 格式 | 一眼认出 | 典型用途 |
|------|---------|---------|
| JSON | `{"key": "value"}` | API 接口、前后端传数据 |
| YAML | `key: value` + 缩进 | 配置文件（Docker、K8s、GitHub Actions、Hugo 文章） |
| TOML | `key = "value"` | 配置文件（Rust/Python 项目、Hugo 站点配置） |
| XML | `<tag>value</tag>` | 老牌格式，现在少用 |
| INI | `key=value` | Windows 老式配置 |

---

## 二、YAML 详解

### 核心语法（三件事）

**1. 键值对用冒号**

```yaml
name: anko
age: 25
```

**2. 层级用缩进（空格，不能用 Tab）**

```yaml
person:
  name: anko
  address:
    city: 上海
    street: 某路
```

**3. 列表用短横线 `-`**

```yaml
tags:
  - Hugo
  - Blog
  - 编程
```

### 特点与坑

- 优点：最像「给人看」的格式，符号噪音少，可读性极强。
- 致命坑：**对缩进极其敏感**。多一个/少一个空格都可能导致解析错误，且报错往往不明显。新手最易翻车点。

### 常见使用场景

- Docker Compose（`docker-compose.yml`）
- Kubernetes 部署文件
- **GitHub Actions 工作流**（`.github/workflows/*.yml`）
- Hugo 文章 front matter、CI 配置

---

## 三、TOML 详解

### 核心语法

**1. 键值对用等号**

```toml
title = "My Blog"
baseURL = "https://example.org"
```

**2. 用 `[表头]` 表示分组/层级**

```toml
[params]
  subtitle = "学习笔记"
  author = "anko"
```

**3. 列表用方括号**

```toml
tags = ["Hugo", "Blog"]
```

### 特点与坑

- 优点：规则明确、**不依赖缩进**（靠 `=` 和 `[]` 表达结构），对齐乱了也不影响，不易因空格出错。
- 优点：类型要求严格清晰（字符串加引号、数字不加），适合精确配置。
- 缺点：略啰嗦，符号比 YAML 多。

### 常见使用场景

- Rust 的 `Cargo.toml`、Python 的 `pyproject.toml`
- **Hugo 站点配置**（`hugo.toml`）

---

## 四、YAML vs TOML 对比速查

| 对比项 | YAML | TOML |
|--------|------|------|
| 赋值方式 | 冒号 `key: value` | 等号 `key = "value"` |
| 表达层级 | 靠缩进 | 靠 `[表头]` |
| 列表写法 | `- item` | `["item"]` |
| 可读性 | 最强，像自然语言 | 较严谨，像编程 |
| 最大风险 | 缩进错乱导致解析失败 | 类型不匹配报错 |
| 一句话印象 | 给「人」读的清单 | 给「机器」填的表 |

---

## 五、怎么选

1. 看你要配的工具/框架默认用什么 —— **跟着它的惯例走**。
2. 没有惯例时：追求可读性选 YAML，追求严谨少出错选 TOML。
3. 你的博客：**文章 front matter 用 YAML，站点配置用 TOML**（社区惯例）。

> 记住：它们只是「写配置的文字格式」，学会一种，另一种一看就懂。

---

## 六、另外三种格式：JSON、XML、INI

### JSON —— 现在最主流的数据交换格式

```json
{
  "title": "My Blog",
  "author": "anko",
  "tags": ["Hugo", "Blog"],
  "isPublic": true,
  "views": 1024
}
```

- 用花括号 `{}` 表示对象，方括号 `[]` 表示数组
- **键名必须用双引号**，值也是（数字、布尔值除外）
- 非常严格：**不允许注释、不允许尾随逗号**

**常见场景**：API 接口传数据（前后端通信几乎都是 JSON）、`package.json`、`tsconfig.json`、VS Code 设置、日志。

**一句话印象**：机器和程序之间交换数据的"世界通用语言"，严谨、无废话，但人读起来累。

### INI —— 最古老的"朴实无华"格式

```ini
[blog]
title = My Blog
author = anko

[server]
port = 1313
debug = true
```

- 用 `[区块名]` 分组，下面跟 `键 = 值`
- 极简：只有"区块"和"键值"两层，**无嵌套**
- 值都是字符串，**没有类型概念**

**常见场景**：Windows 的 `.ini` 配置文件、Linux 程序简单配置、游戏存档。

**一句话印象**：爷爷辈的格式，胜在"傻白甜"——一眼就会，但表达不了复杂结构。TOML 可理解为 INI 的"现代化增强版"（TOML 就是受 INI 启发设计的）。

### XML —— 曾经的王者，现在退居幕后

```xml
<blog>
  <title>My Blog</title>
  <author>anko</author>
  <tags>
    <tag>Hugo</tag>
    <tag>Blog</tag>
  </tags>
</blog>
```

- 用成对的标签 `<xxx>...</xxx>` 包裹内容，很像 HTML
- 极其啰嗦：一个简单值也要写"开标签 + 内容 + 闭标签"
- 功能强大：支持属性、注释、命名空间、校验规则（DTD/XSD）

**常见场景**：老系统/企业级系统（银行、政务、传统行业接口）、Android 布局文件、需要严格校验的场合。

**一句话印象**：曾经是"标准答案"，因太啰嗦很多场景被 JSON 取代，但**需要严谨、带属性、可校验**的场景仍不可替代。

---

## 七、五种格式全家福

| 格式 | 语法特征 | 最大特点 | 典型用途 | 记忆口诀 |
|------|---------|---------|---------|---------|
| JSON | `{"key": "value"}` | 最主流、严格、无注释 | API 传数据、package.json | 机器语 |
| YAML | `key: value` 冒号+缩进 | 可读性最强、怕缩进错 | Docker、GitHub Actions | 给人看的清单 |
| TOML | `key = "value"` 等号+表头 | 严谨、不靠缩进 | Cargo.toml、hugo.toml | 给机器填的表 |
| XML | `<tag>值</tag>` 成对标签 | 啰嗦但可校验、带属性 | 企业接口、Android 布局 | 严谨的老贵族 |
| INI | `[区块]` + `key=value` | 最古老、最简单、无类型 | Windows 老式配置 | 傻白甜老祖宗 |

### 历史演进视角

五种格式的出现顺序，讲了一个故事：

1. **INI**（最老）—— 需求简单，够用就行
2. **XML** —— 需求变复杂，要层级、要校验，于是发明了啰嗦但强大的标签语言
3. **JSON** —— XML 太啰嗦，Web 时代需要轻量格式，JSON 上位
4. **YAML** —— JSON 对"人"不友好，于是有了更易读的 YAML
5. **TOML** —— YAML 缩进易出错，于是有了更严谨的 TOML

**核心规律**：没有谁"绝对更好"，每个格式都为解决"上一个格式的痛点"而生，然后在特定场景沉淀下来。

### 新手实用建议

- **现在最需要熟**：JSON 和 YAML（搭博客、碰现代工具绕不开）
- **TOML**：已会（`hugo.toml`）
- **XML**：遇到能认出来即可，新项目很少主动用
- **INI**：知道是"最简单的老古董"即可，几乎不用主动学
