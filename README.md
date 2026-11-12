# 唐工笔记

个人博客：结构设计、制造工艺与学习记录。

- 线上地址：https://shawntang1128.github.io
- 仓库地址：https://github.com/shawntang1128/shawntang1128.github.io

纯静态页面，无构建、无依赖。Push 到 `main` 分支后几十秒自动生效。

## 文件结构

```
.
├─ index.html            首页（首屏 + 近期文章）
├─ writing.html          全部文章列表
├─ works.html            作品与项目（目前是模板，待替你真实项目）
├─ about.html            关于页
├─ 404.html              404 页
├─ posts/                文章正文（每篇一个 html）
│  ├─ creo-parent-child.html
│  ├─ dfm-redlines.html
│  ├─ cnc-quote.html
│  └─ learning-code.html
├─ assets/
│  ├─ style.css          全站样式（只改这里就能换外观）
│  └─ favicon.svg        网站图标
└─ .nojekyll             告诉 GitHub Pages 不要用 Jekyll 处理，确保文件原样发布
```

## 新增一篇文章

1. 复制 `posts/learning-code.html`，重命名为 `posts/新文章英文短名.html`（建议全小写、用连字符）。
2. 改这五处：`<title>`、`<meta name="description">`、`<p class="kicker">`（栏目）、`<h1>`、`<p class="meta">`（日期与阅读时长）。
3. 正文写在 `<div class="prose">` 里。可用的标签：`<p>`、`<h2>`、`<h3>`、`<ul>/<li>`、`<blockquote>`、`<code>`、`<pre>`。
4. 在 `writing.html` 的文章列表里加一条：

```html
<li>
  <span class="date">2026.12.01</span>
  <div>
    <a class="t" href="posts/新文章英文短名.html">文章标题</a>
    <p>一句话摘要。<span class="tag">栏目</span></p>
  </div>
</li>
```

5. 想让它出现在首页，同样在 `index.html` 的列表里加一条（首页只留最近四篇，旧的可删掉）。

## 常改的地方

| 想改什么 | 改哪里 |
| --- | --- |
| 站点名（唐工笔记） | 所有页面里的 `<a class="brand">`、`<title>` |
| 首页大标题与简介 | `index.html` 里 `.hero` 的 `<h1>` 和 `.lede` |
| 配色 | `assets/style.css` 顶部 `:root` 里的 `--accent`（主色）、`--bg`（背景） |
| 字体 | `:root` 里的 `--serif`（标题，宋体系）、`--sans`（正文） |
| 邮箱 / 联系方式 | `about.html` 的「联系」一节 |
| 作品案例 | `works.html` 里的三张 `<article class="card">` |

## 需要替换的占位内容

- `about.html` 里的邮箱（目前写的是「待填写」）。
- `works.html` 里的三个项目案例（目前是四栏模板，结构可留着，内容要换成你自己的）。

## 本地预览

在仓库目录下运行：

```bash
python -m http.server 8000
```

然后打开 http://localhost:8000 。不要直接双击 html 文件，部分相对路径会不正常。

## 部署说明

GitHub Pages 已开启，配置为：`main` 分支、根目录。

- 推送到 `main` → 等待约 30–60 秒 → 刷新线上地址。
- 部署状态可在仓库的 Actions 页签、或 Settings → Pages 里看到。
- 已放 `.nojekyll`，所以 html 会原样发布；如果你的文件名里有下划线开头的目录，它也不会被吞掉。

## 以后想升级

现在是纯 html，优点是零风险、打开快。如果文章多到几十篇、想用 Markdown 写，可以先迁到 Jekyll（GitHub Pages 原生支持），或者 Hexo / Hugo（需 Actions 构建）。现有文章内容可以整段搬过去，不需要重写。
