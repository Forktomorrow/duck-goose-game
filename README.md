# Duck Goose Game

一个围绕「鹅腿阿姨」热梗做的轻量网页小游戏：看图判断这是鸭腿还是鹅腿，20 题一局，手机左右滑，电脑点按钮。

[在线游玩](https://forktomorrow.github.io/duck-goose-game/) · [项目主页](https://github.com/Forktomorrow/duck-goose-game)

## 这是什么

「鸭腿还是鹅腿？」是一个偏梗向、偏社交传播的小测验。玩家需要在一张张烧鸭、烧鹅、鸭腿、鹅腿图片里快速判断，最后根据得分解锁不同的结算文案和阿姨表情。

游戏里混入了绿色鸭腿、葱叶汁、蔬菜汁、白糖色、同学们、腿腿饿饿等梗元素，但核心体验还是一个简单直觉的视觉判断题：你到底能不能一眼认出鸭腿和鹅腿？

## 玩法

- 手机端：左滑选鸭腿，右滑选鹅腿
- 电脑端：点击「鸭腿」或「鹅腿」按钮
- 每局 20 题，固定 10 张鸭腿/鸭类题 + 10 张鹅腿/鹅类题
- 答题后图片上会短暂停留水印反馈
- 结算页会根据得分给出不同的小故事、聊天气泡和阿姨状态

## 项目亮点

- **移动端优先**：适合微信、QQ、浏览器直接打开分享链接游玩
- **本地题库**：图片随 GitHub Pages 一起托管，避免远程图源加载失败
- **平衡抽题**：每局鸭/鹅比例固定，且同一局不会重复图片
- **梗向叙事**：用聊天框、热搜播报、结算故事把事件梗做进游戏流程
- **零后端部署**：纯 HTML/CSS/JavaScript，GitHub Pages 即可托管

## 技术实现

项目是一个静态网页应用：

- `docs/index.html`：GitHub Pages 入口
- `docs/duck-goose-game.html`：游戏主页面
- `docs/duck-goose-assets/final50/`：精选本地题库图片
- `outputs/`：本地交付版本，与 `docs/` 保持同步

核心逻辑包括：

- 预加载本局 20 张图片
- 按题库类型抽取 10 鸭 + 10 鹅
- 用 `group` 去重，避免一局内重复图片
- 图片加载失败时按同类型尝试替换
- 用 CSS 和少量 JavaScript 实现滑动、按钮、反馈水印和结算页

## 本地预览

```bash
python3 -m http.server 8766 --directory docs
```

然后打开：

```text
http://127.0.0.1:8766/
```

## 部署

本项目通过 GitHub Pages 部署：

- Branch: `main`
- Source folder: `/docs`
- Public URL: https://forktomorrow.github.io/duck-goose-game/

只要更新 `docs/` 并推送到 `main`，GitHub Pages 会自动刷新线上版本。

## 备注

这个项目是一个梗向互动作品，不是严肃的食品识别模型。题库经过人工筛选，尽量保留能看到真实鸭/鹅腿或清楚烧鸭/烧鹅实体的图片，避免门头、菜单、活体和无关食物干扰判断。
