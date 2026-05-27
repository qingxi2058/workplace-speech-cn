# 打工人嘴替 · 内容工作流

> 给下一次 session 看的。避免重复问、重复返工。

---

## 仓库信息

| 项目 | 内容 |
|------|------|
| GitHub 仓库 | `qingxi2058/workplace-speech-cn` |
| 本地路径 | `/Users/zhangxin/7-github仓库/workplace-speech-cn/` |
| Skill 名称 | `workplace-speech-cn` |
| 发布命令 | `npx skills add qingxi2058/workplace-speech-cn` |

---

## 文件结构说明

| 文件 | 用途 | 改动后需要做什么 |
|------|------|-----------------|
| `SKILL.md` | Skill 主定义，Claude 用来生成话术的指令 | **必须重新上传到 redskill** |
| `JT-SCALE.md` | JT 等级框架，被 SKILL.md 引用 | 同步 GitHub 即可 |
| `xiaohongshu.md` | 6 篇小红书图文帖子，含封面文案、正文、标签 | 同步 GitHub 即可 |
| `video-script-XX.md` | 视频逐字脚本，每条帖子一个文件 | 同步 GitHub 即可 |
| `README.md` | 对外展示说明 | 改了就同步 |
| `WORKFLOW.md` | 本文件，工作流说明 | 改了就同步 |

---

## 每次工作后的操作清单

### 如果改了 SKILL.md

```
1. git add SKILL.md
2. git commit -m "feat/fix: [改了什么]"
3. git push origin main
4. 上传 SKILL.md 到 redskill ← 必做
```

### 如果只是新增/改内容文件（xiaohongshu、脚本等）

```
1. git add [文件名]
2. git commit -m "feat: [改了什么]"
3. git push origin main
4. redskill 不需要重新上传
```

---

## 内容发布顺序

| 顺序 | 帖子 | 对应脚本 | 状态 | 发布时机 |
|------|------|---------|------|---------|
| 1 | 帖子 01：JT Scale 框架 | `video-script-01-jt-scale.md` | ✅ 脚本已完成 | 任意时间，系列入口 |
| 2 | 帖子 03：拒绝加班 | `video-script-02-reject-overtime.md` | ✅ 脚本已完成 | 周一或周二 |
| 3 | 帖子 05：格局 PUA | `video-script-03-格局pua.md` | ⏳ 待写 | 任意时间，情绪共鸣强 |
| 4 | 帖子 04：被当众批评 | `video-script-04-被批评.md` | ⏳ 待写 | 任意时间 |
| 5 | 帖子 06：空头承诺 | `video-script-05-空头承诺.md` | ⏳ 待写 | 绩效季前后 |
| 6 | 帖子 02：加薪谈判 | `video-script-06-加薪.md` | ⏳ 待写 | 年中/年末/绩效季 |

---

## 视频脚本写作规范

每条脚本写完后必须自检以下 7 点再输出：

- [ ] Hook 在前 5 秒，反直觉或直戳行为
- [ ] 每个 case 有 ❌→✅ 对比 + 一句"为什么有效"
- [ ] 话术可以直接说出口，不像公文
- [ ] 金句至少 1 句，短、稳、能截图传播
- [ ] CTA 承诺续集内容，不只是"点关注"
- [ ] 估算时长在 75–95 秒之间
- [ ] 语气：站在打工人一边，不是在教课

---

## 小红书图文发布规范

- 每篇正文控制在手机屏幕 3–5 屏滑动内
- 封面用纯色底 + 大字，不做 PPT 风
- 发布后置顶评论："评论区告诉我你的场景，我来给你出话术"
- 每篇都带 `#打工人嘴替` `#职场话术` 保持搜索矩阵

---

## 常见问题

**Q：什么时候需要上传 redskill？**
A：只有 `SKILL.md` 改动时。内容文件（脚本、小红书、README）不需要。

**Q：新增场景时改哪里？**
A：`SKILL.md` 里的"高频场景快表"加一行，然后在 `xiaohongshu.md` 新增对应帖子。

**Q：视频脚本和小红书图文哪个先写？**
A：先写小红书图文（短），确认内容方向后再扩写成视频脚本（长）。

**Q：系列目前有几个话题？**
A：6 个（JT Scale / 拒绝加班 / 格局 PUA / 被当众批评 / 空头承诺 / 加薪谈判）。下一个扩展方向：同事抢功劳、试用期压价、绩效面谈。
