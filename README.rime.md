# 中州鹅 Rime 预编译产物

核心定制源码在 [SandyYuR/librime 的 zhongzhou 分支](https://github.com/SandyYuR/librime/tree/zhongzhou)，prebuilder 固定源码与插件、执行四 ABI 编译和原生测试，本仓库保存验证后的产物，输入法固定引用本仓库提交。

当前更新记录见 [librime-update-2026-11-04.json](librime-update-2026-11-04.json)：官方基线更新到 `e930f57b`（包含 #1203），补齐 #1196 的共享用户词典缓存和事务修复。#1232 的最新 rewriter 已包含，仅核对并记录来源，不重复合入。源码先变基到官方基线，再依次重放仓库特有补丁；#1196 仅补齐尚缺少的有效增量，作为一个提交保留，#1232 仍为独立补丁，格式修复归入对应提交。四 ABI 均已重建，5 项源码契约及 172 项原生测试通过；插件和共享依赖保持原固定版本。

每个 `librime/<ABI>/share/rime/source-manifest.json` 记录定制源码与官方基线，`core_patch_mode=committed-source`；`integrated_patches` 是初次迁入源码的历史，`patches` 为空。最新同步记录同时保存三个 PR 的固定来源；插件版本及其补丁、依赖和归档/头文件摘要均独立记录。

初次源码仓库迁移的历史记录见 [librime-source-maintenance-2026-10-21.json](librime-source-maintenance-2026-10-21.json)。根目录 `toolchain-versions.json` 继续描述未重建的共享依赖基线；当前 librime 的来源以逐 ABI 清单为准。此仓库包含的其他历史组件不代表当前 APK 会链接它们。

发布顺序：librime 的完整 Commit CI 通过后合并 prebuilder，核验四 ABI 和原生测试，再更新本仓库及输入法引用。旧的源码标签保留为回退点，不随分支变基移动。

本次 Android 更新的源码 CI 已通过 13 项检查，macOS ARM 因 GitHub 运行器容量不足未执行，仍保留重试。按本次发布要求，依据已通过的四 ABI、172 项原生测试及 5 项源码契约检查推进，不将该 macOS 任务记录为通过。
