# Program Diagram for Rhino 8 · Public Edition

Turn a Rhino 8 massing model into a complete, layered set of Illustrator program diagrams in one export:
site plan, floor plans, sections, elevations, site / stacked / exploded axons, program chart and pie.

把 Rhino 8 体块模型一键输出成整套分层的 Illustrator 分析图：总平面、各层平面、剖面、立面、场地 / 叠合 / 爆炸轴测、
面积图和饼图。

By Chunya Wu · Copyright © 2026 Chunya Wu. All rights reserved. Free for study and personal projects; please do not
re-upload or sell this package. 仅供学习和个人项目免费使用，请勿二次上传或售卖。

**Download · 下载**：[`download/ProgramDiagram-Public-0.9.0.zip`](download/ProgramDiagram-Public-0.9.0.zip)（GitHub 上点开文件 › Download raw file）
**User guide · 使用说明（带出图示例）**：[GUIDE.md](GUIDE.md)

![Site axon](sheets/03_Site_Axon_SITE_AXON.jpg)

## You need · 需要
- Rhino 8 for Windows（Mac 版暂不支持）
- Adobe Illustrator（用来生成 `.ai`；没有也会得到 SVG 预览和一个之后可在 AI 里运行的脚本）
- Text is set in Arial. 文字默认 Arial，可在 AI 里统一换字体。

## Install · 安装（不需要管理员权限）
1. Unzip and keep the whole `ProgramDiagram` folder in your user folder, e.g. `Documents\Rhino\ProgramDiagram`.
   解压，整个 `ProgramDiagram` 文件夹放在用户目录下，里面的文件不要拆开。
2. Drag `ProgramDiagram.rhp` into Rhino 8 and restart Rhino. 把 `ProgramDiagram.rhp` 拖进 Rhino 8，重启 Rhino。
3. Run `ProgramDiagram`. 命令行输入 `ProgramDiagram` 打开面板。
4. Blocked by Windows? Right-click the zip › Properties › tick **Unblock**, unzip again.
   被 Windows 拦截：右键压缩包 › 属性 › 勾选"解除锁定"，重新解压。

## Try the demo model · 先用示例模型跑一遍
Open `examples/Stacked_Library_Demo.3dm` (also inside the zip), import `palettes/palette_oma_scl.json` in step 5, (a simplified stacked-platform library study, in the spirit of Seattle Central
Library) and click through the nine steps; every layer is recognised automatically.
打开 `Stacked_Library_Demo.3dm`（参考西雅图中央图书馆"错动平台"逻辑的简化研究体块，非原设计模型），按 9 步走一遍，
图层会全部自动识别。

## Model your own · 自己的模型怎么建
| What · 内容 | Layer name · 图层名 | Becomes · 识别为 |
|---|---|---|
| One closed solid per room / program · 每个功能一个封闭实体 | `PROGRAM::Reading Room`, `PROGRAM::Office` … | Program colour, area 计面积 |
| Floor slabs · 楼板 | `FLOOR PLATE` / `SLAB` | Levels 楼层（最可靠） |
| Core and stairs · 核心筒、楼梯 | `CORE`, `STAIR` | Links levels in the exploded axon 爆炸轴测中连接上下层 |
| Glass · 玻璃 | `GLASS`, `CW-*` | Plans, elevations, axons |
| Neighbours · 周边建筑 | `CONTEXT` | White context blocks 白色体块 |
| Site · 场地 | `ROAD`, `PARK`, `TREES`, `WATER`, `NC::PLAZA` | Site base 场地底图 |

Program names are matched to the legend (Office, Lab, Reading, Collection / Stacks, Classroom / Studio, Exhibition,
Retail / Cafe, Residential, Parking, Meeting, Lounge, Auditorium …). Unknown names under `PROGRAM::` still work: pick
a colour in step 5. 图层名会自动对应图例；不认识的名字也可以在第 5 步选颜色。

Tip: build masses from the top of one slab to the underside of the next; keep programs from overlapping.
建模提示：体块从楼板顶建到上层板底；不同功能不要重叠。

## The nine steps · 九步
1 Layers 图层角色 › 2 Cleanup 体块清理 › 3 Levels 楼层 › 4 Names 名称与编号 › 5 Colors 配色 ›
6 Sections 剖切线（可选）› 7 Elevations 立面线（可选）› 8 Output 导出 › 9 Check 检查。
Each export goes to a new folder next to the model: `.ai` files, `_preview/*.svg`, `program_areas.csv`.
每次导出在模型旁新建文件夹：`.ai`、SVG 预览、面积表。

## Colour palettes · 配色
The default palette is **Riso** (risograph-ink tints on warm paper). Three more are in `palettes/`:
`palette_nordic_mist`, `palette_bauhaus`, `palette_ink_wash`. Step 5 › **Import scheme JSON…** › pick one ›
re-export: every drawing recolours in place (global swatches).
默认配色 Riso（孔版印刷油墨色）；`palettes/` 里另有北欧雾、包豪斯、水墨三套。第 5 步 Import scheme JSON 选择后重新导出，
所有图纸原位换色。

## Keep editing in Illustrator · 在 AI 里继续画
Draw your own additions on `_MANUAL` or `OVERLAY` layers: re-exports never touch them.
自己加的内容画在 `_MANUAL` / `OVERLAY` 图层，重新导出不会被覆盖。

## Problems · 遇到问题
Send the `WARN` / `ERROR` lines from `export_log.txt` and `illustrator_log.txt` with a screenshot.
把 `export_log.txt` 和 `illustrator_log.txt` 里的 WARN / ERROR 行连同截图发给作者。
