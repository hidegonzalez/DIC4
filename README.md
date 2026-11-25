# DIC4 — ICEIB 2027 IEEE LaTeX 範例論文與 OpenSpec 自動化部署專案

本專案採用 **OpenSpec**（Spec-Driven Development）規範架構整理，完整保存從 **ICEIB 2027 IEEEtran 起始範本**出發，透過 AI 代理（Antigravity + `chrome-devtools` MCP）自動填入真實論文內容、部署至 **Overleaf 線上編譯**、錄製瀏覽器操作過程，並匯出完整排錯與可複用 Agent SOP 的全套成果。

---

## 專案連結

- **GitHub Repository**：https://github.com/hidegonzalez/DIC4
- **Overleaf 專案（`pdfLaTeX` / TeX Live 2026，0 錯誤編譯通過）**：https://www.overleaf.com/project/6b06d049588b968a8e53cf8d
- **OpenSpec 規範入口**：[openspec/project.md](./openspec/project.md) ｜ [openspec/AGENTS.md](./openspec/AGENTS.md)
- **完整流程、排錯紀錄與對話匯出**：[conversation_export.md](./conversation_export.md)
- **Overleaf 自動建立與編譯操作錄影**：[overleaf_upload_recording.mp4](./overleaf_upload_recording.mp4)

---

## OpenSpec 目錄與專案結構

```text
DIC4/
├── openspec/                                  # OpenSpec 規範驅動文件
│   ├── project.md                             # 專案技術棧、規範與全域約束
│   ├── AGENTS.md                              # 給 AI Agent 照抄執行的標準作業指示（SOP）
│   ├── specs/                                 # 系統能力與行為規範（Source of Truth）
│   │   ├── latex-paper-pipeline/spec.md       # LaTeX 論文填入與 ZIP 打包規格
│   │   ├── chrome-mcp-setup/spec.md           # Chrome / Node.js / MCP 環境建置規格
│   │   ├── overleaf-deployment/spec.md        # Overleaf 空白專案替代部署與編譯規格
│   │   └── github-sync/spec.md                # GitHub Repo 建立與 Git CLI 同步規格
│   └── changes/
│       └── archive/
│           └── 2026-11-25-iceib2027-mobilenetv3-automation/
│               ├── proposal.md                # 變更提案與範圍界定
│               └── tasks.md                   # 已完成任務清單（All Checked）
├── ICEIB2027-IEEE/                            # 已填入 MobileNetV3 範例內容的 IEEEtran 專案
│   ├── main.tex                               # 主文件（\documentclass[conference]{IEEEtran}）
│   ├── references.bib                         # BibTeX 文獻庫
│   ├── sections/                              # 摘要與第 I–V 節（00_abstract ~ 05_conclusion）
│   ├── tables/comparison.tex                  # ImageNet Top-1 準確率與參數量／MAdds 比較表
│   └── figures/README.md                      # 架構圖放置說明
├── ICEIB2027-IEEE.zip                         # 原始空白起始範本壓縮檔
├── ICEIB2027-IEEE-MobileNetV3.zip             # 已填入 MobileNetV3 內容的 Overleaf 上傳用壓縮檔
├── overleaf_upload_recording.mp4              # 瀏覽器代理於 Overleaf 建檔與編譯之完整錄影
├── conversation_export.md                     # 完整流程、意外排錯、Agent SOP 與全對話紀錄
├── .gitignore                                 # 忽略 debug.log 與 LaTeX 編譯暫存檔
└── README.md                                  # 本專案說明文件
```

---

## 論文範例內容說明

- **引用論文**：
  - Andrew Howard et al., *"Searching for MobileNetV3"*, ICCV 2019 (`10.1109/ICCV.2019.00140`)
  - Mark Sandler et al., *"MobileNetV2: Inverted Residuals and Linear Bottlenecks"*, CVPR 2018
- **注意**：`ICEIB2027-IEEE/` 內的文字與比較數據僅作範本展示用途，皆引自上述已發表論文；正式投稿時請替換為作者自身之研究方法與實測數據。
