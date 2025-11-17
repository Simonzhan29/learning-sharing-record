# Day 01：这套「学习笔记 + YouTube + 博客 + 自动化」工作流要解决什么问题？

> 说明：这一篇既是学习笔记，也是你第一条介绍这套工作流的视频脚本草稿。
> 后面我们会一起把结构和内容细化。

## 1. 背景：为什么要折腾这套工作流？

- 你现在的学习 / 输出现状（可以写几条自己的实际情况）。
- 遇到的典型问题（例如：笔记分散、视频没脚本、没办法持续输出等）。
- 希望通过这套流程解决什么痛点。

## 2. 目标：这条工作流长什么样？

- 本地：Windows + VSCode + Git + MkDocs(Material)。
- 远端：GitHub 仓库 + GitHub Actions + 云服务器（静态站点）。
- 内容：学习笔记 + 博客文章 + YouTube 视频互相打通。

## 3. 这条工作流的大致步骤

1. 学习 & 做原始笔记；
2. 把笔记整理成结构化文章 + 视频大纲；
3. 录制和剪辑视频；
4. 上传到 YouTube，并写好标题 / 描述 / 标签；
5. 博客文章中放入视频链接；
6. 推送到 GitHub，自动部署到服务器；
7. 视频描述中补充博客文章链接，形成闭环。

## 4. 接下来要做什么？

- 先把这套工作流的最小闭环跑通；
- 然后再在这个基础上不断迭代（优化模板、自动化、脚本等）。

---

> TODO：
> - 以后你可以在这里补充更详细的笔记；
> - 根据这一篇笔记，拆出一份专门的「视频讲稿」版本。
>
> ## 第一天学习

### 1. 本地仓库 + 基础目录结构 + 最小 mkdocs.yml
Chatgpt给出的方法可用,除了问题汇总中提到的问题

### 2. 在本地把 MkDocs + Material 跑起来，看到网页预览。
Chatgpt给出的方法可用，除了问题汇总中提到的问题。




### 今天问题汇总

1. git 要安装，注意勾选可以使用Vscode调用命令
2. git 要填写用户名和邮箱地址，最好和GitHub的一致
3. 安装Python时，记得勾选Add python.exe to PATH
4. PowerShell 不允许执行脚本，这是 Windows 的安全默认设置，需要调整

### 今天扩展知识点

1. 什么是Windows的虚拟环境，怎么使用？ 虚拟环境对比Docker对比虚拟机，三种优劣在哪？
2. 什么是MkDocs + Material？为什么选用它作为博客？


````markdown
# 第一天学习：本地环境 + MkDocs 预览

> 目标：  
> 在本地完成 **Git 仓库初始化 + 基础目录结构 + 最小 mkdocs.yml**，并成功 **跑起 MkDocs + Material 的本地预览网站**。

---

## 1. 本地仓库 + 基础目录结构 + 最小 mkdocs.yml

### 1.1 初始化本地仓库

工作目录：

```text
C:\2Work\Projects\learning-workflow-demo
````

在该目录中完成了：

```powershell
git init
```

并创建了基础文件（核心几项）：

* `.gitignore`（忽略 `site/`、缓存等）
* `README.md`
* `mkdocs.yml`
* `docs/index.md`
* `docs/videos/workflow/day01.md`
* `.github/workflows/` 目录（预留给 GitHub Actions）

### 1.2 当前目录结构（简化版）

```text
learning-workflow-demo/
├─ docs/
│  ├─ index.md                      # 首页
│  ├─ notes/                        # 预留笔记目录
│  └─ videos/
│     └─ workflow/
│        └─ day01.md                # Day 01 工作流笔记
├─ .github/
│  └─ workflows/                    # 预留 Actions 配置目录
├─ mkdocs.yml                       # MkDocs 配置
├─ .gitignore
└─ README.md
```

### 1.3 最小版 `mkdocs.yml`（已就绪）

核心配置点：

* `site_name`、`site_description`：站点信息
* `theme.name: material`：准备使用 Material 主题
* `docs_dir: docs`：文档目录
* `nav`：配置首页 + Day 01 页面导航

> 到这一步：本地 Git 仓库创建成功，基本目录 + 配置文件就绪，并完成了第一次 `git commit`。

---

## 2. 在本地把 MkDocs + Material 跑起来，看到网页预览

### 2.1 Python 安装 & PATH 修正

* 安装了 **Python 3.13.9**；
* 手动把 Python 加入到 PATH 中（修正了最开始 `python` 指向 Microsoft Store 的问题）；
* 使用命令确认：

```powershell
python --version   # 输出 Python 3.13.9
pip --version      # 确认 pip 正常工作
```

### 2.2 创建和使用虚拟环境（venv）

在项目根目录：

```powershell
cd C:\2Work\Projects\learning-workflow-demo

