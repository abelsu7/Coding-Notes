?> ![](https://notes.abelsu7.top/_media/vscode.svg ':no-zoom')VS Code

!> [![](https://notes.abelsu7.top/_media/vscode.svg)keyboard-shortcuts-windows.pdf](https://code.visualstudio.com/shortcuts/keyboard-shortcuts-windows.pdf)

## VS Code 快捷键

| Keys | Function |
| :-- | :-- |
| **Ctrl-P** | 转到文件 |
| **Ctrl-Shift-P** | 命令面板 |
| **F1** | 命令面板 |
| **Ctrl-Shift-O** | 前往当前文件中的符号 |
| **Ctrl-T** | 前往工作区中的符号 |
| **Ctrl-Shift-K** | 删除当前行 |
| **Ctrl-Shift-方向** | 跨词选择多行 |
| **Ctrl-Alt-↑/↓** | 光标选择多行 |
| **Ctrl-Alt-←/→** | 拆分代码窗口 |
| **Alt-↑/↓** | 移动当前行 |
| **Alt-Shift-↑/↓** | 复制当前行 |
| **F3** | 查找下一个匹配 |
| **Ctrl-Shift-U** | 查看输出 |
| **Ctrl-Alt-N** | 运行代码 |
| **Ctrl-Alt-M** | 停止运行 |
| **Alt-Shift-F** | 格式化代码 |
| **Alt-O** | 切换头文件/源文件 |
| **Ctrl-K Ctrl-R** | 键盘快捷方式参考 |
| **Ctrl-K Z** | 专注模式 |
| **Ctrl-K W** | 关闭当前所有标签 |

## Java in VS Code

- [![](logo/vscode.svg)Java Web Apps with Visual Studio Code![](logo/star.svg)![](logo/star.svg)](https://code.visualstudio.com/docs/java/java-tutorial)

## Markdown

- [在 VSCode 下用 Markdown Preview Enhanced 愉快地写文档 | 知乎](https://zhuanlan.zhihu.com/p/56699805)
- [VSCode Markdown Snippet 配置 | CSDN](https://blog.csdn.net/serryuer/article/details/89393760)
- [【VScode】使用Snippets（用户代码片段）使 Markdown 文件快速生成代码 | NipGeihou Blog](https://nipgeihou.com/vscode_Snippets_markdowm/)


## Snippets

- [在 Visual Studio Code 中添加自定义的代码片段 | walterlv 吕毅](https://blog.walterlv.com/post/add-custom-code-snippet-for-vscode.html)
- [![](logo/csdn.ico ':size=16')跟我一起在Visual Studio Code 添加自定义snippet（代码段），附详细配置 | CSDN](https://blog.csdn.net/maokelong95/article/details/54379046)
- [![](logo/csdn.ico ':size=16')Visual Studio Code 自定义Snippet配置 | CSDN](https://blog.csdn.net/u011127019/article/details/73461831)

```json
{
    "github.svg": {
        "prefix": "svggithub",
        "body": "![](logo/github.svg)",
        "description": "github.svg"
    },
    "wechat.svg": {
        "prefix": "svgwechat",
        "body": "![](logo/wechat.svg)",
        "description": "wechat.svg"
    },
    "star.svg": {
        "prefix": "svgstar",
        "body": "![](logo/star.svg)",
        "description": "star.svg"
    },
    "zhihu.svg": {
        "prefix": "svgzhihu",
        "body": "![](logo/zhihu.svg)",
        "description": "zhihu.svg"
    },
    "csdn.ico": {
        "prefix": "icocsdn",
        "body": "![](logo/csdn.ico ':size=16')",
        "description": "csdn.ico"
    }
}
```

## 插件推荐

- [如何快速上手一款 IDE - VSC 配置指南和插件推荐 | 小胡子哥](https://mp.weixin.qq.com/s?__biz=MzAxMjA5ODQwMQ==&mid=2455058817&idx=1&sn=32ba09d2cfb28c472b9c343358f6e468&chksm=8c16978fbb611e9954cb242a218e4ae0d878f1cc3927de14c0dd18b2c40505108a99a512b888&mpshare=1&scene=1&srcid=1121ZPSO0rlv4GswvIs79Lod#rd)

### C/C++

- [Visual Studio Code 配置 C/C++ 编译运行环境 | Cyprestar](https://www.cyprestar.com/2019/03/11/Configure-vscode-for-cpp/)

### 语言支持

- C/C++
- C/C++ GNU Global
- Chinese(Simplified) Language Pack
- Go
- Go Test Explorer
- Go Mod Grapher
- Python
- Excel Viewer
- Rainbow CSV
- Txt Syntax

### Markdown

- Markdown All in One
- Markdown Preview Enhanced
- qiniu-fig-bed
- qiniu-upload-image

### 数据库

- SQLTools

### 图床

- PicGo

### 主题美化

- Monokai++
- Material Icon Theme
- vscode-icons
- Highlight Line
- Select Line Status Bar
- Banner Comments
- Beautify

### 资源监控

- Filesize
- Resource Monitor

### 常用工具

- Code Runner
- Gitlens
- Open
- Open in browser
- Vim
- REST Client
- SVG Viewer
- Todo Tree
- VSC Netease Music

## 用户设置

```json
{
    // Editor
    "editor.minimap.enabled": true,
    "editor.detectIndentation": false,
    "editor.wordWrap": "on",
    "editor.renderWhitespace": "none",
    "editor.snippetSuggestions": "top",
    "editor.suggestSelection": "first",
    "editor.renderLineHighlight": "all",
    "editor.quickSuggestions": {
        "other": true,
        "comments": false,
        "strings": false
    },
    // Workbench
    "workbench.statusBar.visible": true,
    "workbench.activityBar.visible": true,
    "workbench.editor.highlightModifiedTabs": true,
    "workbench.sideBar.location": "right",
    "workbench.colorTheme": "Monokai++",
    "workbench.iconTheme": "material-icon-theme",
    "workbench.startupEditor": "none",
    // Window
    "window.titleBarStyle": "custom",
    // 面包屑导航
    "breadcrumbs.enabled": true,
    // Markdown
    "[markdown]": {
        "editor.wordWrap": "on",
        "editor.renderWhitespace": "all",
        "editor.quickSuggestions": {
            "others": true,
            "comments": true,
            "strings": true
        },
        "editor.acceptSuggestionOnEnter": "on"
    },
    // Markdown All in One
    "markdown.extension.toc.updateOnSave": false,
    "markdown.extension.toc.githubCompatibility": true,
    "markdown.extension.toc.levels": "2..3",
    // Markdown Preview Enhanced
    "markdown-preview-enhanced.mermaidTheme": "default",
    "markdown-preview-enhanced.previewTheme": "atom-dark.css",
    "markdown-preview-enhanced.codeBlockTheme": "monokai.css",
    // Search
    "search.showLineNumbers": true,
    // Update
    "update.enableWindowsBackgroundUpdates": false,
    // Code Runner
    "code-runner.runInTerminal": true,
    // Go
    "go.gopath": "C:\\Users\\<YOUR_NAME>\\go",
    "go.goroot": "C:\\Go",
    "go.inferGopath": false, // 使用 Go Modules 时无需 inferGopath
    "go.useLanguageServer": true,
    "go.autocompleteUnimportedPackages": true,
    "go.gotoSymbol.includeImports": false,
    "go.gotoSymbol.includeGoroot": false,
    "go.useCodeSnippetsOnFunctionSuggest": true,
    "go.useCodeSnippetsOnFunctionSuggestWithoutType": true,
    "go.lintOnSave": "file",
    "go.buildOnSave": "off",
    "go.formatTool": "goimports",
    "go.testFlags": [
        "-v"
    ],
    // Terminal
    "terminal.integrated.setLocaleVariables": false,
    // 代理
    "http.proxyStrictSSL": false,
    // 网易云音乐
    "NeteaseMusic.CDN.redirect": false,
    // Git
    "git.ignoreLegacyWarning": true,
    // 字体
    "editor.fontFamily": "'Cascadia Code', Consolas, 'Courier New', monospace, '苹方-简', 'Sarasa Gothic SC'",
    "editor.fontLigatures": true,
}
```