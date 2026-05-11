# OfflineDownloader

一个基于 Docker 的中文离线下载中心，支持多用户、BT / 磁力 / 种子 / HTTP / FTP / M3U8 下载、文件管理、在线播放、视频下载、回收站、用户额度、限速、到期时间和在线设备管理。

> 请只在合法授权范围内使用本项目。使用者需要自行遵守所在地区法律法规，项目作者不对任何滥用行为负责。

## 功能

- 支持 BT、BitTorrent 磁力链接、`.torrent` 种子文件
- 支持 HTTP、HTTPS、FTP、HLS / M3U8 下载
- 支持视频下载功能，可配合用户自己的 Cookie 和代理
- 支持多用户登录，管理员可添加、删除用户和修改密码
- 支持普通用户空间额度、下载限速、到期时间和可访问目录
- 支持用户在线设备查看和强制退出
- 支持注册开关、验证码、注册默认额度和默认限速
- 支持文件管理、文件搜索、新建目录、重命名、上传文件
- 支持在线播放、外部播放链接、复制直链、下载整个文件夹
- 支持删除进入回收站、恢复文件、彻底删除和一键清空回收站
- 支持 Tracker 更新、服务器时间显示、上传更新包和 GitHub 自动检查更新
- 支持中文和英文界面

## 一键安装

下载一键安装脚本后执行：

```bash
sudo bash offline-downloader-onekey-install-v1.6.6.sh
```

安装完成后会显示：

```text
离线下载中心安装完成
访问网站：http://服务器IP:端口
账户：admin
密码：随机 8 位密码
```

默认端口：

- Web：`80/tcp`
- BT：`6881/tcp`
- BT：`6881/udp`

如果需要自定义端口：

```bash
sudo WEB_PORT=8080 BT_PORT=6881 bash offline-downloader-onekey-install-v1.6.6.sh
```

安装完成后，请在云服务器安全组放行对应端口。

## 手动安装

```bash
tar -xzf offline-downloader-docker-v1.6.6.tar.gz
cd offline-downloader-docker
sudo bash install.sh
```

## 更新

管理员可以在网页后台检查 GitHub 最新版本，并自动下载 Releases 里的更新包完成更新；也可以继续手动上传更新包。

上传更新包通常使用：

```text
offline-downloader-docker-v1.6.6.tar.gz
```

也可以进入项目目录后执行：

```bash
bash update.sh
```

## 数据目录

项目默认安装到：

```text
/opt/offline-downloader-docker
```

重要目录：

- `data/`：配置、用户、会话、任务状态、Tracker 信息
- `downloads/`：下载文件
- `.env`：端口、密钥、管理员初始密码等环境变量

更新和重建容器不会主动删除 `data/` 和 `downloads/`。

## 最新版本信息

仓库根目录的 `version.json` 可用于程序检查最新版本：

```text
https://raw.githubusercontent.com/zzgood-cmd/OfflineDownloader/main/version.json
```

当前稳定版：`V1.7.5`

## 卸载

```bash
bash uninstall.sh
```

默认卸载不会删除 `data/` 和 `downloads/`。
