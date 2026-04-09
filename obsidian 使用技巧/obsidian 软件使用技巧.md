# 插件

## 推荐插件


| 插件名                        | 说明                          | 使用方法                        |
| -------------------------- | --------------------------- | --------------------------- |
| 核心插件-斜杠命令                  | 当输入 / 时候能出现快捷方式             |                             |
| Iconize                    | 用于为 obsidian 文件夹自定义图标       | 插件类可以选择图标库<br>邮件文件夹可以修改图标   |
| custom-attachment-location | 用于管理 md 图片                  |                             |
| Enhancing Export           | 用于导出笔记为 html 、 word         |                             |
| Image Toolkit              | 图片预览                        | 点击图片后能够预览图片                 |
| Mousewheel Image Zoom      | 改变文档中图片大小                   | 鼠标放于图片上  atl + 鼠标滚轮操作       |
| Global Proxy               | 给 Obsidian 增加代理服务器配置的选项     |                             |
| Manual Sorting             | 控制知识库文件、文件夹顺序               |                             |
| Local Images Plus          | 对网页复制文字+图片时候，下载图片到本地        |                             |
| Outliner                   | 文档内改变标题+内容顺序                | 大纲上面选中移动（慎用容易内容错乱）          |
| Smart Composer             | AI 相关                       |                             |
| Copilot                    | AI 相关                       |                             |
| linter                     | 格式化 md 文档                   |                             |
| Link Remover               | 去除超链接                       | 选中文字右键能够去除，可以设置快捷键 crtl + \ |
| Git                        | 管理知识库,提交到仓库                 |                             |
| Remotely Save              | 用于 obsidian 同步到类似 onedriver |                             |
| Github sync                | 用于 obsidin 同步到 github       | windows mac                 |
| GitHub Gitless Sync        | 用于 obsidin 同步到 github       | 手机能够安装                      |
|                            |                             |                             |
|                            |                             |                             |



## 插件安装


### 方法一： 社区插件市场 安装

设置 -> 第三方插件 (关闭安全模式) -> 社区插件市场

![](assets/obsidian%20软件使用技巧/file-20260330222843820.png)


### 方法二： 离线插件


>安装说明：

- 解压文件：将 .zip 文件解压，得到插件文件夹。
-  放入插件目录：

![](assets/obsidian%20软件使用技巧/file-20260330222843825.png)


![](assets/obsidian%20软件使用技巧/file-20260330222843827.png)

- 找到 Obsidian 的 vault（笔记库）文件夹。
- 直接将解压得到的plugin文件夹粘贴到 .obsidian文件夹
- 最终路径应为：你的 vault 路径/.obsidian/plugins。

![](assets/obsidian%20软件使用技巧/file-20260330222843829.png)

- **启用插件**：
    - 打开 Obsidian，进入“设置” > “社区插件”。
    - 确保“安全模式”已关闭（如果未关闭，点击“关闭安全模式”）。
    - 在“已安装的插件”列表中找到新添加的插件（例如 Dataview），点击“启用”。

![|675](assets/obsidian%20软件使用技巧/file-20260330222843831.png)
- 可能需要重启 Obsidian 以确保插件加载。



## GIT 管理知识库



### 构建 git 仓库

```shell
### 创建 .gitgnore 文件
### windows 创建时候可以是  .gitgnore.
### 排除 workspace 相关文件，由于其记录了当前 obsidian 情况，会被频繁更改
.obsidian/workspace.json
.obsidian/workspace-mobile.json

## 命令windows
echo .obsidian/workspace.json >> .gitignore.
echo .obsidian/workspace-mobile.json >> .gitignore.

### 提交 github public 仓库会拦截，由于其包含了 Google OAuth Client ID 和 Client Secret等敏感信息
### base 仓库没有，其他知识库使用时候需要独立安装
### smart composer
.obsidian/plugins/smart-composer/
### remotely save
.obsidian/plugins/remotely-save/

### github gitless sync 插件下会记录 github token 不建议提交
.obsidian/plugins/github-gitless-sync/

### 移除已提交内容
git rm -r --cached .obsidian/plugins/remotely-save/

### windows
echo # knowledge.obsidian.it >> README.md
### 初始化仓库 (只需要操作一次)
### cmd 命令行
git init
git add README.md
### 将仓库中所有东西提交
git add .
git commit -m "first commit"
### 现在推荐为 main 而非 master， `main` 更符合“主干分支”的语义
git branch -M main
### 以下地址自行修改
git remote add origin https://github.com/213sky/knowledge.obsidian.base.git
git push -u origin main
### 此时会让输入密码等信息
```


当提交 github 时候 FAQ
```
### 错误 remote: Invalid username or token. Password authentication is not supported for Git operations.
## 1. 获取 token
https://github.com/settings/tokens
## 2. 建议选
Fine-grained token（推荐）-> 没有token创建 -> Repository access → Only select repositories -> Generate token -> 权限选择 Contents

### 错误 error: src refspec main does not match any
## 可能未有提交，检查是否有更新 git status


```

### 插件安装

git

### 插件配置

```
--- 配置更改后自动提交+提交周期
Auto commit-and-sync after stoping file edits
勾选 -> 开启

Auto commit-and sync interval(minutes)
设置 -> n 分钟

--- 配置每次启动 obsidian 后自动拉取
Pull on startup
勾选 -> 开启
```


## github-gitless-sync 使用

### 项目目录操作

```
### 项目目录创建 .gitless/manifest.json
### 文件内容
{
  "version": "1.0",
  "files": []
}
```

### git 权限开放

```
### 网址
https://github.com/settings/personal-access-tokens

### 开启token
Fine-grained token（推荐）-> 没有token创建 -> Repository access → Only select repositories -> Generate token -> 权限选择 Contents
### token 及时复制，否则会消失，需要重新生成 token
```


### 插件配置

```
### 配置
GitHub token : 配置生成的token
Owner        : git 用户名
Repository   : 仓库名称
```


## custom-attachment-location 安装与使用


### 插件安装

custom-attachment-location

### 插件配置 

```
--- Markdown URL 格式
assets/${noteFileName}/${generatedAttachmentFilename}

--- 附件重命名模式
选择 -> 全部 (推荐选择: 图片)

--- 是否重命名附件文件
勾选 -> 是
```

### 系统配置

```
--- 设置-> 文件与链接

--- 使用 Wiki 连接
勾选 -> 否

--- 内部链接类型
选择 -> 基于当前笔记的相对路劲
```




## Enhancing Export 安装与使用

### 插件安装

Enhancing Export

### pandoc 下载与安装

```
--- 下载地址
https://github.com/jgm/pandoc/releases/tag/3.9.0.2

--- 安装
解压到目录，右键复制 pandoc.exe 文件路劲
```

### 插件配置

```
--- 配置 pandoc 路劲
将 pandoc.exe 路劲配置上
```

### 使用

```
右键文件 -> 导出 -> 选择相应格式导出
```



# 主题

## 主题安装

设置 -> 外观 -> 主题 (管理)

- Obsidianite
- Things
- Blue Topaz




# 使用技巧


## 打开文件的大纲

### 方法一

```
更多选项(文件右上角) -> 打开当前文件的... -> 打开大纲
```


### 方法二


右上角

![|500](assets/obsidian%20软件使用技巧/file-20260330234316590.png)


# chrome 插件

```
--- 插件名
# Obsidian Web Clipper
```

![](assets/obsidian%20软件使用技巧/file-20260330222843823.png)