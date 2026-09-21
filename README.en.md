# TypeSafe AI OpenCode Free

<p align="center">
    <a href="https://linux.do"><img src="https://shorturl.at/ggSqS" alt="LINUX DO" /></a>
</p>

An OpenCode Zen free-tier transport variant of TypeSafe AI's `typesafe-ai`
Codex skill. It preserves the official skill's guidance for building with
System One, while providing a small helper for calls to OpenCode Zen's
`jev-1.13-free` model.

[中文说明](README.md)

## Contents

- `SKILL.md`: the official TypeSafe skill guidance, with a short local note
  that directs real System One calls through the helper.
- `bin/systemone-call`: a dependency-free Python 3 command-line helper for
  posting the canonical System One request body to OpenCode Zen.
- `LICENSE`: the MIT license distributed with the upstream TypeSafe skill.

## Install

Clone the repository, then copy its contents into your Codex skills directory:

```bash
git clone https://github.com/aftely1337/typesafe-ai-opencode-free.git
mkdir -p ~/.codex/skills
cp -R typesafe-ai-opencode-free ~/.codex/skills/
```

Restart Codex or start a new session so it can discover the skill.

## Use the transport helper

The helper reads a System One request body from standard input. It defaults to
the OpenCode Zen System One endpoint and `jev-1.13-free`; no third-party Python
packages are required.

```bash
echo '{
  "questions": {
    "smoke": {
      "type": "noul",
      "question": "Is the transport working?",
      "instructions": "Return the probability that the request is working."
    }
  }
}' | ~/.codex/skills/typesafe-ai-opencode-free/bin/systemone-call --state ''
```

Configure the endpoint, API credential, or default model through environment
variables when needed:

```bash
export TYPESAFE_BASE_URL="https://opencode.ai/zen/v1/systemone"
export TYPESAFE_DEFAULT_MODEL="jev-1.13-free"
export TYPESAFE_API_KEY="public"
```

Run `bin/systemone-call --help` for the full invocation schema. Read the live
TypeSafe documentation before building a production integration; the model and
free-tier availability are controlled by their respective providers and can
change.

## Attribution

The skill's design guidance and `SKILL.md` originate from the official
[TypeSafe AI skills repository](https://github.com/typesafe-ai/skills).

The OpenCode request-transport behavior used by `bin/systemone-call` was
studied with reference to [opencode2api](https://github.com/jasonxu114514/opencode2api).
This repository does not vendor or distribute source code from that project.

This is an independent community variant, not an official TypeSafe AI or
OpenCode project. Use OpenCode Zen in accordance with its applicable terms and
service limits.

## License

The repository is MIT licensed. TypeSafe AI's original copyright notice remains
in [LICENSE](LICENSE) alongside the copyright notice for the local additions.
