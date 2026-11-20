# Drawnix Issue 修复流程

> 最后更新：2026-11-20

## 阶段一：准备 ✅

- [x] 克隆仓库 `w1tv/drawnix` → `develop` 分支
- [x] 安装依赖（yarn，140 packages）
- [x] 启动开发服务器 `http://localhost:7200`
- [x] 理解代码结构

## 阶段二：Issue 评估 ✅

- [x] 三维打分（用户影响 / 修复成本 / 依赖风险）
- [x] 优先级矩阵定位
- [x] 确定首批修复清单

## 阶段三：单 Issue 修复 SOP

每个 issue 走固定流程：

```
① 建分支  fix/<issue#>-<kebab-case>
② 复现     写最小复现步骤
③ 定位     读源码 → 日志 → 找根因
④ 改代码  必要时写/改测试
⑤ 验证    跑测试 → 手动复现 → 回归检查
⑥ 提交    规范 commit message
⑦ 推送    push origin <branch>
⑧ 合并    squash merge → develop
```

## 阶段四：批量推进

- [ ] 修完一批后更新 CHANGELOG
- [ ] 更新 README roadmap

---

## 当前状态

**阶段：四（进行中）**

### ✅ 已完成

- **#323 图片拖动残影** — CSS 修复：`display:none` → `visibility:hidden + pointer-events:none`
  - 分支：`fix/323-image-drag-ghost`
  - 已合并到 develop：`5bdc46c`

- **#478 文字样式（加粗/斜体/下划线）** — UI 按钮 + 属性函数
  - 分支：`fix/478-text-styling`
  - 新增 `setTextBold/setTextItalic/setTextUnderline`（封装 `TextTransforms.setTextMarks`）
  - 新增 `BoldIcon/ItalicIcon/UnderlineIcon`
  - 在 popup-toolbar 中添加三个 toggle 按钮，支持 5 种语言翻译
  - 底层 `@plait/text-plugins` 的 `MarkTypes.bold/italic/underline` 已内置，快捷键 Ctrl+B/I/U 也已支持

### 📋 待修

- **#392** 导出文本截断
- **#177** IndexedDB 存储
- **#413** 对齐 + 新建画布
- **#474** 思维导图键盘修复