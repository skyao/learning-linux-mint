---
title: "yt-dlp"
linkTitle: "yt-dlp"
weight: 90
date: 2025-12-03
description: >
  命令行音频/视频下载器
---


https://github.com/yt-dlp/yt-dlp

## 安装

推荐用 python 3.10 和 3.11. 

```bash
pip install yt-dlp
```

更新时，重新运行这个命令即可。


## 使用

### 下载字幕

以 https://www.youtube.com/watch?v=uwXrtyXXuy8 视频为例，先 list-subs ：


```bash
yt-dlp --no-check-certificate --list-subs "https://www.youtube.com/watch?v=uwXrtyXXuy8"
```

输出为：

```bash
[youtube] Extracting URL: https://www.youtube.com/watch?v=uwXrtyXXuy8
[youtube] uwXrtyXXuy8: Downloading webpage
[youtube] uwXrtyXXuy8: Downloading tv client config
[youtube] uwXrtyXXuy8: Downloading player c816c7d8-main
[youtube] uwXrtyXXuy8: Downloading tv player API JSON
[youtube] uwXrtyXXuy8: Downloading ios player API JSON

[youtube] uwXrtyXXuy8: Downloading m3u8 information
[info] Available automatic captions for uwXrtyXXuy8:
......


[info] Available subtitles for uwXrtyXXuy8:
Language       Name              Formats
en-eEY6OEpapPo English - English vtt, ttml, srv3, srv2, srv1, json3
```

看最后的 Available subtitles，这里只有一个 en-eEY6OEpapPo。

下载这个字幕：

```bash
yt-dlp --no-check-certificate --write-sub --sub-lang en-eEY6OEpapPo --skip-download "https://www.youtube.com/watch?v=uwXrtyXXuy8"
```