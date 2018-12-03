<link href="//cdn.bootcss.com/font-awesome/4.7.0/css/font-awesome.min.css" rel="stylesheet">
<script async src="//busuanzi.ibruce.info/busuanzi/2.3/busuanzi.pure.mini.js"></script>

?> <span id="busuanzi_container_site_uv"><img src="_media/visit.svg" data-origin="view.svg" alt data-no-zoom> 本站访客数 <span id="busuanzi_value_site_uv"><i class="fa fa-spinner fa-spin"></i></span> 人次</span><br><span id="busuanzi_container_page_pv"><img src="//notes.abelsu7.top/_media/view.svg" data-origin="view.svg" alt data-no-zoom> 本文阅读量 <span id="busuanzi_value_page_pv"><i class="fa fa-spinner fa-spin"></i></span> 次</span>

## 利用 docsify + Github Pages 搭建云笔记

<p>
    <div style='text-align: center'>
        <img src='https://notes.abelsu7.top/_images/cover.jpg' width='600'></img>
    </div>
    <div style='text-align: center'>
        Test image
    </div>
</p>

!> Test Hint

?> Test Info

<!-- tabs:start -->

#### ** English **

Hello!

#### ** French **

Bonjour!

#### ** Italian **

Ciao!

<!-- tabs:end -->

## 用到的插件

* docsify-pagination
* docsify-copy-code
* docsify-themeable
* zoom-image
* docsify-tabs
* search
* external-script
* prism-js

!> 引入 `prism-cpp.js` 前需先引入 `prism-c.js`

## 目录结构

```bash
├ docs/      # Github Pages 根目录
|   ├ _images/       # 图片
|   ├ _media/        # 多媒体文件 
|
|   ├ basic/         # 基础知识
|   ├ keys/          # 热键速查
|   ├ links/         # 友情链接
|   ├ offer/         # 求职应聘
|   ├ writing/       # 写作排版
|
|   ├ _coverpage.md  # 封面
|   ├ _navbar.md     # 导航栏
|   ├ _sidebar.md    # 侧边栏
|
|   ├ README.md   # docs README 文件
|   ├ index.html  # 首页，在这里配置 docsify
|   ├ CNAME       # 绑定自定义域名 notes.abelsu7.top
|   └ .nojekyll   # 阻止 GitHub Pages 忽略命名是下划线开头的文件
|    
├ README.md  # Github 仓库 README 文件
└ LICENSE    # MIT License
```

## docsify 配置

### head 标签

```html
<head>
  <meta charset="UTF-8">
  <link rel="icon" href="_media/favicon.ico">
  <title>Coding-Notes</title>
  <meta http-equiv="X-UA-Compatible" content="IE=edge,chrome=1" />
  <meta name="description" content="Notes about 💻Computer Science & 📝Coding Skills.">
  <meta name="viewport" content="width=device-width, user-scalable=no, initial-scale=1.0, maximum-scale=1.0, minimum-scale=1.0">
  <meta name="theme-color" content="#283339">
  <link rel="stylesheet" href="https://unpkg.com/docsify-themeable/dist/css/theme-simple-dark.css">
</head>
```

### 滚动条样式优化

```html
<style>
  .sidebar::-webkit-scrollbar {
    -webkit-appearance: none;
    width: 5px;
    height: 5px;
  }

  .sidebar::-webkit-scrollbar-thumb {
    /* background-color: #b6b6b6; */
    background-color: transparent;
    border: 0px solid transparent;
    border-radius: 10px
  }

  .sidebar:hover::-webkit-scrollbar {
    display: inline-block;
  }

  .sidebar:hover::-webkit-scrollbar-thumb {
    background-color: #b6b6b6;
    border: 0px solid #fff;
  }

  .sidebar:hover::-webkit-scrollbar-track {
    background-color: inherit
  }

  .sidebar::-webkit-scrollbar-thumb:active {
    background-color: #9d9d9d
  }

  .sidebar {
    -webkit-overflow-scrolling: touch
  }

  body {
    -webkit-overflow-scrolling: touch
  }

  ::-webkit-scrollbar {
    -webkit-appearance: none;
    width: 5px;
    height: 5px
  }

  ::-webkit-scrollbar-track {
    background-color: inherit
  }

  ::-webkit-scrollbar-thumb {
    background-color: #b6b6b6;
    border: 0px solid #fff;
    border-radius: 10px
  }

  ::-webkit-scrollbar-thumb:hover {
    background-color: #9d9d9d
  }

  ::-webkit-scrollbar-thumb:active {
    /* background-color: #0b87da */
  }

  @media screen and (max-width: 48em) { /* 760px */
    .sidebar::-webkit-scrollbar {
      display: none;
      background-color: transparent;
    }

    code::-webkit-scrollbar {
      /* display: none; */
      background-color: transparent;
    }
  }
</style>
```

### docsify 配置

```html
<body>
  <div id="app"></div>
  <script>
    window.$docsify = {
      name: 'Coding-Notes',
      repo: 'https://github.com/abelsu7/Coding-Notes',
      coverpage: true,
      basePath: '/',
      loadSidebar: true,
      subMaxLevel: 2,
      loadNavbar: true,
      mergeNavbar: false,
      search: {
        maxAge: 3600000, // 过期时间，单位毫秒，默认一天
        paths: 'auto',
        placeholder: 'Search',
        noData: 'No Results!',
        depth: 4 // 搜索标题的最大程级, 1 - 6
      },
      themeable: {
        responsiveTables: true // default
      }
    }
  </script>
</body>
```

### 引入 Scripts

```html
<script src="//unpkg.com/docsify/lib/docsify.min.js"></script>
<script src="//unpkg.com/docsify-pagination/dist/docsify-pagination.min.js"></script>
<script src="//unpkg.com/docsify-copy-code@2"></script>
<script src="//unpkg.com/docsify-themeable"></script>
<script src="//unpkg.com/docsify/lib/plugins/zoom-image.min.js"></script>
<!-- docsify-tabs v1.x -->
<script src="//unpkg.com/docsify-tabs@1"></script>
<script src="//unpkg.com/docsify/lib/plugins/search.js"></script>
<script src="//unpkg.com/docsify/lib/plugins/external-script.min.js"></script>
<script src="//unpkg.com/prismjs/components/prism-bash.js"></script>
<script src="//unpkg.com/prismjs/components/prism-java.js"></script>
<script src="//unpkg.com/prismjs/components/prism-go.js"></script>
<script src="//unpkg.com/prismjs/components/prism-c.min.js"></script>
<script src="//unpkg.com/prismjs/components/prism-cpp.js"></script>
```
