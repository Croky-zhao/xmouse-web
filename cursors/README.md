# 鼠标样式云端清单

`cursors.json` 是 XMouse App 的远程样式清单，App 启动时会拉取此文件来展示可用的鼠标样式。

## 怎么加一个新样式

### 步骤 1: 准备 2 张 PNG

- **`<id>_preview.png`** — 卡片中显示的预览图（建议 64-128px，带透明背景）
- **`<id>_actual.png`** — 实际应用为鼠标指针的图（建议 32-64px，带透明背景）

`<id>` 必须是英文短名（如 `red_arrow`、`heart`），全小写下划线分隔。

### 步骤 2: 把 PNG 上传到 `cursors/` 文件夹

放在跟现有样式 PNG 同一个文件夹下。

### 步骤 3: 编辑 `cursors.json`

在 `cursors` 数组末尾加一项：

```json
{
  "id": "red_arrow",
  "name": "红色箭头",
  "isPremium": true,
  "order": 5,
  "previewImage": "https://xmouse.top/cursors/red_arrow_preview.png",
  "actualImage": "https://xmouse.top/cursors/red_arrow_actual.png"
}
```

- `id`: 跟图片文件名前缀一致
- `name`: 中文显示名（用户看到的）
- `isPremium`: `true` 表示 Pro 会员专属；`false` 表示免费样式
- `order`: 显示顺序，数字小的排前面（建议预留空隙，比如 10, 20, 30 以便后续插入）
- 两个 URL：替换 `red_arrow` 为你的 id

### 步骤 4: 把改动 commit + push

```bash
cd /Users/corky/Desktop/XMouse/xmouse-web
git add cursors.json cursors/red_arrow_preview.png cursors/red_arrow_actual.png
git commit -m "add: red arrow cursor style"
git push
```

GitHub Pages 会在 1-2 分钟内自动重新发布。

### 步骤 5: 用户 App 拉到新样式

用户 **下次启动 XMouse** 时会自动拉取新清单。**不需要他们重新下载 App**。

## 怎么下架一个样式

把对应的对象从 `cursors.json` 的 `cursors` 数组里删除即可。已经在用该样式的用户**继续可用**（依赖本地缓存），但新用户看不到该样式。

`cursors/` 文件夹里的 PNG **建议保留**——已经选择该样式的用户的 App 还需要下载它。

## 修改现有样式

直接编辑 `cursors.json` 里的字段（如 `name`、`isPremium`）。用户下次启动 App 自动同步。

⚠️ **不要改 `id`** —— `id` 是用户本地记住"当前用的哪个样式"的依据。改 id 会导致用户的"当前样式"丢失。

## JSON Schema 当前版本

`version` 字段当前为 `1`。如果未来 schema 不兼容地变更（比如改字段名），版本号会增加，App 会做兼容处理。
