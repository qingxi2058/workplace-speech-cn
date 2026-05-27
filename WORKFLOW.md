# Skill 创作完整 SOP

> 适用于所有 skill 的创建、优化、发布、内容变现流程。
> 每次新 session 先读本文件，按步骤执行，不重复返工。

---

## 第一步：确认需求

开始前先问清楚三件事：

1. **用户有什么具体痛点？** 要能用一句话说清楚。
2. **目标用户是谁？** 国内打工人 / 海外职场人 / 两者都要？
3. **这个 skill 要解决什么问题，不解决什么问题？** 边界要清楚。

---

## 第二步：检查本地和 GitHub 是否已有

**检查本地：**
```bash
ls ~/.agents/skills/
ls ~/7-github仓库/
```

**检查 GitHub：**
打开 https://github.com/qingxi2058 查看是否已有同类仓库。

**判断结果：**

| 情况 | 下一步 |
|------|--------|
| 本地和 GitHub 都没有 | 从零新建，跳到第三步 |
| 本地有，GitHub 没有 | 读现有文件，评估质量，迁移到 `7-github仓库` 后推上 GitHub |
| GitHub 有，本地没有 | `git clone` 到 `7-github仓库` 目录 |
| 两边都有 | 读现有文件，进入优化流程 |

---

## 第三步：审查并优化现有 SKILL.md

如果已有文件，按以下清单逐一检查：

### SKILL.md 质量检查

- [ ] **frontmatter description** 是否包含关键触发词（中英文都有更好）
- [ ] **响应流程** 是否有明确的判断步骤（不只是规则堆砌）
- [ ] **场景覆盖** 是否包含高频痛点场景
- [ ] **公式/框架** 是否有可复用的结构（不只给结论）
- [ ] **反例处理** 是否说明了哪些情况不适用
- [ ] **输出模板** 是否清晰，Claude 能直接遵循
- [ ] **立场声明** 是否说清楚 skill 的边界和原则

### 常见优化方向

| 问题 | 修法 |
|------|------|
| description 太长/太短 | 改成关键词列表，触发词要具体 |
| 场景和公式脱节 | 加映射表：场景 → 公式 |
| 只有规则没有例句 | 每个公式加一句示范语感 |
| 两处重复的输出模板 | 合并成一个标准模板 |
| 框架放在文末像附录 | 提前到第一步，强制每次先用 |

---

## 第四步：让内容吸引国内外用户

### 国内用户（小红书 / 抖音 / 微信）

- 语气要"站在用户一边"，不是在教课
- 场景要具体，能让人第一眼看到自己
- 有对比格式（❌→✅）最容易传播
- 金句要短，能截图发朋友圈

### 海外用户（GitHub / Product Hunt / X / LinkedIn）

SKILL.md 的 frontmatter description 加英文触发词：

```yaml
description: |
  Use when user needs workplace communication scripts in Chinese.
  Triggers: salary negotiation, refusing overtime, handling blame-shifting,
  responding to PUA management, severance negotiation, setting boundaries.
  用于职场对话话术：加薪/升职/拒绝加班/被甩锅/被PUA/谈赔偿/离职沟通。
```

README.md 加英文简介段落（放在中文说明之前）：

```markdown
## English Summary

A Claude skill for Chinese workplace communication.
Helps workers say what they actually mean — clearly, firmly, professionally.
Covers: salary negotiation / refusing unreasonable requests /
handling blame-shifting / anti-PUA responses / severance negotiation.
```

---

## 第五步：迁移文件夹到 `7-github仓库`

**规则：** 每个 skill 的所有资料放在同一个文件夹里，统一管理。

```
~/7-github仓库/
└── [skill-name]/
    ├── SKILL.md              ← Skill 核心定义
    ├── [框架文件].md          ← 如 JT-SCALE.md
    ├── xiaohongshu.md        ← 小红书内容
    ├── video-script-XX.md   ← 视频脚本（按序号命名）
    ├── WORKFLOW.md           ← 本文件
    ├── README.md
    └── LICENSE
```

**迁移命令（从 .agents/skills 移过来）：**
```bash
mv ~/.agents/skills/[skill-name] ~/7-github仓库/[skill-name]
```

---

## 第六步：同步 GitHub

