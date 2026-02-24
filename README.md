# her voice — 部署指南

## 仓库结构

```
voice-archive/
│
├── index.html        ← 网页播放器（不需要改）
├── manifest.json     ← 语音文件清单（每次添加语音后要更新这个）
├── README.md         ← 本文件
│
└── voices/           ← 把所有语音文件放这里
    ├── 001.aac
    ├── 002.aac
    └── ...
```

---

## 第一次部署（一次性设置）

### 第一步：创建 GitHub 账号
去 https://github.com 注册账号，记住用户名

### 第二步：创建仓库
1. 登录后点右上角 **+** → **New repository**
2. Repository name 填：`voice-archive`（或任何名字）
3. 选 **Private**（这样只有你知道链接才能访问）
4. 点 **Create repository**

### 第三步：上传文件
1. 点页面中央的 **uploading an existing file** 链接
2. 把以下文件全部拖进去：
   - `index.html`
   - `manifest.json`
3. 点 **Commit changes**

### 第四步：创建 voices 文件夹并上传语音
1. 点 **Add file** → **Upload files**
2. 在上传前，先在文件名输入框里输入 `voices/` —— 这会创建文件夹
3. 把你的 `.aac` 语音文件拖进来
4. 点 **Commit changes**

### 第五步：开启 GitHub Pages
1. 进入仓库 → 点 **Settings**（设置）
2. 左侧菜单找 **Pages**
3. Source 选 **Deploy from a branch**
4. Branch 选 **main**，文件夹选 **/ (root)**
5. 点 **Save**
6. 等 1-2 分钟，页面会显示你的网址：
   `https://你的用户名.github.io/voice-archive/`

---

## 更新 manifest.json

每次添加新语音后，需要更新 `manifest.json`，告诉网页有哪些文件。

格式如下，每个语音一个 `{}` 块：

```json
{
  "tracks": [
    {
      "name": "voice 001",
      "file": "001.aac",
      "duration": null
    },
    {
      "name": "voice 002",
      "file": "002.aac",
      "duration": null
    },
    {
      "name": "voice 003",
      "file": "003.aac",
      "duration": null
    }
  ]
}
```

- `name`：播放器里显示的名字，随便写
- `file`：voices/ 文件夹里的实际文件名，要完全一致
- `duration`：填 null，网页会自动获取时长

---

## 后续添加新语音（日常操作）

1. 打开仓库页面
2. 点进 `voices/` 文件夹
3. 点 **Add file** → **Upload files**
4. 上传新的 `.aac` 文件
5. Commit changes
6. 回到仓库根目录，点 `manifest.json`
7. 点右上角铅笔图标（Edit this file）
8. 在 `tracks` 数组里添加一个新的 `{}` 块
9. Commit changes
10. 等 30 秒，刷新你的网站就能看到新语音了

---

## 常见问题

**语音播放不了？**
检查 `manifest.json` 里的 `file` 字段和 `voices/` 里的文件名是否完全一致（包括大小写和扩展名）

**网站打不开？**
等几分钟，GitHub Pages 部署需要时间。也可以在 Settings → Pages 查看部署状态

**想换名字？**
改 `manifest.json` 里的 `name` 字段就行，不影响文件本身
