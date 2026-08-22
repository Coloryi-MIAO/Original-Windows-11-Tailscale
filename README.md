# 🖥️ 通过 Tailscale 在 GitHub Actions 上实现纯 Windows RDP ☁️**

该仓库提供了一套 GitHub Actions 工作流，用于创建一个干净、未经修改的 Windows 远程桌面（RDP）会话，并通过 [Tailscale](https://tailscale.com/) 网络安全访问。

此工作流有意保持极简。它**不会**应用任何性能调整、精简脚本或系统修改。您将获得一个纯净、标准的 Windows 环境，如同一块白板，供您按需自由定制。🎨

---

## ✨ 功能特点

*   ✅ **纯 Windows 环境**：运行在最新的标准 `windows-latest` 镜像上。不删除或禁用任何组件、服务或应用程序。
*   ✅ **完整管理员权限**：拥有完整的管理员权限，可安装软件、更改设置或执行任何操作。
*   ✅ **安全便捷访问**：借助 Tailscale，RDP 端口不会暴露到公共互联网。🛡️
*   ✅ **按需使用**：直接从您的 GitHub 仓库中，随时启动一台全新的 Windows 机器。
*   ✅ **零配置**：工作流开箱即用。只需提供您的 Tailscale 认证密钥，一切就绪！

---

## 🚀 使用方法

### 📋 前提条件
*   一个 **GitHub 账号**。
*   一个 **Tailscale 账号**（免费个人版即可）。

### 步骤 1：获取 Tailscale 认证密钥 🔑

1.  前往 Tailscale 管理控制台的 **[密钥页面](https://login.tailscale.com/admin/settings/keys)**。
2.  点击 **Generate auth key**（生成认证密钥）。
3.  配置密钥。为获得最佳效果，建议将其设为 **Reusable**（可重复使用）并禁用 **Ephemeral**（临时节点）。
4.  复制生成的密钥（格式类似 `tskey-auth-...`）。

### 步骤 2：将密钥添加到 GitHub Secrets 中 🔒

1.  在您的 GitHub 仓库中，进入 `Settings`（设置）> `Secrets and variables`（密钥和变量）> `Actions`（操作）。
2.  点击 **New repository secret**（新建仓库密钥）。
3.  将密钥命名为 `TAILSCALE_AUTH_KEY`。
4.  将您的 Tailscale 认证密钥粘贴到 "Secret"（密钥）字段中。
5.  点击 **Add secret**（添加密钥）。

### 步骤 3：运行工作流 ▶️

1.  进入您仓库中的 **Actions**（操作）选项卡。
2.  从侧边栏中选择 **Pure RDP via Tailscale**（通过 Tailscale 实现纯 RDP）工作流。
3.  点击 **Run workflow**（运行工作流）下拉按钮，然后点击绿色的 **Run workflow**（运行工作流）按钮。

### 步骤 4：获取连接信息 🔎

1.  等待任务启动。点击正在运行的工作流以查看其进度。
2.  展开 `Display Connection Details and Keep Alive`（显示连接详情并保持存活）步骤的日志。
3.  您将在日志中看到打印出的 **Tailscale IP 地址**、**用户名**和**密码**。

    ```sh
    ================ RDP IS READY ================
    IP Address: 100.XX.XX.XX
    Username  : runneradmin
    Password  : WindowsRDP#2025
    ==============================================
    ```

### 步骤 5：通过 RDP 连接 💻

1.  打开您喜欢的远程桌面客户端（例如 Microsoft Remote Desktop）。
2.  使用 **Tailscale IP 地址**作为计算机名/PC 名。
3.  使用日志中的用户名（`runneradmin`）和密码进行连接。

现在您已连接成功！会话将保持活跃长达 6 小时，或者直到您在 GitHub 上手动取消工作流为止。⏰
