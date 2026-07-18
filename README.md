# tools

个人维护的系统工具脚本。

## nftables.sh

交互式 nftables IPv4 DNAT/SNAT 端口转发管理脚本，支持安装 nftables、添加和删除端口转发、查看现有规则及运行诊断。

### 下载和使用

建议先下载、校验和审阅，再以 root 权限执行：

```bash
curl -fL --proto '=https' --tlsv1.2 \
  https://raw.githubusercontent.com/mban9584/tools/main/nftables.sh \
  -o nftables.sh

sha256sum nftables.sh
less nftables.sh
chmod 700 nftables.sh
sudo ./nftables.sh
```

当前版本 SHA-256：

```text
e5d6c24feabaa190e00e0c08fe014889624d28f1d9a9fc3f75199672c6dd4b84
```

如果只需要一条命令：

```bash
curl -fL --proto '=https' --tlsv1.2 https://raw.githubusercontent.com/mban9584/tools/main/nftables.sh -o nftables.sh && chmod 700 nftables.sh && sudo ./nftables.sh
```

### 注意事项

- 脚本需要 root 权限，并会修改 nftables、iptables/UFW/firewalld 和 sysctl 配置。
- 初始化操作可以清空当前 nftables 规则集。远程服务器上操作前应备份防火墙配置，并准备控制台救援方式。
- 适用于使用 apt、dnf、yum 或 pacman 的常规 Linux 发行版；不建议直接在群晖 DSM 上运行。
- 使用前请确认下载哈希并自行审阅脚本内容。

## ss2022install.sh

Shadowsocks-rust 2022 安装管理脚本，支持安装、更新、卸载、配置修改和 systemd 服务管理。脚本内保留原作者署名，仓库分发版本未修改其内容。

### 下载和使用

```bash
curl -fL --proto '=https' --tlsv1.2 \
  https://raw.githubusercontent.com/mban9584/tools/main/ss2022install.sh \
  -o ss2022install.sh

sha256sum ss2022install.sh
less ss2022install.sh
chmod 700 ss2022install.sh
sudo ./ss2022install.sh
```

当前版本 SHA-256：

```text
79f55b286c9a3cc4bd61087c7afd9ff30f9119609739fb3592356e6897a9f966
```

### 注意事项

- 脚本需要 root 权限，并会安装软件包、写入 `/etc/ss-rust`、`/usr/local/bin/ss-rust` 和 systemd 服务配置。
- 安装时会从 `shadowsocks/shadowsocks-rust` 的最新 GitHub Release 下载二进制文件。当前脚本只检查下载文件是否存在且非空，没有验证发布文件的 SHA-256 或数字签名。
- 配置文件包含连接密码；脚本将其权限设置为 `600`，但查看配置功能会在终端中显示密码和完整连接链接。
- 正式使用前应审阅脚本，并确认服务器防火墙、服务端口和当地法律政策符合预期。

### 使用许可

任何人都可以下载、运行和原样分发本脚本，但未经版权所有者书面许可，不得修改、改编、创建衍生作品或发布修改后的版本。完整条款见 [LICENSE](LICENSE)。

本项目采用限制修改的源代码可用许可，不属于传统开源许可证。GitHub 允许公开仓库被浏览或派生，不代表获得发布修改版本的许可。