# 创建虚拟环境
python -m venv .venv

# 激活虚拟环境
.\.venv\Scripts\Activate.ps1
```

激活成功的标志：命令行前缀变成类似：

```text
(.venv) PS C:\2Work\Projects\learning-workflow-demo>
```

> 后续所有依赖（MkDocs 等）都安装在 `.venv` 中，与系统环境隔离。

### 2.3 安装 MkDocs + Material

在虚拟环境已激活的情况下：

```powershell
pip install mkdocs mkdocs-material
mkdocs --version
```

确认 `mkdocs` 能正常运行。

### 2.4 启动本地预览

在项目根目录执行：

```powershell
mkdocs serve
```

看到类似日志：

```text
INFO    -  Serving on http://127.0.0.1:8000/
```

在浏览器中访问：

* [http://127.0.0.1:8000/](http://127.0.0.1:8000/)

可以正常看到：

* 站点标题：**学习型 YouTuber 工作流测试项目**
* 导航里有：

  * 「首页」
  * 「视频笔记 → 工作流测试项目 → Day 01：这套工作流是干嘛的？」

> 到这一步：本地 MkDocs + Material 预览站点已跑起来，最小闭环的“本地一侧”打通。

---

## 3. 今天问题汇总（症状 → 原因 → 解决方案）

### 3.1 Git 命令无法使用

**症状：**

```text
git : 无法将“git”项识别为 cmdlet、函数、脚本文件或可运行程序的名称。
```

**原因：**

* 本机没有安装 Git，或者未正确添加到 PATH。

**解决：**

1. 从 **Git for Windows 官方** 下载并安装；
2. 安装时勾选允许从命令行/VSCode 使用；
3. 安装完成后，在 PowerShell 中确认：

   ```powershell
   git --version
   ```

---

### 3.2 Git 需要用户名和邮箱

**症状：**

```text
Author identity unknown
*** Please tell me who you are.
```

**原因：**

* Git 需要知道提交的作者是谁（用户名 + 邮箱）。

**解决：**

在终端中配置一次（全局）：

```powershell
git config --global user.name "你的名字或 GitHub 用户名"
git config --global user.email "你的邮箱（最好是 GitHub 绑定的）"
```

验证：

```powershell
git config --global --list
```

然后重新：

```powershell
git add .
git commit -m "init: basic structure and minimal mkdocs config"
```

---

### 3.3 Python 安装后 `python` 命令异常（跳微软商店）

**症状：**

```text
Python was not found; run without arguments to install from the Microsoft Store...
```

**原因：**

* 安装 Python 时没有勾选 **“Add python.exe to PATH”**，
* 再加上 Windows 的 **App Execution Aliases** 用 `python` 这个名字绑了微软商店的“假壳”。

**解决：**

1. 手动将真实 Python 路径加入用户 PATH：

   * `C:\Users\user\AppData\Local\Programs\Python\Python313\`
   * `C:\Users\user\AppData\Local\Programs\Python\Python313\Scripts\`
2. 在「应用执行别名」中关闭：

   * `python.exe`
   * `python3.exe`
3. 新开 PowerShell，确认：

   ```powershell
   python --version
   pip --version
   ```

---

### 3.4 PowerShell 禁止执行 venv 的激活脚本

**症状：**

```text
无法加载文件 ... Activate.ps1，因为在此系统上禁止运行脚本。
```

**原因：**

* PowerShell 默认执行策略是禁止执行本地脚本（出于安全考虑）。

**解决：**

一次性修改当前用户的执行策略：

```powershell
Set-ExecutionPolicy -Scope CurrentUser -ExecutionPolicy RemoteSigned
```

输入 `Y` 或 `A` 确认。
然后重新打开 PowerShell，回到项目目录再执行：

```powershell
cd C:\2Work\Projects\learning-workflow-demo
.\.venv\Scripts\Activate.ps1
```

即可正常激活虚拟环境。

---

## 4. 今天扩展知识点（简要理解）

### 4.1 什么是虚拟环境？VS Docker？VS 虚拟机？

**虚拟环境（Python venv）**

* 作用：在同一台机器上，为不同项目提供**独立的 Python 依赖环境**。
* 特点：

  * 只隔离 **Python 解释器 + 第三方库**；
  * 创建速度快，轻量；
  * 适合：同一系统下多个 Python 项目并存。

**Docker 容器**

* 作用：打包“运行项目所需的一整套环境”（系统库 + 运行时 + 依赖）。
* 特点：

  * 隔离程度比 venv 高，比虚拟机轻；
  * 更接近「可复制的运行环境」；
  * 适合：部署、迁移、多人协作、避免“我这能跑你那跑不动”。

**虚拟机（VM）**

* 作用：在一台物理机器上模拟一整套**独立操作系统**。
* 特点：

  * 隔离最彻底（像多台电脑）；
  * 资源开销最大，启动慢；
  * 适合：需要完全隔离、测试不同系统/版本等场景。

**简单对比：**

* 虚拟环境：轻量级，解决“Python 项目之间依赖冲突”；
* Docker：中等重量，解决“整个应用运行环境一致性”；
* 虚拟机：重量级，解决“操作系统级别隔离”。

在本项目里：
👉 **先用 venv 就够了**，以后如果要做“可复制的一键部署环境”，再考虑 Docker。

---

### 4.2 什么是 MkDocs + Material？为什么选它做博客？

**MkDocs**

* 一个基于 Markdown 的静态文档站点生成器；
* 用 `mkdocs.yml` 配置站点，用 `docs/*.md` 写内容；
* 一条命令生成静态网站：

  ```bash
  mkdocs build
  ```

**Material for MkDocs**

* MkDocs 的一个主题（皮肤），但远不止样式：

  * 自带响应式布局、搜索、导航、暗色模式、代码高亮等；
  * 适合做文档站 / 知识库 / 笔记站；
  * 文档和社区都比较成熟。

**为什么选它来做博客 / 学习笔记站：**

1. **Markdown 优先**：写笔记 = 写 Markdown，不用关心前端框架。
2. **静态站点**：生成的是纯静态文件，部署到任意静态服务器都很简单。
3. **集成 GitHub Actions 很方便**：

   * 每次 push 自动构建；
   * 结果丢到云服务器 / GitHub Pages 即可。
4. **适合“学习型 YouTuber”工作流**：

   * 一份笔记既是博客文章，又是视频脚本；
   * 可以在文章中嵌 YouTube 链接，在视频描述中放回文章链接，形成闭环。

---

## 5. 下一步计划（预告）

> ✅ 当前已完成：
>
> * 本地 Git 仓库 + 基础结构；
> * 虚拟环境 + MkDocs + Material 安装；
> * 本地预览站点跑通。

> ⏭ 接下来要做的（Day 01 后半段）：
>
> * 把 `docs/videos/workflow/day01.md` 从“骨架”升级为一篇 **可以直接拿去录视频的脚本笔记**；
> * 顺便提炼出：以后每一期视频都可以复用的“脚本模板”。

（可以在下一步真正开始写 Day 01 的内容：
**这套工作流要解决什么问题？我的现状是什么？痛点是什么？目标是什么？**）

```
::contentReference[oaicite:0]{index=0}
```
