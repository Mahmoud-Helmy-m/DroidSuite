# droidsuite commands

Run `droidsuite` with nothing after it for an interactive menu. Every command also takes `--help`.

| Command | What it does |
|---|---|
| [`setup`](#setup) | First-run setup: add the DroidSuite icon, get adb ready for Wi-Fi debugging, offer the AI agent skill, show next steps |
| [`serve`](#serve) | Share APKs with your paired phones, push every new build to them, and swap files |
| [`open`](#open) | Open the DroidSuite page, starting the server if it isn't running (what the desktop icon does) |
| [`push`](#push) | Send any files to your paired phones (needs droidsuite serve running) |
| [`send`](#send) | Upload APKs or any files to a phone that has Receive mode open |
| [`get`](#get) | Download the files a phone offers in Receive mode |
| [`devices`](#devices) | List phones that have Receive mode open on this network |
| [`debug`](#debug) | Connect adb to phones with Wireless debugging on (Android Studio, logcat, breakpoints) |
| [`debug setup`](#debug-setup) | Set up Debug over Wi-Fi step by step: turn on, pair, connect (Android 11+) |
| [`debug connect`](#debug-connect) | Connect adb to the IP address & Port shown on the phone |
| [`debug usb`](#debug-usb) | Android 8–10: turn on adb over Wi-Fi through a USB cable, then connect |
| [`debug doctor`](#debug-doctor) | Explain why Debug over Wi-Fi doesn't connect, and what to do |
| [`debug install`](#debug-install) | Install adb (Google's Android SDK Platform-Tools) for droidsuite |
| [`debug path`](#debug-path) | Add adb to your PATH so typing "adb" works in new terminals |
| [`adb`](#adb) | Run adb, even when it isn't on PATH |
| [`shortcut`](#shortcut) | Add a "DroidSuite" icon that starts the server and opens its page |
| [`skill`](#skill) | Teach AI coding agents (Claude Code, Codex, Gemini CLI, Cursor and others) to use droidsuite, in every project |
| [`help`](#help) | Show all commands, or the details of one |

## setup

First-run setup: add the DroidSuite icon, get adb ready for Wi-Fi debugging, offer the AI agent skill, show next steps.

```
droidsuite setup [--yes] [--skip-adb] [--no-shortcut]
```

| Option | Meaning |
|---|---|
| `-y, --yes` | Answer yes to every question (accepts the Platform-Tools license). |
| `--skip-adb` | Don't check or install adb (only needed for Debug over Wi-Fi). |
| `--no-shortcut` | Don't add the DroidSuite icon. |
| `--shortcut` | Add the icon even with no terminal to answer in. The install scripts use this. |

Examples:

```bash
droidsuite setup
```

The install scripts run this for you. Have Node.js and nothing installed yet? npx droidsuite@latest setup installs DroidSuite too. Asks before installing adb, changing PATH or adding the skill; with no terminal to answer in, it skips.

## serve

Share APKs with your paired phones, push every new build to them, and swap files.

```
droidsuite serve [folders or APK files...] [options]
```

| Option | Meaning |
|---|---|
| `--inbox <folder>` | Where files sent from phones are saved (default: Downloads/DroidSuite in your home folder). |
| `--install-via <mode>` | auto (default): when the phone has Wireless debugging connected, builds install through adb, which also works where Android blocks apps from unregistered developers; otherwise through the app. app: always through the app. |
| `--port <n>` | Port to listen on (default 8765; the next free one if it's busy). |
| `--host <ip>` | Address to put in the pairing QR code. Repeat for several. Default: this computer's Wi-Fi/LAN addresses. |
| `--no-mdns` | Don't announce this computer on the network (phones then only use the QR addresses). |
| `--reset` | Make a new pairing token. Every phone has to scan the QR code again. |
| `--open` | Open the page in your browser once the server is running. |
| `--background` | How the DroidSuite icon runs it: no default folder (only the one you chose before), output for a log file. Stop it from the page. Use droidsuite open to start it like the icon does. |

Examples:

```bash
droidsuite serve                       # inside an Android project: watches app/build/outputs/apk
droidsuite serve D:\builds\myapp       # any folder of APKs
droidsuite serve app-release.apk --port 9000
```

Prints a pairing QR code. http://localhost:8765 shows a bigger one, connected phones, builds, a drop zone for sending files, files received from phones, the phone app download, the Debug over Wi-Fi panel, and Phone screen: the phone's screen live, with control (tap, swipe, keys, typing). Phone screen needs a phone connected through adb (Debug over Wi-Fi or USB); it uses Android's own screen recorder and pauses when the tab is hidden. Stop with Ctrl+C.

## open

Open the DroidSuite page, starting the server if it isn't running (what the desktop icon does).

```
droidsuite open
```

Examples:

```bash
droidsuite open
```

Already running on this computer: just opens the page. Otherwise it starts droidsuite serve with the builds folder you chose last (in the menu or on the page), or with none, in the background (no window; its output goes to serve.log in the droidsuite folder), and opens the page. Stop it with Stop on the page.

## push

Send any files to your paired phones (needs droidsuite serve running).

```
droidsuite push <files...> [--port <n>]
```

| Option | Meaning |
|---|---|
| `--port <n>` | Port of the running serve, if you started it with --port (it's found by itself otherwise). |

Examples:

```bash
droidsuite push design.png notes.txt
```

Every phone with Live on gets the files in Downloads/DroidSuite, with a notification to open them. Phones send files back with Share → DroidSuite.

## send

Upload APKs or any files to a phone that has Receive mode open.

```
droidsuite send <files...> [--to <ip[:port]>] [--pin <123456>] [--save]
```

| Option | Meaning |
|---|---|
| `--to <ip[:port]>` | The address shown on the phone (port 8686 if left out). Default: find the phone automatically. |
| `--pin <123456>` | The PIN shown on the phone. Not needed when this computer is paired with the phone; asked for otherwise. |
| `--save` | Save APKs as files instead of installing them. |

Examples:

```bash
droidsuite send app-release.apk
droidsuite send report.pdf app.apk --to 192.168.1.23 --pin 481027
droidsuite send app.apk --save
```

Open Receive on the phone first. Pairing is optional, but a paired computer skips the PIN. .apk, .apks and .zip (split bundles) are installed; other files are saved to Downloads/DroidSuite on the phone.

## get

Download the files a phone offers in Receive mode.

```
droidsuite get [file names...] [--to <ip[:port]>] [--pin <123456>] [--out <folder>]
```

| Option | Meaning |
|---|---|
| `--to <ip[:port]>` | The address shown on the phone (port 8686 if left out). Default: find the phone automatically. |
| `--pin <123456>` | The PIN shown on the phone. Not needed when this computer is paired with the phone; asked for otherwise. |
| `--out <folder>` | Where to save the files (default: the current folder). Existing files are never overwritten. |

Examples:

```bash
droidsuite get
droidsuite get report.pdf --out D:\in
```

On the phone: Receive → Offer files, or Share → DroidSuite → A browser. With no names, every offered file is downloaded.

## devices

List phones that have Receive mode open on this network.

```
droidsuite devices
```

Examples:

```bash
droidsuite devices
```

## debug

Connect adb to phones with Wireless debugging on (Android Studio, logcat, breakpoints).

```
droidsuite debug [--ip <x.x.x.x>]
```

| Option | Meaning |
|---|---|
| `--ip <x.x.x.x>` | Only connect to this phone. |

Examples:

```bash
droidsuite debug
droidsuite debug --ip 192.168.1.23
```

Finds the phone by itself, whatever port Wireless debugging picked today (also when the network blocks discovery, using the port the DroidSuite app reports). First time? Run "droidsuite debug setup".

## debug setup

Set up Debug over Wi-Fi step by step: turn on, pair, connect (Android 11+).

```
droidsuite debug setup [--code <123456> [<ip:port>]] [--timeout <seconds>]
```

| Option | Meaning |
|---|---|
| `--code <123456>` | Pair with the 6-digit code from "Pair device with pairing code" instead of the QR code. |
| `<ip:port>` | The IP address & Port shown under that code. Only needed when the network blocks discovery. |
| `--timeout <seconds>` | How long to wait (default 300). |

Examples:

```bash
droidsuite debug setup
droidsuite debug setup --code 123456 192.168.1.23:37123
```

Shows a QR code for "Pair device with QR code". Camera won't scan? Type the 6-digit code while it waits. "droidsuite debug pair" does the same.

## debug connect

Connect adb to the IP address & Port shown on the phone.

```
droidsuite debug connect <ip:port>
```

Examples:

```bash
droidsuite debug connect 192.168.1.23:41235
```

For networks that block discovery. The address is at the top of the phone's Wireless debugging screen, and in DroidSuite → Settings → Debug over Wi-Fi.

## debug usb

Android 8–10: turn on adb over Wi-Fi through a USB cable, then connect.

```
droidsuite debug usb
```

Examples:

```bash
droidsuite debug usb
```

Plug the phone in with USB debugging on, run this, then unplug. Needed again after each phone restart.

## debug doctor

Explain why Debug over Wi-Fi doesn't connect, and what to do.

```
droidsuite debug doctor
```

Examples:

```bash
droidsuite debug doctor
```

Checks adb, what the network shows, and what Live phones report (Android version, Wireless debugging port). Paste its output when reporting a problem.

## debug install

Install adb (Google's Android SDK Platform-Tools) for droidsuite.

```
droidsuite debug install [--yes]
```

| Option | Meaning |
|---|---|
| `-y, --yes` | Accept the Platform-Tools license without asking. |

Examples:

```bash
droidsuite debug install
```

Installs into %LOCALAPPDATA%\droidsuite (Windows) or ~/.droidsuite. Set DROIDSUITE_HOME to use another folder.

## debug path

Add adb to your PATH so typing "adb" works in new terminals.

```
droidsuite debug path
```

Examples:

```bash
droidsuite debug path
```

Windows: your user PATH only, no admin rights. macOS/Linux: one line in your shell profile. Safe to run twice.

## adb

Run adb, even when it isn't on PATH.

```
droidsuite adb <adb arguments...>
```

Examples:

```bash
droidsuite adb devices
droidsuite adb logcat -s MyApp
```

## shortcut

Add a "DroidSuite" icon that starts the server and opens its page.

```
droidsuite shortcut [--desktop]
```

| Option | Meaning |
|---|---|
| `--desktop` | Also put the icon on the desktop. |

Examples:

```bash
droidsuite shortcut --desktop
```

No terminal window: the icon opens the page in your browser, and the page does everything (Stop is on it too). Windows: "DroidSuite" in the Start menu (and on the desktop), plus "DroidSuite menu" for the text menu. macOS: a "DroidSuite" app on the desktop. Linux: "DroidSuite" in the applications menu. The installers do this for you.

## skill

Teach AI coding agents (Claude Code, Codex, Gemini CLI, Cursor and others) to use droidsuite, in every project.

```
droidsuite skill [--project | --dir <folder>] [--print]
```

| Option | Meaning |
|---|---|
| `--project` | Install only into the current project instead of for every project on this computer. |
| `--global` | Every project on this computer. This is the default. |
| `--dir <folder>` | Install into another skills folder, for an agent that reads skills from somewhere else. |
| `--print` | Only print where the bundled skill is. |

Examples:

```bash
droidsuite skill            # every project on this computer, for every agent
droidsuite skill --project  # only this project (commit it to share)
droidsuite skill --dir ~/.my-agent/skills
```

The installer offers this when it finds an AI agent on your computer. Always installs into .agents/skills and .claude/skills, and into the folders of Gemini CLI, Antigravity, Cursor, GitHub Copilot, Windsurf, Qwen Code and Amp when they are on this computer. The skill shows an agent how to install builds on your phone, read logcat and screenshots over Wi-Fi, and copy files, and which steps need you (pairing, Allow, PIN). Run it again after updating droidsuite or adding an agent.

## help

Show all commands, or the details of one.

```
droidsuite help [command]
```

Examples:

```bash
droidsuite help
droidsuite help serve
droidsuite serve --help
```

## Environment variables

| Variable | Meaning |
|---|---|
| `DROIDSUITE_HOME` | Folder for droidsuite's own adb copy (default %LOCALAPPDATA%\droidsuite or ~/.droidsuite). |
| `DROIDSUITE_CONFIG` | Pairing identity file (default ~/.droidsuite.json). |
| `ANDROID_HOME` | Android SDK folder; its adb is used first when present. |
| `NO_COLOR` | Turn off colours in the output. |

