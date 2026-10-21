# 中州鹅 Rime 预编译产物

核心定制源码在 [SandyYuR/librime 的 zhongzhou 分支](https://github.com/SandyYuR/librime/tree/zhongzhou)，prebuilder 固定源码与插件、执行四 ABI 编译和原生测试，本仓库保存验证后的产物，输入法固定引用本仓库提交。

本次源码仓库迁移记录见 [librime-source-maintenance-2026-10-21.json](librime-source-maintenance-2026-10-21.json)。四 ABI 的 librime.a 与前一固定产物逐字节相同；本轮只更新来源清单，不改变引擎功能或依赖。

每个 librime/<ABI>/share/rime/source-manifest.json 分别记录定制源码与官方基线，core_patch_mode=committed-source；integrated_patches 是迁入源码的历史，patches 为空。插件版本及其补丁、依赖和归档/头文件摘要均独立记录。

根目录 toolchain-versions.json 继续描述未重建的共享依赖基线；本轮 librime 的来源以逐 ABI 清单为准。此仓库包含的其他历史组件不代表当前 APK 会链接它们。
