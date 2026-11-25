# DIC4 — ICEIB 2027 IEEE LaTeX 範例論文與自動化部署紀錄

本專案記錄並保存從 **ICEIB 2027 IEEEtran 起始範本**出發，透過 AI 代理（Antigravity + `chrome-devtools` MCP）自動填入真實論文內容、完成 **Overleaf 線上編譯**、錄製操作過程，並匯出完整流程與可複用 Agent SOP 的全套成果。

---

## 相關連結

- **GitHub Repository**：https://github.com/hidegonzalez/DIC4
- **Overleaf 專案（`pdfLaTeX` / TeX Live 2026，0 錯誤編譯通過）**：https://www.overleaf.com/project/6b06d049588b968a8e53cf8d
- **完整流程、排錯紀錄、Agent SOP 與對話匯出**：[conversation_export.md](./conversation_export.md)
- **Overleaf 自動建立與編譯操作錄影**：[overleaf_upload_recording.mp4](./overleaf_upload_recording.mp4)

---

## 專案目錄結構

```text
DIC/
├── ICEIB2027-IEEE/                  # 已填入 MobileNetV3 範例內容的模組化 IEEEtran 專案
│   ├── main.tex                     # 主文件（\documentclass[conference]{IEEEtran}）
│   ├── references.bib               # BibTeX 文獻庫（Howard et al. 2019, Sandler et al. 2018）
│   ├── sections/                    # 摘要與第 I–V 節（00_abstract ~ 05_conclusion）
│   ├── tables/comparison.tex        # ImageNet Top-1 準確率與參數量／MAdds 比較表
│   └── figures/README.md            # 架構圖放置說明（預設顯示佔位框）
├── ICEIB2027-IEEE.zip               # 原始空白起始範本壓縮檔
├── ICEIB2027-IEEE-MobileNetV3.zip   # 已填入 MobileNetV3 內容的 Overleaf 上傳用壓縮檔
├── overleaf_upload_recording.mp4    # 瀏覽器代理於 Overleaf 建檔與編譯之完整錄影
├── openspec/                        # OpenSpec 規範驅動文件（project.md, specs/, changes/）
├── conversation_export.md           # 完整流程總覽、意外排錯、Agent SOP 與完整對話紀錄
└── README.md                        # 本專案說明文件
```

---

## 論文範例內容說明

- **參考論文**：
  - Andrew Howard et al., *"Searching for MobileNetV3"*, ICCV 2019 (`10.1109/ICCV.2019.00140`)
  - Mark Sandler et al., *"MobileNetV2: Inverted Residuals and Linear Bottlenecks"*, CVPR 2018
- **注意**：`ICEIB2027-IEEE/` 內的文章與數據僅作為範本展示用途，皆引用自上述已發表論文之公開結果；若用於正式投稿，請替換為作者自身之研究方法與實測數據。

---

## 重點歷程與避坑摘要

1. **自動化環境建置**：安裝 Google Chrome（改用 `curl.exe` 下載官方安裝程式避開 `winget` 卡住與 `msstore` 逾時）、安裝 `Chrome DevTools` 插件與 Node.js LTS（v26.13.1），並於 `~/.gemini/config/mcp_config.json` 設定 `chrome-devtools-mcp@latest --autoConnect`。
2. **Overleaf 部署替代方案**：因 `chrome-devtools` MCP 的 `upload_file` 受工作區路徑限制無法選取本機 `.zip`，改由瀏覽器代理建立 Overleaf **Blank Project** 並直接在網頁編輯器逐檔填入 9 個 `.tex`／`.bib` 檔案，順利通過 `pdfLaTeX` 編譯。
3. **GitHub 推送分工**：由瀏覽器代理透過 Chrome 建立空白 `DIC4` Repository，再於本機透過 `git push -u origin main` 一次推送所有檔案。

詳細步驟、意外排除與可讓其他 Agent 直接照抄執行的 SOP，請參閱 [conversation_export.md](./conversation_export.md)。
