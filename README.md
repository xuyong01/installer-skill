# SkillHub Installer Skill

这是一个给 Agent 读取的 SkillHub 安装指导文档。用户只需要让 Agent 阅读仓库里的
`installer.skill.md`，再给出要安装的 SkillHub 坐标即可。

## Raw URL

发布到 GitHub 后使用这个地址：

```text
https://raw.githubusercontent.com/xuyong01/installer-skill/main/installer.skill.md
```

## 使用方式

把下面这句话发给 Codex 或 Claude Code：

```text
请阅读 https://raw.githubusercontent.com/xuyong01/installer-skill/main/installer.skill.md，然后帮我安装 @namespace/skill-slug
```

Agent 会读取 `installer.skill.md`，把 `@namespace/skill-slug` 转成当前
`@astron-team/skillhub` CLI 支持的参数形式，再安装到当前项目。

## 示例转换

用户输入：

```text
@clink-bot-skills/simulate-clink-order
```

Codex 会执行：

```bash
# 安装 clink-bot-skills 命名空间下的 simulate-clink-order 到当前项目的 Codex skills 目录，并输出 JSON 结果
npx @astron-team/skillhub@latest install simulate-clink-order --namespace clink-bot-skills --agent codex --scope project --registry https://skillhub.clinkpay.team --json
```

Claude Code 会使用同样的参数，但把 `--agent codex` 换成 `--agent claude-code`。

## 发布

如果本地已经提交但还没推送，配置好 GitHub 凭据后运行：

```bash
# 推送本地 main 分支到 xuyong01/installer-skill，让 Raw URL 可以访问最新 installer.skill.md 和 README.md
git push origin main
```
