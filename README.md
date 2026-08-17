# Semi Hub

**AI 硬件与半导体供应链研究知识库** · _AI Hardware & Semiconductor Supply Chain Research_

CCL · PCB · IC Substrate · CoWoS · Optical Communication · Glass Substrate

> 围绕 AI 硬件上游的结构化研究知识库：产业链图谱、公司深度笔记、关键环节的持续跟踪。
>
> _A structured research hub covering the upstream of AI hardware — supply-chain maps, company deep dives, and ongoing coverage of key nodes._

## 在线地图 · Live Maps

- 🧠 [超节点产业链地图 · SuperNode Hub](https://daisypku.github.io/semi-hub/supernode/)
- 🧱 [CCL / PCB / 封装 / 光通信产业链图谱](https://daisypku.github.io/semi-hub/diagram002.html)

SuperNode Hub 是 AI 硬件研究图谱的顶层系统入口；原有产业链图谱作为 PCB、CCL、封装与光互联子地图继续维护。

---

## 覆盖范围 · Coverage

**82 家公司** · 82 companies across **6 major layers** · 遍及 **9 个国家与地区**

| 环节 · Layer | 公司数 · Count |
|---|---|
| STEP 0 · CCL 三大原材料 _CCL raw materials (copper foil · glass cloth · resin)_ | 28 |
| STEP 1 · 覆铜板制造 _CCL manufacturing_ | 9 |
| STEP 2 · PCB · _printed circuit boards_ | 12 |
| STEP 3 · IC 载板 · _IC substrate (ABF / BT)_ | 12 |
| STEP 3.5 · CoWoS 先进封装 · _advanced packaging_ | 工艺专题 / _process overview_ |
| STEP 4 · 光通信 · _optical communication_ | 24 |
| STEP 5 · 玻璃基板 · _glass substrate (next-gen)_ | 5 |

**地区分布 · Geographic distribution**

🇨🇳 34　·　🇯🇵 18　·　🇹🇼 15　·　🇺🇸 13　·　🇰🇷 4　·　🇦🇹 3　·　🇭🇰 1

---

## 已发布深度研究 · Published deep dives

| Ticker | 公司 · Company | 环节 · Layer | 状态 · Status |
|---|---|---|---|
| 600183.SS | 生益科技 _Shengyi Technology_ | STEP 1 · CCL | ✅ 已发布 / _Published_ |

_更多公司深度笔记持续更新中。_ · _More deep dives being added._

---

## 使用方式 · How to use

从[产业链图谱](https://daisypku.github.io/semi-hub/diagram002.html)入口进入，点击任意公司跳转至其详情页：

_Enter from the [supply chain map](https://daisypku.github.io/semi-hub/diagram002.html) and click any company to open its dedicated page:_

- **产业链定位标签** · Supply chain position tags
- **一句话定位** · One-line positioning
- **Yahoo Finance / 同花顺 / 东方财富 F10** 等外部快捷入口 · External links to financial portals
- **深度研究笔记**（如已发布）· Deep-dive notes _(when available)_

---

## 仓库结构 · Repository structure

```
semi-hub/
├── diagram002.html                      CCL / PCB / packaging / optics sub-map
├── supernode/
│   ├── index.html                       超节点产业链地图 · SuperNode Hub
│   └── data/                            拓扑、公司身份证与价值地图数据
└── company/
    ├── index.html                       公司详情页模板 · Company page template
    ├── HOWTO.md                         维护手册 · Maintenance guide
    └── data/
        ├── companies.json               82 家公司基础信息 · Company metadata
        └── reports/
            └── {ticker_slug}.md         深度笔记 · Deep dive notes
```

**技术栈 · Stack**：纯静态站点 (HTML + JSON + Markdown)，GitHub Pages 托管。
_Fully static site — HTML + JSON + Markdown, hosted on GitHub Pages._

---

## 更新记录 · Changelog

- **2026-08-17** · SuperNode Hub v0.4：02 改为左侧八环节/右侧详情布局；NVL576 增加 S1 官方事实与 S2 公开研究观察分层
- **2026-08** · SuperNode Hub v0.4：产业链导航、系统结构对比、价值环节与公司身份证顺向联动
- **2026-08** · SuperNode Hub v0.1–v0.3：拓扑实验室、公司身份证与价值地图上线
- **2026-04** · 公司详情页系统上线，覆盖 82 家公司 · _Company-level pages launched, 82 firms indexed_
- **2026-04** · 产业链图谱 v1 · _Supply chain map v1_

---

## 免责声明 · Disclaimer

本仓库内容为个人研究整理，不构成任何投资建议。引用第三方数据均已在原始页面标注来源。

_This repository contains personal research notes. It does not constitute investment advice. All third-party data citations are attributed on their respective pages._

