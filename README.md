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
