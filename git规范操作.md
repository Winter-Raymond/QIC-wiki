这是一个非常标准的软件开发协作流程。为了保证代码的安全、清晰和可追溯，遵循规范的操作流程至关重要。

以下是从拉取仓库到最终提交代码的**规范全流程操作指南**，分为四个阶段：准备阶段、开发阶段、提交阶段、推送与合并阶段。

---

### 第一阶段：准备阶段 (获取代码)

在开始工作前，确保手里的代码是最新的，并且处于正确的分支上。

**1. 克隆仓库 (Clone)**
如果是第一次获取代码：
```bash
git clone <仓库地址>
cd <项目文件夹名>
```
本仓库地址是 https://github.com/Winter-Raymond/QIE-wiki.git


**2. 切换并更新主分支 (Checkout & Pull)**
在开发新功能前，通常需要基于最新的主分支（通常是 `main` 或 `master`，或者是开发分支 `develop`）开始。
```bash
git checkout main        # 切换到主分支
git pull origin main     # 拉取远程主分支的最新代码，防止冲突
```

**3. 创建新分支 (Create Branch) [重要]**
**绝对不要直接在 `main` 或 `master` 分支上修改代码！** 必须为即将开始的任务创建一个新的分支。
分支命名规范通常为：`类型/任务描述` 或 `类型/工单号-描述`。
*   `feature/`: 新功能 (如 `feature/login-page`)
*   `docs/`：修改文档（如`docs/update-readme`）
*   `bugfix/`: 修复bug (如 `bugfix/nav-bar-error`)
*   `hotfix/`: 紧急修复 (线上问题)

例如：

```bash
# 创建并切换到新分支
git checkout -b feature/yolo-detect
```

---

### 第二阶段：开发阶段 (修改代码)

**1. 编写代码**
在这个阶段，专注于修改文件、编写业务逻辑。

**2. 查看状态 (Status)**
随时查看你修改了哪些文件，确保没有误改不该动的文件。
```bash
git status
```

**3. 暂存更改 (Add)**
将修改好的文件添加到暂存区（Staging Area）。
```bash
git add .                  # 添加所有修改和新建的文件（慎用，建议确认无误）
# 或者
git add src/utils/api.js   # 推荐：只添加特定的文件，更安全
```

---

### 第三阶段：提交阶段 (Commit)

这是最关键的一步，规范的提交信息（Commit Message）能让团队其他成员快速理解你的改动。

**1. 提交规范**
推荐使用 **Conventional Commits** 规范。格式通常为：
`<type>(<scope>): <subject>`

*   **Type (类型):**
    *   `feat`: 新功能 (feature)
    *   `fix`: 修补bug
    *   `docs`: 文档修改
    *   `style`: 代码格式修改 (不影响代码运行的变动)
    *   `refactor`: 重构 (即不是新增功能，也不是修改bug的代码变动)
    *   `chore`: 构建过程或辅助工具的变动
*   **Scope (范围):** (可选) 影响的模块，如 `login`, `api`, `styles`。
*   **Subject (主题):** 简短描述，动词开头。

**2. 执行提交**
```bash
git commit -m "feat(profile): add user avatar upload function"
```
*如果修改比较多，建议分多次 commit，保持每个 commit 的原子性（只做一件事）。*

---

### 第四阶段：推送与合并阶段 (Push & Merge)

**1. 拉取远程代码防冲突 (Pull Rebase) [进阶但推荐]**
在你开发的过程中，远程的 `main` 分支可能已经被别人更新了。为了避免合并时的复杂冲突，建议在推送前变基（Rebase）。
```bash
git pull origin main --rebase 
# 这条命令的意思是：把我的修改，由于 main 的最新提交之后 "重新播放" 一遍。
```
*如果有冲突，解决冲突后 `git add .` 然后 `git rebase --continue`。*

**2. 推送到远程仓库 (Push)**
将你的分支推送到服务器。
```bash
git push origin feature/new-user-profile
```
*如果是第一次推送该分支，Git 会提示你设置上游分支，直接复制它提示的命令即可（通常是 `git push --set-upstream ...`）。*

**3. 发起合并请求 (Pull Request / Merge Request)**
在 GitHub/GitLab/Gitee 页面上：
1.  找到你的分支。
2.  点击 **New Pull Request (PR)** 或 **Merge Request (MR)**。
3.  **Review (代码评审):** 邀请同事检查你的代码。
4.  **Merge:** 评审通过后，点击合并按钮，代码正式进入主分支。

---

### 总结流程图

1.  `git checkout main` (切回主分支)
2.  `git pull` (拉取最新)
3.  `git checkout -b feature/xxx` (切出新分支)
4.  ... 写代码 ...
5.  `git add .` (暂存)
6.  `git commit -m "feat: xxx"` (提交)
7.  `git push origin feature/xxx` (推送到远程)
8.  **去网页端提 Pull Request**

遵循这个流程，可以最大程度减少代码冲突，保持项目历史清晰。