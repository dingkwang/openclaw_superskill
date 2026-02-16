---
openclaw:
  emoji: 🌉
  requires:
    bins:
      - code
---

# File Transfer Tunnel (VS Code Tunnel)

这个 Skill 允许 OpenClaw 通过 GitHub 建立一个安全的 VS Code Tunnel 隧道。
即使你在复杂的内网环境（如公司、学校），只要有浏览器，就能通过 `vscode.dev` 远程连接到这台机器的文件系统、终端和编辑器。

## 功能

1. **建立隧道**：启动一个安全的、基于 GitHub 授权的隧道。
2. **远程文件管理**：通过 VS Code 网页端直接进行文件的上传、下载和编辑。
3. **远程终端**：在浏览器中直接操作 OpenClaw 所在的宿主机。
4. **无需端口转发**：利用 Microsoft 的基础设施，绕过任何防火墙。

## 核心命令参考

### 1. 登录与启动隧道
首次使用需要执行登录并获得授权码（Device Flow）：
```bash
code tunnel --accept-server-license-terms
```
系统会给出一个 8 位代码和登录地址。授权成功后，隧道会自动开启，并分配一个地址如 `https://vscode.dev/tunnel/<machine-name>`。

### 2. 查看隧道状态
```bash
code tunnel status
```

### 3. 安装为系统服务 (持久化)
如果你希望重启机器后隧道也自动运行：
```bash
code tunnel service install
```

### 4. 卸载服务
```bash
code tunnel service uninstall
```

## 注意事项

- **安全性**：隧道受到 GitHub 账户保护。只有登录了对应 GitHub 账户的浏览器才能访问。
- **资源消耗**：隧道运行时会占用少量内存和 CPU。
- **OpenClaw 集成**：你可以让 OpenClaw 帮你重启隧道，或者在需要外网协助时临时开启一个限时链接。
