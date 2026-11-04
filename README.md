# 实验03：GitHub Action 和 GitHub Pages 使用

本项目对应《实验03-Github Action和GitHub Pages使用》文档，包含两部分内容：

1. **GitHub Action 使用**：Python 单元测试的自动化（`calculator.py` + `test_calculator.py` + 工作流 `python-test.yml`）。
2. **GitHub Pages 使用**：使用 MkDocs 构建静态文档站点，并通过 GitHub Actions 自动部署（`docs/` + `mkdocs.yml` + 工作流 `deploy.yml`）。

## 项目结构

```
github-actions-pages-demo/
├── calculator.py            # 待测试的 Python 模块（add、multiply）
├── test_calculator.py       # pytest 单元测试
├── .github/
│   └── workflows/
│       ├── python-test.yml  # 单元测试自动化工作流
│       └── deploy.yml       # MkDocs 自动部署工作流
├── docs/                    # 存放 Markdown 文档（MkDocs 源文档）
│   ├── index.md             # 主页
│   ├── about.md             # 关于页面
│   ├── guide.md             # 使用指南
│   └── api.md               # API 参考
├── mkdocs.yml               # MkDocs 配置文件
├── requirements.txt         # Python 依赖清单
└── README.md                # 项目说明
```

## 本地运行

### 1. 运行单元测试

```bash
pip install pytest
pytest -v
```

### 2. 本地构建 MkDocs 文档

```bash
pip install mkdocs-material
mkdocs build      # 生成静态文件到 site/ 目录
mkdocs serve      # 本地预览 http://127.0.0.1:8000
```

## 推送到 GitHub

```bash
# 1. 将所有文件添加到暂存区
git add .
# 2. 提交代码
git commit -m "初始化MkDocs项目并配置GitHub Actions"
# 3. 推送到GitHub的main分支
git push origin main
```

推送后，GitHub Actions 会自动运行单元测试，并在 `docs/` 或 `mkdocs.yml` 变化时构建并部署文档站点到 GitHub Pages。
