# 網路課程筆記網站 - 實體層

用 [MkDocs Material](https://squidfunk.github.io/mkdocs-material/) 建立的網路通訊概論實體層課程筆記網站。

## 本機開發與預覽

```bash
# 安裝所需套件
pip install mkdocs-material

# 啟動本地開發伺服器
mkdocs serve
```

啟動後在瀏覽器打開 http://127.0.0.1:8000 即可即時預覽（存檔會自動重新整理）。

## 部署到 GitHub Pages

### 方法一：一行指令手動部署 (最快速)

在專案根目錄下直接執行：

```bash
mkdocs gh-deploy
```

MkDocs 會自動將 `docs/` 編譯為靜態 HTML，並推送到遠端儲存庫的 `gh-pages` 分支。

---

### 方法二：透過 GitHub Actions 自動部署 (推薦)

在專案中建立 `.github/workflows/deploy.yml` 檔案：

```yaml
name: Deploy MkDocs to GitHub Pages

on:
  push:
    branches:
      - main
      - master

permissions:
  contents: write

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4

      - name: Configure Git Credentials
        run: |
          git config user.name github-actions[bot]
          git config user.email 41898282+github-actions[bot]@users.noreply.github.com

      - uses: actions/setup-python@v5
        with:
          python-version: 3.x

      - run: echo "cache_id=$(date --utc '+%V')" >> $GITHUB_ENV
      - uses: actions/cache@v4
        with:
          key: mkdocs-material-${{ env.cache_id }}
          path: .cache
          restore-keys: |
            mkdocs-material-

      - name: Install dependencies
        run: pip install mkdocs-material

      - name: Deploy to GitHub Pages
        run: mkdocs gh-deploy --force
```

之後只要 `git push` 到 GitHub，GitHub Actions 就會自動編譯並部署最新筆記！

## 專案結構

```
network-notes/
├── mkdocs.yml              # 設定檔（含導覽列結構、主題、外掛）
└── docs/
    ├── index.md             # 首頁導覽
    ├── physical-layer/      # 實體層全章筆記
    ├── javascripts/         # MathJax 渲染設定腳本
    └── ai-collaboration.md  # AI 協作與提示詞紀錄
```
