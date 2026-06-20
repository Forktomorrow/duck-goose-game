# 鸭腿鹅腿分类器小游戏说明

## 题库数量建议

当前版本是 20 道题，所以最低题库是 20 张图，建议鸭腿 10 张、鹅腿 10 张，避免随机偏科。

真正好玩建议做成：

- MVP：20 张，固定 20 题。
- 小程序上线版：60-100 张，每局随机抽 20 张。
- 高难版：120 张以上，分「整只烤鹅/鸭」「单腿特写」「切件」「汤菜」「带配菜遮挡」五类。

我建议先做 80 张：鸭腿 40、鹅腿 40。每局抽 20 张，其中鸭/鹅各 10 张。这样玩家复玩时不容易背答案。

## 图片怎么找

优先找可标注来源、能长期使用的图：

1. Wikimedia Commons：适合找 `duck leg confit`、`roast goose`、`Martinigans`、`Entenbraten`。
2. Flickr Creative Commons：适合找餐馆实拍，注意筛选许可证。
3. Openverse：聚合 CC 图片，能按许可过滤。
4. 自己拍：最适合上线，因为答案和版权都最稳。

搜索关键词建议用英文：

- 鸭腿：`duck leg confit`、`roasted duck leg`、`braised duck leg`、`duck legs`
- 鹅腿：`roast goose leg`、`goose leg`、`Martinigans`、`Gänsebraten`

## 替换题库

打开 `duck-goose-game.html`，找到 `const bank = [...]`。

每张图按这个格式加：

```js
{ kind: "duck", filename: "图片文件名.jpg", credit: "图片说明" }
{ kind: "goose", filename: "图片文件名.jpg", credit: "图片说明" }
```

如果你不用 Wikimedia，而是用自己的图片，可以把 `filename` 改成完整 URL，并把代码里的图片地址函数改成直接返回 URL。

## 下一步可以做成小程序

这个 HTML 已经把核心逻辑拆清楚了：题库、出题、左滑右滑、计分、结算。迁移到微信小程序时，把 `bank` 放进 JSON，把滑动逻辑改成 `touchstart/touchmove/touchend`，图片放云存储或 CDN 就可以。
