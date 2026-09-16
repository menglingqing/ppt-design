# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## 项目目的

本仓库用于沉淀 PPT 设计资产并产出高质量的 HTML/CSS 网页幻灯片：

- `references/` — 用户提供的优秀 PPT 案例（PDF、PPTX、截图等）及对应的分析笔记（`notes/` 下的 Markdown）
- `prompts/` — 沉淀的 PPT 设计提示词，每个提示词一个 Markdown 文件
- `slides/` — 每次产出的幻灯片项目，**每个任务一个独立子目录**（如 `slides/2026-q3-review/`）

## 工作流程

1. 用户拿来一份优秀 PPT 时：存入 `references/`，并在 `references/notes/` 写一份分析笔记，提炼其版式、配色、字体、图表风格等可复用的设计决策。
2. 用户给出口头或文字的设计要求时：先确认是否有可复用的 `references/` 案例或 `prompts/` 提示词，有则先读取再动手。
3. 产出幻灯片时：在 `slides/` 下新建子目录，用 HTML/CSS 实现。

## HTML 幻灯片约定

- 单文件优先：每个幻灯片项目以 `index.html` 为入口，CSS 内联在 `<style>` 中，避免构建步骤，浏览器直接打开即可。
- 每页幻灯片是一个 `<section class="slide">`，尺寸固定为 **1280×720**（16:9），居中显示。
- 必须支持打印导出 PDF：`@page { size: 1280px 720px; margin: 0; }`，每个 `.slide` 加 `page-break-after: always`。
- 中文字体栈优先使用系统字体（如 `"PingFang SC", "Microsoft YaHei", sans-serif`），不依赖外部字体服务。
- 图片等静态资源放在该项目的 `assets/` 子目录内，使用相对路径引用。
- 需要翻页交互时再加少量原生 JS（键盘 ←/→ 翻页、页码显示），保持无依赖、无构建。

## 图表

在幻灯片中制作任何图表、数据可视化前，先阅读并遵循 `dataviz` skill 的规范（配色公式、图表类型选择、交互规则）。
