+++
title = 'Morphology: Exponence'
date = '2026-10-09T13:13:00+08:00'
draft = false
tags = ['morphology', 'linguistics']
ShowToc = true
description = 'What is Morphology §6.1.1'
+++
> 来源：*What is Morphology*（Mark Aronoff & Kirsten Fudeman），第六章 Inflection，§6.1.1
> 
> 定位：本节是理解「屈折 vs 派生」「屈折类型清单」「syncretism」的理论地基。

---

## 1. 核心术语：Exponence

- **Exponence**（Peter Matthews 造词）：指「形态句法特征（morphosyntactic features）通过屈折被**实现**出来」这件事。
- **Exponent（承载项 / 体现项）**：用来实现某个特征的那个具体形式。

| 词形 | 形式 | 承载的特征 |
| --- | --- | --- |
| `seas` | `[z]` | 复数（plural） |
| `sailed` | `[d]` | 过去时 / 过去分词（past tense / past participle） |

上面两个例子都是「一个形式 ↔ 一个特征」的一一对应，Matthews 称之为 **simple exponence（简单承载）**。

一旦超出简单对应，就进入现代形态学理论的核心地带。

---

## 2. 三种「升级版」exponence 总览

| 类型 | 关系方向 | 一句话概括 |
| --- | --- | --- |
| **cumulative exponence**（累积承载） | 多个特征 → 一个形式 | 一个词素「一次打包」好几个特征 |
| **portmanteau**（混成 / 并合） | 多个（原本独立的）词 → 一个词 | 两个词「融合」成一个 |
| **extended exponence**（扩展承载） | 一个特征 → 多个形式 | 一个特征「同时散落」在好几个位置 |

---

## 3. 累积承载（cumulative exponence）

**定义**：不止一个形态句法特征，映射到同一个形式上。

### 例子 A：拉丁语动词

```
cant-ō
sing-1sg.pres.ind.act
‘我唱’
```

词尾 `-ō` 这一个词素，同时打包了 **五个** 特征：

```
人称(person) + 数(number) + 时态(tense) + 语气(mood) + 语态(voice)
```

### 例子 B：切罗基语（Cherokee，易洛魁语系）主宾一致

动词前缀同时标明 **主语和宾语** 的人称 / 数 / 有生性：

```
ci:y  =  1SG.主语 + 3SG.有生.宾语   （一个前缀，两个论元信息）
```

### 例子 C：印欧语系的名词格变化

- 希腊语 `kalós` 的 `-os` = 阳性 + 主格 + 单数（三个特征一包）
- 俄语 `stolá` 的 `-á` = 属格 + 单数

### 重要结论

> 累积承载的存在，说明 **相当复杂的句法结构可以被形态「压缩」掉** —— 这对理解形态-句法接口（morphology–syntax interface）至关重要。

---

## 4. 混成词（portmanteau）

**词源**：Lewis Carroll（刘易斯·卡罗尔）造的词，本指把两个词拼成一个，如 `slithy` = slimy + lithe。

**定义**：两个（或更多）历史上原本独立的词，融合成一个词。

### 例子：法语「介词 + 定冠词」

```
à  la  plage    ‘去/在 海滩’    （阴性 la，介词和冠词分开写）
de  la  plage    ‘从 海滩’

au [o]   marché  ‘去/在 市场’   （*à le → au，阳性融合成一个词）
du [dy]  marché  ‘从 市场’      （*de le → du）
```

### 与累积承载的区别（最易混）

| | 合并的对象 | 层面 |
| --- | --- | --- |
| **累积承载** | 多个 **语法特征** | 特征层面 |
| **混成词** | 多个 **词** | 词层面 |

---

## 5. 扩展承载（extended exponence）

**定义**：累积承载的反面——**一个**形态特征，**同时**被 **不止一个** 形式实现。

**关键判据**：这些标记里，**没有任何一个能单独指认「就是这个特征」**，必须合在一起才构成该特征。

### 例子 A：古希腊语完成体（Matthews 1991）

```
elelykete  ‘你们解开了’（词干 -ly-）
```

「完成体（perfective）」这一个特征，靠 **三样东西同时** 标记：

```
1. 重叠(reduplication)   le-
2. 中缀(infixation)      -k-
3. 特殊词干              -ly- （对比非完成 -ly:-）
```

谁单独都不表「完成」，合起来才表。

### 例子 B：Kujamaat Jóola 语动名词

由不定式变出名词，靠 **名词类别变化 + 元音紧张化** 两样一起，缺一不可。

---

## 6. 累积 + 扩展 同时出现（最复杂的情形）

拉丁语完成体就是「累积 + 扩展」叠加：

```
rēx  -istī     rule.PERF-2SG.ACT.PERF   ‘你统治了’
rēx  -ērunt    rule.PERF-3PL.ACT.PERF   ‘他们统治了’
```

- **扩展承载**：既要有特殊完成体词干 `rēx-`（对比现在体 `reg-`），又有完成体词尾。
- **累积承载**：词尾 `-istī` / `-ērunt` 又同时打包了人称、数、语态、完成体。

