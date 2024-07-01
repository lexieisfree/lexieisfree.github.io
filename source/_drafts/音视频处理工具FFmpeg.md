---
title: 音视频处理工具FFmpeg
tags:
  - ffmpeg
---

# ffmpeg功能简介
ffmpeg是最强大的音视频处理工具（没有之一），可以实现视频转码、压缩、音频处理、格式转换、视频缩略图、添加水印滤镜、录频等等。ffmpeg由一位俄罗斯程序员编写（歪个题，俄罗斯程序员里牛人好多，想到了clickhouse、sci-hub、nginx），完全免费，支持在Linux/MacOS/Windows多平台运行。本身是一个命令行工具，因此可以**在脚本中方便地调用**，进行批量化自动处理，很多视频工具、平台、播放器都是使用到了ffmpeg或者它的核心库。

# 下载安装
- windows安装
官网下载安装包：[Download FFmpeg](https://ffmpeg.org/download.html) 
![](image-20240626203519362.png)
点击进入下载`ffmpeg-git-full.7z`，使用7zip解压。
解压后将ffmpeg.exe所在目录添加到环境变量。
- linux平台使用包管理工具安装
```bash
sudo apt install ffmpeg -y
```
- macOs使用Homebrew安装
```bash
brew install ffmpeg
```

修改brew镜像源可参考本篇视频 https://www.bilibili.com/video/BV1ig4y1w7o6

安装完成后，在终端中输入`ffmpeg -version`来确认FFmpeg已经成功安装，并查看其版本信息。

# 基本使用
官方使用文档：[ffmpeg Documentation](https://ffmpeg.org/ffmpeg.html)
视频文件封装/容器格式一般包含：音频流、视频流、字幕、元数据等
对于MP4文件，目前最常用的编码（将视频文件转换为二进制文件）格式为H.264/AVC/MPEG-4 Part 10。还有更高压缩率的H.265和VP9。

- 视频编码
```bash
#使用ffmpeg将avi视频编码为mp4
ffmpeg -i input.avi -c:v libx264 output.mp4
#使用英伟达显卡加速编码
ffmpeg -i input.avi -c:v h264_nvenc output.mp4
#通过预设压缩视频大小，选项：ultrafast/superfast/veryfast/
ffmpeg -i input.avi -c:v libx264 -preset xxx output.mp4
```
`-i`指定输入，`-c:v`指定视频编码器(video encoder)，libx264是ffmpeg默认提供的h264视频编码器。
- 转换音频
```
ffmpeg -i input.wav output.mp3
```



# 参考资料
https://www.bilibili.com/video/BV1AT411J7cH



