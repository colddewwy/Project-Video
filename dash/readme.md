

## 调用代码自己生成

将原始 360 度 ERP 视频放入 `video/` 目录。推荐视频比例为 `2:1`，例如 `3840x1920`。

打包全部视频：

```bash
python tools/pack_dash_tiles.py video dash_out
```

只打包单个视频：

```bash
python tools/pack_dash_tiles.py video dash_out --only video13.mp4
```

指定 tile 网格、编码预设和码率：

```bash
python tools/pack_dash_tiles.py video dash_out --cols 4 --rows 2 --preset 8 --bitrates 120k,350k,800k
```

指定 DASH 分片时长：

```bash
python tools/pack_dash_tiles.py video dash_out --segment-duration 0.5
```

默认情况下，脚本会清理并重建对应视频的输出目录。如需保留已有输出，可添加：

```bash
python tools/pack_dash_tiles.py video dash_out --keep
```

打包完成后，每个视频会生成类似结构：

```text
dash_out/video13/
├── meta.json
├── tile_0/
│   ├── manifest.mpd
│   ├── init_0.m4s
│   └── chunk_0_00001.m4s
├── tile_1/
└── ...
```

