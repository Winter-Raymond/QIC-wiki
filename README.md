# 项目开发

## 项目简介

欢迎来到 QIE Wiki 项目！这是一个基于 [MkDocs](https://www.mkdocs.org/) 和 [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/) 主题构建的个人知识库/Wiki 系统。
本项目开始于2025年，目标是搭建属于QIE（Qian Xuesen Innovation and Expansion Class，作者自己想的简称 doge）的知识库，
服务于后来的学弟学妹，欢迎钱班的大家参与开发，作者会一直维护下去的

## 🚀 快速开始

如果你想在本地运行该项目进行预览或开发，请按照以下步骤操作。

### 1. 环境准备

确保你的电脑上已经安装了：
*   [Python 3.8+](https://www.python.org/downloads/)
*   [Git](https://git-scm.com/)

### 2. 获取代码

打开终端/命令行，克隆本项目到本地：

```bash
git clone https://github.com/Winter-Raymond/QIE-wiki.git
cd QIE-wiki
```

### 3. 安装依赖

建议在项目根目录下运行以下命令安装所需的 Python 包：

```bash
pip install -r requirements.txt
# 该命令会直接根据requirments.txt安装和作者一样的环境
```

### 4. 本地预览

安装完成后，运行以下命令启动本地服务器：

```bash
mkdocs serve
```

启动成功后，打开浏览器访问 [http://127.0.0.1:8000](http://127.0.0.1:8000) 即可看到实时预览。
**注意：** 在本地编辑 Markdown 文件并保存后，网页会自动刷新，无需重启服务。

---

## 📝 贡献指南

我们非常欢迎你为 QIE Wiki 添加内容！

### 项目结构

```text
.
├── docs/               # 文档源文件目录（所有文章都在这里）
│   ├── images/         # 存放图片的目录
│   ├── algorithm/      # 示例：分类文件夹
│   └── index.md        # 首页
├── mkdocs.yml          # 网站配置文件（修改菜单在这里）
└── README.md           # 项目说明文档
```

### 如何添加新文章

1.  **创建文件**：在 `docs/` 目录下（或相应的子目录下，这里更推荐再对应的类别子目录下）创建一个新的 `.md` 文件，比如CS相关知识写在CS下，数学相关内容写在数学对应目录下。
2.  **撰写内容**：使用 Markdown 语法编写内容。
    *   支持 LaTeX 数学公式，例如 `$\sum_{i=0}^n i^2$`。
    *   支持代码高亮。
3.  **注册菜单**：打开根目录下的 `mkdocs.yml` 文件，找到 `nav:` 字段，将你的新文件路径添加进去。

**示例 (`mkdocs.yml`)：**

```yaml
nav:
  - 首页: index.md
  - 新分类:
      - 我的新文章: new-folder/my-new-post.md
```

### 提交更改

完成编辑后，请将代码推送到 GitHub：
```bash
git add .
git commit -m "添加了关于XXX的文章"
git push
```
这一步具体如何操作请查看，项目根目录下的：git规范操作.md。作者已经锁死了main分支，所以这样是提交不上去


## 🚀 部署机制

本项目使用 **GitHub Actions** 进行自动部署。

*   **自动构建**：每当你将代码 `push` 到 `master` (或 `main`) 分支时，GitHub Actions 会自动触发构建流程。但是按照规范提交，一般会提交再新分支上，这时候由作者审核提交后，再把相关分支合并到主分支才能再在线网站看到变化。
*   **发布页面**：构建完成的内容会自动发布到 `gh-pages` 分支，并更新在线网站，该在线网页地址为：https://winter-raymond.github.io/QIE-wiki/
*   **无需手动操作**：请勿手动运行 `mkdocs gh-deploy`，让 CI/CD 自动处理即可。

## 📄 许可证

暂无