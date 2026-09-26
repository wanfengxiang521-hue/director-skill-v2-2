# 导演 Skill V2.2

把脚本、分镜或表达简报转成可执行的导演方案。调用名：`$director-skill-v2-2`。

## 能力

表达目标与视觉隐喻、人物调度、机位与运镜、构图与焦点、光色、声音、剪辑、时长和连续性。主线为：表达目标 → 可感知关系 → 行为或声画组织 → 摄影视点 → 声音与剪辑完成感受。

## 安装与使用

下载本仓库，将完整目录命名为 `director-skill-v2-2`，放入你的 Codex skills 目录（通常是 `~/.codex/skills/`），保留 `SKILL.md`、`agents/` 和 `references/` 的相对结构。

示例：

> 使用 $director-skill-v2-2，为一个10秒竖屏短片设计逐镜方案，表达忙碌后重新拥有自己的空间。请给出机位、运镜、焦点、声音与剪辑。

本仓库可独立用于导演思路与分镜。最终模型提示词编译依赖另外安装的 `prompt-skill`；本仓库不包含该技能，不直接生成视频。

## 文件

- [SKILL.md](SKILL.md)：入口与工作流。
- [学习方法](references/learned-methods.md)：方法的适用范围和来源。
- [导演合同](references/director-lock-schema.md)：DIRECTOR_LOCK v1，Codex 兼容结构1.3。
- [来源说明](references/provenance.md)与[上游许可证](references/upstream-licenses.md)：保留原作者署名及对应许可证，未将不同来源统一改为单一授权。

## 验证边界

已进行 Skill 结构校验、本地引用检查和三类文字导演方案验证；不代表实际视频生成、观众理解或商业效果已经验证。