映射方向 **既多对一、又一(对)多**。

---

## 7. 补充：context-free vs. context-sensitive（语境无关 vs. 语境敏感）

这两个概念紧接在本节之后，常用于澄清「一个特征有几种实现」这个易混现象。

- **context-free（语境无关）**：一个特征 **总是** 用同一个形式实现。
  - 例：英语现在分词 / 进行体，永远是 `-ing`。
- **context-sensitive（语境敏感）**：一个特征的实现 **因词而异**。

英语过去时 `[past]` 的多种实现：

```
a. 元音交替(ablaut)   ran, sat, won, drank, shone
b. 异干(suppletion)   was, went
c. 零标记(Ø)          hit, cut, put
d. /-t/               sent, lent
e. /-d/               helped [-t], shrugged [-d], wanted [-ǝd]
```

其中 `thought`、`brought` 是 **部分异干 + /-t/ 词尾** 并用 —— 这本身就是 **extended exponence** 的例子。

> 规律：跨语言看，**context-sensitive 远多于 context-free**。

---

## 8. 一页速查：三个概念怎么分

判断「这是不是 extended exponence」，问自己：

> 这个特征，是不是在 **同一个词形** 里，靠 **两个以上** 的标记 **同时** 体现，而且 **去掉任何一个都不完整**？

| 情形 | 判定 |
| --- | --- |
| 1 特征 ↔ 1 形式 | simple exponence |
| 多特征 ↔ 1 形式 | cumulative exponence |
| 多词 → 1 词 | portmanteau |
| 1 特征 → 多标记（同词内、缺一不可） | extended exponence |
| 1 特征 → 多「可选」形式（每次只用一个、因词而异） | context-sensitive inflection |

### 易错点小结

- `man → men` 和 `apple → apples` 都是 **simple exponence**（一个特征一个标记），只是实现手段不同（元音交替 vs 加 `-s`）。
- 两者「方式不同」这个现象，叫 **context-sensitive**，**不是** extended。
- extended 的多个标记 **往往是不同类型混搭**（词干变化 + 词缀 + 重叠……），不一定是几个词缀拼一个义项。

---

## 9. 三种 exponence 在不同语言里的分布（英 / 日 / 中）

**核心认知**：三种 exponence 的「充分展现」需要 **强屈折语言**（拉丁语、古希腊语、闪语）。弱屈折语言凑得齐但不典型；孤立语根本凑不齐；粘着语介于两者之间。

| 语言 | 类型 | simple | cumulative | portmanteau | extended |
| --- | --- | --- | --- | --- | --- |
| 英语 | 弱屈折 / 偏分析 | ★★★ 遍地都是 | ★ 少而窄 | ★★ 地道 | ★ 边缘（`thought`） |
| 日语 | 粘着 | ★★ 透明 | ★ 有 | ★ 有 | ★ 有（词内） |
| 中文 | 孤立 | ✗ 无屈折 | ✗ | ✗ | ✗ |

### 英语：三种都能表示，但典型性差别大

- **simple**：`book + s`、`load + ed`、`drink + ing`，一个形式一个特征。
- **cumulative**（少而窄）：
  - 动词 `-s`（第三人称单数现在时）= 「第三人称 + 单数」两个特征打包；
  - `am` / `are` / `is` 同时表「人称 + 数 + 时态 + 语气」。
- **portmanteau**（地道）：
  - `don't` = do + not、`won't` = will + not、`I'm` = I + am；
  - `gonna` / `wanna` / `gotta`、`o'clock` = of the clock。
  - 注：这些多属「语音缩合 + 书写并合」，是否算严格的 morphosyntactic portmanteau 学界有分歧。
- **extended**（边缘）：`thought` / `brought`（部分异干 `thin- → though-` + `-t` 词尾），作者 §6.1.1 亲口给的例子。

### 中文：不是补充，是反例

- 中文是 **孤立语**，复数/时态靠**独立虚词**（`们`、`了`、`着`、`过`）或**语序**表达，几乎没有词形屈折。
- exponence 的定义**前提是「通过词形屈折实现」**，所以：
  - `们` 表复数是独立附着成分，**不是屈折词缀**，严格说不算 exponence；
  - 即便把 `们` 算进来，也只是「一个特征 ↔ 一个形式」（最多 simple），产生不了 cumulative / extended。
- 中文的作用是**衬托**：证明「屈折不是语言必备的」。

### 日语：粘着型，能提供更干净的例子

- **cumulative**：敬体 `-ます`（masu）同时表「礼貌语气 + 非过去时」。
- **portmanteau**：`である → だ`（da）是两个词并合。
- **extended**：`行く iku → 行った itta` 里，过去 = **词干音便**（`ik- → it-`）+ **词尾 `-ta`** 两样合作，有 extended 的味道。

### 结论

> 英语能三种都表示（simple 强、portmanteau 地道、cumulative 少、extended 边缘）；加**中文补不了**（无屈折，是反例）；加**日语能补**（粘着型，可提供更干净的 cumulative / extended）。要真正「三种都干净地凑齐」，得上拉丁语、古希腊语、闪语这类强屈折语言。
