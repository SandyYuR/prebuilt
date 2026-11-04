# 中州鹅 Rime 预编译产物

核心定制源码在 [SandyYuR/librime 的 zhongzhou 分支](https://github.com/SandyYuR/librime/tree/zhongzhou)。prebuilder 固定源码与插件、执行四 ABI 编译和原生测试，本仓库保存验证后的产物，输入法固定引用本仓库提交。

当前更新记录见 [librime-update-2026-11-04-userdict.json](librime-update-2026-11-04-userdict.json)：源码固定为 `6af3692f`，先变基到官方 `0e8ee404`，再依次重放定制补丁；补充上游空词典迭代器修复，并修复同库多个 Memory 的同次上屏学习事务被提前提交、立即退格无法撤销的问题。事务按输入上下文与上屏轮次协调，不要求修改万象方案或 Lua 插件。已有 #1203、#1196、#1232 改动保留，没有重复合入。

源码正式分支完整 Commit CI 的 14 项检查全部通过。四 ABI 已重建，199 项原生测试及 5 项源码契约检查通过；逐项核验归档摘要、所有对象文件的 CPU 架构、插件及补丁摘要、共享依赖和公共 C API 头文件，插件与依赖保持原固定版本。

每个 `librime/<ABI>/share/rime/source-manifest.json` 记录定制源码与官方基线，`core_patch_mode=committed-source`；`integrated_patches` 是初次迁入源码的历史，`patches` 为空。更新记录同时保存上游 PR 的固定来源；插件版本及其补丁、依赖和归档/头文件摘要均独立记录。

上一次同步记录保留在 [librime-update-2026-11-04.json](librime-update-2026-11-04.json)，初次源码仓库迁移记录见 [librime-source-maintenance-2026-10-21.json](librime-source-maintenance-2026-10-21.json)。根目录 `toolchain-versions.json` 继续描述未重建的共享依赖基线；当前 librime 的来源以逐 ABI 清单为准。此仓库包含的其他历史组件不代表当前 APK 会链接它们。

发布顺序：librime 的完整 Commit CI 通过后推进 prebuilder，核验四 ABI 和原生测试，再更新本仓库及输入法引用。旧的源码标签保留为回退点，不随分支变基移动。
