# 網路課程筆記網站

用 [MkDocs Material](https://squidfunk.github.io/mkdocs-material/) 建立，內容涵蓋實體層與資料連接層。

## 本機開發

```bash
pip install mkdocs-material
mkdocs serve
```

然後打開 http://127.0.0.1:8000 即可即時預覽（存檔會自動重新整理）。

## 部署到 GitHub Pages

```bash
mkdocs gh-deploy
```

會自動把 `docs/` 建置成靜態網站並推到 `gh-pages` 分支。

## 專案結構

```
network-notes/
├── mkdocs.yml              # 設定檔（含導覽列結構）
└── docs/
    ├── index.md             # 首頁
    ├── physical-layer/      # 實體層章節
    └── data-link-layer/     # 資料連接層章節
```

## 待補內容

各頁面中標記 `<!-- TODO: ... -->` 的地方，是建議補充課堂實際內容、圖表、範例的位置。
