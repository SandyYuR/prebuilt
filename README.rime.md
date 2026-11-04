> **已迁移，停止维护：仅用于历史版本重建。**
>
> 中州鹅当前引擎的 Android 构建、固定依赖和版本发布已集中到 [SandyYuR/librime 的 zhongzhou 分支](https://github.com/SandyYuR/librime/tree/zhongzhou)。输入法直接引用该仓库发布的 Android SDK，当前流程不再使用 prebuilder/prebuilt。
>
> 新流程见 [Android SDK 维护说明](https://github.com/SandyYuR/librime/blob/zhongzhou/downstream/android/README.zh-CN.md) 和 [输入法原生依赖说明](https://github.com/SandyYuR/fcitx5-android/blob/fx-rime-only/native/README.md)。本仓库的提交、标签、源码和产物保留，旧版输入法的固定引用仍可读取。

# 中州鹅 Rime 预编译产物

核心源码维护在 [SandyYuR/librime 的 zhongzhou 分支](https://github.com/SandyYuR/librime/tree/zhongzhou)。prebuilder 固定源码、插件与工具链，本仓库保存四 ABI 产物，输入法固定引用本仓库提交。

当前记录见 [librime-update-2026-11-04.json](librime-update-2026-11-04.json)。源码固定为 `69a934ac`：先变基到官方 `9777cb2f`，再重放 10 个仓库特有提交。官方已包含 #1196 和 #1203，重复的缓存与并行部署补丁不再保留下游实现；#1232、音节选择、忘词刷新、启动指纹及同次上屏事务撤销修复继续保留。

本轮整理只改变来源说明与提交历史，源码、构建和测试文件与已通过 14 项完整 CI 的 `6af3692f` 逐字节一致。重新构建的四 ABI 归档与上一轮验证产物也完全一致；199 项原生测试、5 项源码契约检查通过。已逐项核验归档摘要、全部 ELF 对象架构及源码来源，插件、共享依赖和公共 C API 头文件保持原固定版本。

每个 `librime/<ABI>/share/rime/source-manifest.json` 记录实际构建源码、prebuilder、插件及补丁、依赖和归档/头文件摘要。`core_patch_mode=committed-source`；`integrated_patches` 仅保存初次迁移历史，已由官方覆盖的项目不再重放，`patches` 为空。独有基准工具仍保留，默认不执行性能基准测试。

同库多个 Memory 在一次上屏时共享待提交事务，立即退格可撤销当轮学习，无需修改万象方案或 Lua 插件。初次源码迁移记录保留在 [librime-source-maintenance-2026-10-21.json](librime-source-maintenance-2026-10-21.json)，共享依赖基线仍由 `toolchain-versions.json` 描述。

整理前的仓库历史保留在 `v0-archive-before-upstream-1196-20261104` 标签，已发布标签不移动。
