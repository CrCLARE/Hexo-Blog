# CrCLARE Hexo Blog

> Source code of the [CrCLARE Studio blog](https://blog.crclare.top).

This repository hosts the Hexo source code for the CrCLARE Studio blog — including configuration files, theme overrides, Markdown articles, and CI/CD workflows.

The site is built and deployed automatically. Every push to `main` triggers GitHub Actions to install dependencies, generate static files, and deploy the output.

---

## 🔧 Tech Stack

| Component | Choice |
| --- | --- |
| Static site generator | [Hexo](https://hexo.io/) |
| Theme | [Solitude](https://github.com/everfu/hexo-theme-solitude) (Apache-2.0) |
| Online admin panel | [Qexo](https://github.com/am-abudu/Qexo) |
| CI/CD | GitHub Actions |
| Hosting | GitHub Pages / Vercel |

---

## 📁 Project Structure

```

Hexo-Blog/
├── .github/workflows/     # CI/CD pipeline
├── source/
│   ├── _posts/            # Blog posts (Markdown)
│   └── _data/             # Theme data overrides
├── _config.yml            # Hexo main config
├── _config.solitude.yml   # Solitude theme config
├── package.json
└── README.md

```

---

## 🚀 Local Development

Requires **Node.js 20+** and **Git**.

```bash
git clone https://github.com/CrCLARE/Hexo-Blog.git
cd Hexo-Blog
npm install
npm run server    # Visit http://localhost:4000
```

To build only:

```bash
npm run clean && npm run build
```

The generated static files live in public/.

---

📝 Writing

Posts live in source/_posts/. Each file is standard Markdown with a YAML front matter block.

You can also use Qexo as an online editor — it commits directly to this repository, which then triggers the deployment pipeline.

---

🔐 License

The source code of this blog (configuration, scripts, and Markdown articles) is licensed under the MIT License.

This blog uses the Solitude theme as an external dependency, which is licensed under the Apache License 2.0. The theme is not included in this repository.

---

🌐 Links

· Blog: https://blog.crclare.top
· Studio: https://crclare.top
· Docs: https://docs.crclare.top
· Main Project (Chronos Seal): https://github.com/CrCLARE/Chronos-Seal

---

Made with ❤️ by CLARE-XHL · CrCLARE Studio
