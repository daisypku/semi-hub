# CCL 产业链知识库 — 使用说明

## 目录结构

```
market-daily/                          （你的 GitHub 仓库根目录）
├── diagram002.html                    CCL 产业链图谱（入口）
└── company/                           公司知识库模块
    ├── index.html                     通用模板页（一份代码，所有公司共用）
    └── data/
        ├── companies.json             82 家公司的基础信息（结构化数据）
        └── reports/                   你的深度报告，一家一个 .md 文件
            ├── 600183_SS.md           生益科技（示例）
            ├── 002463_SZ.md           沪电股份（待写）
            └── ...
```

## 它是怎么工作的

1. 用户在产业链图里点一家公司（比如"生益科技"）
2. 浏览器跳转到 `company/?ticker=600183.SS`
3. `company/index.html` 从 URL 里读出 ticker，去 `data/companies.json` 拿基础信息
4. 再尝试去 `data/reports/600183_SS.md` 拿你的深度报告
5. 用 marked.js 把 Markdown 渲染成 HTML 展示

**关键点**：
- 只有**一份 HTML 模板**，所有 82 家公司共用。以后改版式，改这一个文件即可。
- **新写报告**只需要在 `reports/` 里新建一个 `.md` 文件，文件名用 ticker（把点号换成下划线）。**不用改任何 HTML 代码**。
- **纯静态**，可以直接托管在 GitHub Pages，别人通过网址就能访问。

## 日常操作

### 为某家公司写深度报告

1. 找到对应 ticker，把点号换成下划线：
   - `600183.SS` → `600183_SS`
   - `9992.HK` → `9992_HK`
   - `5706.T` → `5706_T`
2. 在 `company/data/reports/` 里新建 `600183_SS.md`
3. 用你熟悉的编辑器（VS Code / Typora / Obsidian）写 Markdown
4. 保存、push 到 GitHub —— 页面立即生效

报告支持所有标准 Markdown 语法：标题、列表、**加粗**、*斜体*、表格、引用、代码块、链接、图片等。

### 更新某家公司的基础信息

编辑 `company/data/companies.json`，找到对应 ticker 的条目，修改 `description`、`appearances` 等字段。

### 新增一家公司（扩充到 82 家以外）

编辑 `company/data/companies.json`，按现有格式添加一个条目：

```json
"NEW.TICKER": {
  "ticker": "NEW.TICKER",
  "ticker_slug": "NEW_TICKER",
  "name": "新公司名",
  "description": "一句话介绍",
  "yahoo_url": "https://finance.yahoo.com/quote/NEW.TICKER/",
  "appearances": [{
    "step_num": "1",
    "step_name": "环节名称",
    "submaterial": null,
    "region": "🇨🇳 大陆"
  }],
  "has_report": false
}
```

### 本地预览

由于页面需要用 `fetch()` 加载 JSON 和 MD 文件，**不能直接双击打开 HTML**（浏览器会阻止 `file://` 协议的本地文件读取）。

在项目目录启动一个简易 HTTP 服务器：

```bash
cd market-daily
python3 -m http.server 8000
```

然后访问：
- 产业链图：`http://localhost:8000/diagram002.html`
- 某家公司：`http://localhost:8000/company/?ticker=600183.SS`

### 上线到 GitHub Pages

在 GitHub 仓库 Settings → Pages：
- Source: Deploy from a branch
- Branch: main (或你用的分支), folder: / (root)

上线后的访问地址形如：
- `https://your-username.github.io/market-daily/diagram002.html`
- `https://your-username.github.io/market-daily/company/?ticker=600183.SS`

## 将来可以扩展的模块（MVP 之后）

根据你之前的选择，MVP 版本先不做这些，但 JSON 里已经预留了字段，将来加很容易：

- **财务速览表**：在 JSON 里加 `financials` 字段，模板页读取后渲染表格
- **上下游客户/供应商图**：在 JSON 里加 `relationships` 字段
- **业绩/公告时间线**：在 JSON 里加 `timeline` 数组
- **实时股价图**：复用你 Market Daily 的 yfinance 脚本，生成 JSON 数据，模板页用 SVG sparkline 渲染

## 常见问题

**Q：为什么有些公司点进去没报告？**
A：正常。你没写过报告的公司会显示"深度报告整理中"。慢慢积累，能够做到写多少展示多少。

**Q：为什么有些公司的链接在图里出现了多次？**
A：因为有些公司跨多个产业链环节（如南亚塑胶 1303.TW 既做铜箔也做 CCL），或者在"小结"段落里被引用。无论从哪点进去，都会跳到同一个公司页面，页面上会展示所有产业链位置。

**Q：我可以用 Obsidian 写这些 .md 吗？**
A：可以。`reports/` 目录就是一个纯 Markdown 文件夹，Obsidian / Typora / VS Code 都能直接打开。内部链接（如链接到另一家公司）建议用相对路径：`[沪电股份](./002463_SZ.md)`。

**Q：图里的实时股价热力图还能用吗？**
A：完全没动它，继续用。这次改动只影响每家公司的详情链接。
