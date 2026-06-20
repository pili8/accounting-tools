# GitHub 仓库连通指南

## 前置条件

- 已安装 `git` 命令
- 拥有 GitHub 账号
- 已生成 Personal Access Token (PAT)

---

## 一、生成 Personal Access Token

1. 打开 GitHub → 右上角头像 → **Settings**
2. 左侧最下方 → **Developer settings**
3. **Personal access tokens** → **Tokens (classic)**
4. **Generate new token** → 勾选 `repo` 权限（完整读写）
5. 生成后复制 token（格式：`ghp_xxxxxxxxxxxx`）

> ⚠️ token 只显示一次，务必保存好。用完建议撤销重新生成。

---

## 二、克隆仓库

```bash
git clone https://github.com/pili8/accounting-tools.git
```

如果是私有仓库，克隆时需要带 token：

```bash
git clone https://pili8:<TOKEN>@github.com/pili8/accounting-tools.git
```

---

## 三、配置提交身份

```bash
cd accounting-tools
git config user.name "pili8"
git config user.email "pili8@users.noreply.github.com"
```

---

## 四、提交并推送代码

```bash
# 添加所有修改
git add .

# 提交（写清楚改了什么）
git commit -m "描述你的修改"

# 推送（首次用 main 分支）
git push origin main
```

如果是私有仓库，推送前需要设置远程地址带 token：

```bash
git remote set-url origin https://pili8:<TOKEN>@github.com/pili8/accounting-tools.git
git push origin main
```

---

## 五、推送后清除 token（安全操作）

```bash
git remote set-url origin https://github.com/pili8/accounting-tools.git
```

这样 token 不会残留在 git 配置中。

---

## 完整流程模板（私有仓库）

```bash
# 1. 克隆
git clone https://pili8:<TOKEN>@github.com/pili8/accounting-tools.git
cd accounting-tools

# 2. 配置身份
git config user.name "pili8"
git config user.email "pili8@users.noreply.github.com"

# 3. 修改文件后提交
git add .
git commit -m "你的修改说明"

# 4. 推送
git remote set-url origin https://pili8:<TOKEN>@github.com/pili8/accounting-tools.git
git push origin main

# 5. 清除 token
git remote set-url origin https://github.com/pili8/accounting-tools.git
```

---

## 公开仓库简化流程

公开仓库不需要 token 即可克隆，但**推送仍需认证**：

```bash
# 克隆（无需 token）
git clone https://github.com/pili8/accounting-tools.git
cd accounting-tools

# 推送前临时设置 token
git remote set-url origin https://pili8:<TOKEN>@github.com/pili8/accounting-tools.git
git push origin main

# 推送后清除
git remote set-url origin https://github.com/pili8/accounting-tools.git
```

---

## 给其他 AI 的指令模板

把以下内容直接发给 AI：

```
我给你一个 GitHub 仓库地址：https://github.com/pili8/accounting-tools

我的 GitHub 用户名：pili8
我的 Personal Access Token：<TOKEN>

请你：
1. 克隆仓库到你的工作目录
2. 配置 git 身份为 pili8
3. 对代码进行修改
4. 提交并推送到 GitHub
5. 推送完成后清除远程 URL 中的 token

如果仓库是私有的，克隆时使用：
git clone https://pili8:<TOKEN>@github.com/pili8/accounting-tools.git
```

---

> 📅 创建日期：2026年6月20日
