# AI coding agents

Let an AI coding agent install your app on a real phone, open it, and check that it starts without errors.

## Add the skill

Setup offers this when it finds an agent on your computer. To add it yourself:

```bash
droidsuite skill                    # every project on this computer
droidsuite skill --project          # only this project; commit it to share
droidsuite skill --dir <folder>     # an agent that reads skills from somewhere else
```

Run it again after updating DroidSuite, or after adding an agent.

## Which agents

| Agent | Status |
|---|---|
| **Claude Code** | Tested from install to launch on a real phone |
| **Codex** | Confirmed to find the skill |
| **OpenCode** | Confirmed to find the skill |
| **Antigravity** | Confirmed to find the skill |
| **Gemini CLI, Cursor, GitHub Copilot, Windsurf, Qwen Code, Amp** | Installed to the folders they're documented to read. Not tested yet. |

Using one of these? [Tell us how it went](https://github.com/Mahmoud-Helmy-m/droidsuite/issues/new/choose).

## Try it

Ask your agent, in your Android project:

> Install the debug build on my phone, open it, and tell me whether it starts without errors.

Before that, the phone needs [Debug over Wi-Fi](debugging.md) set up once.

## What stays with you

The skill tells agents to leave these to you:

- Security prompts, such as Play Protect, install approvals and **Allow** on a Receive request
- Anything asking for a PIN or password
- Uninstalling apps or clearing their data

It also tells them to read only the logs of the app being tested, and not to list the apps on your phone. These are instructions to the agent, so check what your agent is doing, as you would with any tool that can reach your phone.

> [!NOTE]
> **Xiaomi, Redmi, POCO:** each install through adb shows a prompt lasting about 10 seconds. The agent will ask you to watch the screen, then install as soon as you reply.

---

**Next:** [Commands](commands.md) · [Privacy and security](privacy.md)