```bash
cd ~/7-github仓库/[skill-name]

# 首次推送（新仓库）
git init
git remote add origin https://github.com/qingxi2058/[skill-name].git
git add .
git commit -m "feat: initial release"
git push -u origin main

# 日常更新
git add [改动的文件]
git commit -m "feat/fix/docs: [改了什么]"
git push origin main
```

**提交类型说明：**

| 前缀 | 用于 |
|------|------|
| `feat:` | 新增场景、新增文件 |
| `fix:` | 修正错误、补漏 |
| `refactor:` | 重组结构但内容不变 |
| `docs:` | README、WORKFLOW 等说明文件 |

---

## 第七步：上传到 redskill

**触发条件：只有 `SKILL.md` 改动时才需要上传。** 其他文件（脚本、小红书内容、README）只需 git push，不需要重新上传 redskill。

### redskill 内容怎么写

redskill 读取的就是 SKILL.md 文件，重点是 **frontmatter** 部分：

```yaml
---
name: [skill-slug]          # 全小写，用连字符，如 workplace-speech-cn
description: |
  Use when [触发场景描述]。
  关键词触发列表（中英文都写）：
  [关键词1] / [关键词2] / [关键词3]
  核心功能：[一句话说清楚这个 skill 做什么、不做什么]
---
```

**description 写法要点：**
1. 第一句必须是 `Use when` 开头，说明触发场景
2. 列出 6-12 个关键词，覆盖用户真实会说的词
3. 最后一句说清楚核心原则或边界
4. 控制在 5-8 行，不要写成段落文章

**示例（当前 skill）：**
```yaml
description: |
  Use when user needs Chinese workplace dialogue scripts.
  Triggers: 加薪/升职/涨薪、拒绝加班/临时需求、被甩锅/被背刺/被当众批评、
  老板施压/被PUA/谈赔偿/逼离/N+1、边界/底线/怎么说/怎么回、
  同事推锅/面试谈薪/离职沟通/绩效面谈。
  核心：把真话说清楚、说稳、说得体，不教撒谎，不教吃亏式圆滑。
```

---

## 第八步：写视频脚本

**写之前先确认：** 对应的小红书图文帖子是否已完成。先有图文，再扩写成脚本。

**脚本命名规范：**
```
video-script-01-[主题].md
video-script-02-[主题].md
```

**脚本结构（固定）：**

| 段落 | 时间 | 内容 |
|------|------|------|
| 开场钩子 | 0–5s | 反直觉或直戳行为，不解释 |
| 戳痛点 | 5–15s | 为什么常见做法会失效，说明机制 |
| 给逻辑 | 15–22s | 正确方向一句话 |
| Case 1–3 | 22–70s | 每个 case：❌→✅ + 一句原理 |
| 金句 | 70–80s | 短、能截图、有对比感 |
| CTA | 80–92s | 承诺续集内容，引导评论 |

**脚本自检 7 点（写完必过，不通过不输出）：**

- [ ] Hook 在前 5 秒，反直觉或直戳行为
- [ ] 每个 case 有 ❌→✅ 对比 + 一句"为什么有效"
- [ ] 话术可以直接说出口，不像公文
- [ ] 金句至少 1 句，短稳能传播
- [ ] CTA 承诺续集，不只说"点关注"
- [ ] 估算时长 75–95 秒
- [ ] 语气站在用户一边，不在教课

---

## 当前 skill 进度（workplace-speech-cn）

### 脚本状态

| 顺序 | 内容 | 脚本文件 | 状态 | 发布时机 |
|------|------|---------|------|---------|
| 1 | JT Scale 框架 | `video-script-01-jt-scale.md` | ✅ 完成 | 任意，系列入口 |
| 2 | 拒绝加班 | `video-script-02-reject-overtime.md` | ✅ 完成 | 周一/周二 |
| 3 | 格局 PUA | 待创建 | ⏳ 待写 | 任意，情绪共鸣强 |
| 4 | 被当众批评 | 待创建 | ⏳ 待写 | 任意 |
| 5 | 空头承诺 | 待创建 | ⏳ 待写 | 绩效季前后 |
| 6 | 加薪谈判 | 待创建 | ⏳ 待写 | 年中/年末/绩效季 |

### 下一步可扩展的话题

- 同事抢功劳/背刺
- 试用期被压价
- 绩效面谈被打低分
- 跨部门资源争取
- 远程办公边界沟通
