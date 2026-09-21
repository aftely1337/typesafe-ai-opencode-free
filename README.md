# TypeSafe AI OpenCode Free

<p align="center">
    <a href="https://linux.do"><img src="https://shorturl.at/ggSqS" alt="LINUX DO" /></a>
</p>

这是 TypeSafe AI 官方 `typesafe-ai` Codex skill 的 OpenCode Zen 免费层传输变体。
它保留了官方 skill 关于 System One 开发的指导，同时提供一个小型 helper，用于调用
OpenCode Zen 的 `jev-1.13-free` 模型。

[English README](README.en.md)

## 内容

- `SKILL.md`：官方 TypeSafe skill 的完整指导，仅增加了一段本地说明，将实际的
  System One 请求交给 helper 处理。
- `bin/systemone-call`：无第三方依赖的 Python 3 命令行 helper，用于将标准的
  System One 请求体发送到 OpenCode Zen。
- `LICENSE`：上游 TypeSafe skill 随附的 MIT 许可证。

## 安装

克隆仓库后，将内容复制到 Codex skills 目录：

```bash
git clone https://github.com/aftely1337/typesafe-ai-opencode-free.git
mkdir -p ~/.codex/skills
cp -R typesafe-ai-opencode-free ~/.codex/skills/
```

重启 Codex 或开启一个新会话，让它发现这个 skill。

## 使用传输 helper

helper 从标准输入读取 System One 请求体。默认使用 OpenCode Zen 的 System One
端点和 `jev-1.13-free`，不需要安装第三方 Python 包。

```bash
echo '{
  "questions": {
    "smoke": {
      "type": "noul",
      "question": "传输是否正常工作？",
      "instructions": "返回该请求正常工作的概率。"
    }
  }
}' | ~/.codex/skills/typesafe-ai-opencode-free/bin/systemone-call --state ''
```

需要时可通过环境变量配置端点、凭证或默认模型：

```bash
export TYPESAFE_BASE_URL="https://opencode.ai/zen/v1/systemone"
export TYPESAFE_DEFAULT_MODEL="jev-1.13-free"
export TYPESAFE_API_KEY="public"
```

完整的调用格式见 `bin/systemone-call --help`。生产集成前请阅读 TypeSafe 实时文档；
模型和免费层可用性由相应服务提供方决定，可能发生变化。

## 致谢与来源

skill 的设计指导和 `SKILL.md` 来自官方
[TypeSafe AI skills 仓库](https://github.com/typesafe-ai/skills)。

`bin/systemone-call` 使用的 OpenCode 请求传输行为参考了
[opencode2api](https://github.com/jasonxu114514/opencode2api)。本仓库不包含、也不
分发该项目的源代码。

这是独立的社区变体，并非 TypeSafe AI 或 OpenCode 的官方项目。请按照适用条款和
服务限制使用 OpenCode Zen。

## 许可证

本仓库使用 MIT 许可证。TypeSafe AI 的原始版权声明和本地新增内容的版权声明均保留在
[LICENSE](LICENSE) 中。
