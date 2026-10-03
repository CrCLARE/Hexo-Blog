# CrCLARE Hexo 博客

> [CrCLARE 工作室博客](https://blog.crclare.top) 的源码仓库。

本仓库托管 CrCLARE 工作室博客的 Hexo 源码，包括配置文件、主题覆盖、Markdown 文章以及 CI/CD 工作流。

站点自动构建并部署。每次推送到 `main` 分支都会触发 GitHub Actions，自动安装依赖、生成静态文件并发布。

---

## 🔧 技术栈

| 组件 | 选择 |
| --- | --- |
| 静态站点生成器 | [Hexo](https://hexo.io/) |
| 主题 | [Solitude](https://github.com/everfu/hexo-theme-solitude)（Apache-2.0） |
| 在线管理后台 | [Qexo](https://github.com/am-abudu/Qexo) |
| CI/CD | GitHub Actions |
| 托管 | GitHub Pages / Vercel |

---

## 📁 项目结构

```

Hexo-Blog/
├── .github/workflows/     # CI/CD 流水线
├── source/
│   ├── _posts/            # 博客文章（Markdown）
│   └── _data/             # 主题数据覆盖
├── _config.yml            # Hexo 主配置
├── _config.solitude.yml   # Solitude 主题配置
├── package.json
└── README.md

```

---

## 🚀 本地开发

需要 **Node.js 20+** 和 **Git**。

```bash
git clone https://github.com/CrCLARE/Hexo-Blog.git
cd Hexo-Blog
npm install
npm run server    # 访问 http://localhost:4000
```

仅构建：

```bash
npm run clean && npm run build
```

生成的静态文件位于 public/ 目录。

---

📝 写作

文章位于 source/_posts/ 目录下，每个文件都是带 YAML front matter 的标准 Markdown。

你也可以使用 Qexo 作为在线编辑器——它会直接提交到本仓库，随后自动触发部署流水线。

---

🔐 许可证

本博客的源码（配置文件、脚本和 Markdown 文章）采用 MIT 许可证。

本博客使用 Solitude 主题 作为外部依赖，该主题采用 Apache License 2.0 许可。主题源码并未包含在本仓库中。

---

🌐 相关链接

· 博客：https://blog.crclare.top
· 工作室：https://crclare.top
· 文档：https://docs.crclare.top
· 主项目（Chronos Seal）：https://github.com/CrCLARE/Chronos-Seal

---

Made with ❤️ by CLARE-XHL · CrCLARE Studio
