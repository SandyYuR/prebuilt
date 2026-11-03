# 中州鹅 Rime 预编译产物

核心定制源码在 [SandyYuR/librime 的 zhongzhou 分支](https://github.com/SandyYuR/librime/tree/zhongzhou)，prebuilder 固定源码与插件、执行四 ABI 编译和原生测试，本仓库保存验证后的产物，输入法固定引用本仓库提交。

当前更新记录见 [librime-update-2026-11-04.json](librime-update-2026-11-04.json)：官方基线更新到 `e930f57b`（包含 #1203），补齐 #1196 的共享用户词典缓存和事务修复。#1232 的最新 rewriter 已包含，仅核对并记录来源，不重复合入。四 ABI 均已重建，5 项源码契约及 172 项原生测试通过；插件和共享依赖保持原固定版本。

每个 `librime/<ABI>/share/rime/source-manifest.json` 记录定制源码与官方基线，`core_patch_mode=committed-source`；`integrated_patches` 是初次迁入源码的历史，`patches` 为空。最新同步记录同时保存三个 PR 的固定来源；插件版本及其补丁、依赖和归档/头文件摘要均独立记录。

初次源码仓库迁移的历史记录见 [librime-source-maintenance-2026-10-21.json](librime-source-maintenance-2026-10-21.json)。根目录 `toolchain-versions.json` 继续描述未重建的共享依赖基线；当前 librime 的来源以逐 ABI 清单为准。此仓库包含的其他历史组件不代表当前 APK 会链接它们。
