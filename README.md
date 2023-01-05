# qBittorrent-Enhanced-Docker

## 支持x64、arm64、arm32平台


### 感谢以下项目:
[https://github.com/qbittorrent/qBittorrent](https://github.com/qbittorrent/qBittorrent)   
[https://github.com/c0re100/qBittorrent-Enhanced-Edition](https://github.com/c0re100/qBittorrent-Enhanced-Edition)  
[https://github.com/XIU2/TrackersListCollection](https://github.com/XIU2/TrackersListCollection)  
[https://github.com/gshang2017/docker](https://github.com/gshang2017/docker)


## 本Docker镜像说明
- 全平台架构`x86-64`、`arm64`、`armhf`
- 使用qBittorrent-Enhanced-Edition 4.2.5.10，防止迅雷吸血
- 默认中文
- 参考[johngong/qbittorrent](https://hub.docker.com/r/johngong/qbittorrent)编译

### docker命令行设置：

1. 运行docker容器
```
docker run -d \
    --name=qbittorrent-enhanced \
    -e WEBUIPORT=8989 \
    -e PUID=1000 \
    -e PGID=1000 \
    -e UMASK=022 \
    -p 6881:6881 \
    -p 6881:6881/udp \
    -p 8989:8989 \
    -e TZ=Asia/Shanghai \
    -v /path/to/config:/config  \
    -v /path/to/downloads:/downloads  \
    --restart unless-stopped \
    dzlx/qbittorrent-enhanced:4.2.5.10
```

2. 变量

|参数|说明|
|-|:-|
| `--name=qbittorrent` |容器名|
| `-p 8989:8989` |web访问端口 [IP:8989](IP:8989);(默认用户名:admin;默认密码:adminadmin);</br>此端口需与容器端口和环境变量保持一致，否则无法访问|
| `-p 6881:6881` |BT下载监听端口|
| `-p 6881:6881/udp` |BT下载DHT监听端口
| `-v /配置文件位置:/config` |qBittorrent配置文件位置|
| `-v /下载位置:/downloads` |qBittorrent下载位置|
| `-e PUID=1000` |PUID设置,默认为1000|
| `-e PGID=1000` |PGID设置,默认为1000|
| `-e UMASK=022` |umask设置,默认为022|
| `-e TZ=Asia/Shanghai` |系统时区设置,默认为Asia/Shanghai|
| `-e WEBUIPORT=8989` |web访问端口环境变量|
| `-e TRACKERSAUTO=true` |(true\|false)自动更新qBittorrent的trackers,默认开启|
| `-e TRACKERS_LIST_URL=` |trackers更新地址设置,仅支持ngosang格式,默认为 </br>https://jsd.cdn.zzko.cn/gh/XIU2/TrackersListCollection/best.txt |

