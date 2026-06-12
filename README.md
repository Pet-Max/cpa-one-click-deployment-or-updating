# CPA 一键部署/更新

- 用于 Ubuntu 系统的 CLIProxyAPI 一键部署/更新脚本
- 这是一个面向 Ubuntu 22.04 及以上系统的 Bash 脚本，用于快速执行 CLIProxyAPI 的安装或更新流程，并通过 systemd 管理服务

## 适用环境

- Ubuntu 22.04及以上
- 需要 `root` 或 `sudo`
- 需要系统中可用的 `curl`、`bash`、`systemctl`、`cp`、`getent`、`sed`

## 使用教程

### 方法一：下载后执行

```bash
curl -O https://raw.githubusercontent.com/Pet-mini/cpa-one-click-deployment-or-updating/main/cpa.sh
sudo bash cpa.sh
```

### 方法二：直接执行

```bash
curl -fsSL https://raw.githubusercontent.com/Pet-mini/cpa-one-click-deployment-or-updating/main/cpa.sh | sudo bash
```

### 方法三：下载压缩包后上传执行

1. 下载项目压缩包
2. 取出其中的 `cpa.sh`
3. 将 `cpa.sh` 上传到服务器或者其他测试环境的 `/root` 文件夹下
4. 执行：

```bash
bash cpa.sh
```

## 脚本大致会做什么

1. 检查是否以 `root` / `sudo` 执行
2. 检查系统是否为 Ubuntu 22.04 及以上
3. 检查必要命令是否存在
4. 尝试停止旧的用户服务和系统服务
5. 拉取并执行上游安装器
6. 复制服务文件到 systemd 系统目录
7. 修改配置文件，默认会在配置文件中执行以下修改：
- 将 `allow-remote` 设置为 `true`，允许远程访问面板
- 将管理面板密码 `secret-key` 设置为 `admin`
9. 重载、启用并启动 systemd 服务
10. 输出服务状态

## 注意事项

- 请在你自己的服务器或测试环境中使用
- 执行前建议先阅读脚本内容，确认符合你的需求
- 如果系统环境与脚本预期不一致，可能需要你自行调整

## 上游
https://github.com/router-for-me/CLIProxyAPI

## 免责声明

本项目按当前状态提供，不承诺适用于所有环境。请在自有环境中自行验证后使用，使用后果由使用者自行承担。
