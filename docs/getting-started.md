# Get started

About 10 minutes, once. After that, you just open the icon.

## What you need

- An Android phone, version 8 or newer.
- A Windows, Mac or Linux computer with a browser.
- Both on the same network: normally the same Wi-Fi, or the phone on the computer's hotspot. Guest networks often keep devices apart, so avoid them.

## 1. Install on your computer

**Have Node.js 20 or newer?** Run this in any terminal:

```bash
npx droidsuite@latest setup
```

**Don't have Node.js?** Use the installer for your system.

<details>
<summary><strong>Windows</strong></summary>

Press <kbd>Win</kbd>+<kbd>R</kbd>, paste this whole line, and press <kbd>Enter</kbd>:

```powershell
powershell -NoExit -ExecutionPolicy Bypass -Command "irm https://cdn.jsdelivr.net/npm/droidsuite/install.ps1 | iex"
```

Don't download `install.ps1` and double-click it, because Windows blocks downloaded scripts. This line runs the installer once and doesn't change your script settings.

</details>

<details>
<summary><strong>Mac or Linux</strong></summary>

Open Terminal, paste this, and press <kbd>Enter</kbd>:

```bash
curl -fsSL https://cdn.jsdelivr.net/npm/droidsuite/install.sh | sh
```

On a Mac, it offers to install Node.js if Homebrew is available. Otherwise, install Node.js 20 or newer from [nodejs.org](https://nodejs.org), then run this line again.

</details>

### The questions it asks

| Question | What to answer |
|---|---|
| **Install Node.js?** | Yes. DroidSuite needs it. |
| **Install adb?** | Yes, if you want the phone screen or debugging. You can skip it if you only need files and app installs. |
| **Add adb to PATH?** | Optional. Say yes if you'll type `adb` commands yourself. |
| **Let your AI agent use your phone?** | Only appears if you have one. See [AI coding agents](ai-agents.md). |

> [!TIP]
> If Windows Firewall asks about Node.js, choose **Allow** for your private network. Without that, your phone can't reach the computer.

When setup finishes, you have a **DroidSuite** icon:

| System | Where it is |
|---|---|
| Windows | Desktop and Start menu |
| Mac | Desktop |
| Linux | Applications menu |

## 2. Open DroidSuite

Open the icon. The DroidSuite page opens in your browser, normally at `http://localhost:8765`. No window stays open, because it runs quietly in the background.

## 3. Get the phone app

1. On the page, open **Pair your phone** and find **Get the phone app**.
2. Scan that code with your phone's normal camera.
3. Tap **Download DroidSuite**, then open the downloaded file.
4. Android asks whether your browser may install apps. Allow it, then tap **Install**.

Open the app. When it asks to install apps and show notifications, allow both.

## 4. Connect

1. In the phone app, tap **Pair**.
2. Scan the **big** code on the computer's page.
3. On the app's **Home** screen, check that **Live** is on.

The page now shows your phone under **Phones on Live**. You only pair once.

> [!NOTE]
> Camera not working? In **Pair**, tap **Camera not working? Type a code instead**, and enter the **Computer address** and **Code** shown under the big QR code.

> [!WARNING]
> The big QR code and its code connect a phone to your computer. Don't share or post them.

## Every day after that

- **Start:** open the **DroidSuite** icon.
- **Phone:** open the app and check **Live** is on.
- **Stop:** click **Stop** at the top right of the page. Closing the tab leaves DroidSuite running.

## Update

DroidSuite tells you when a newer version is out. To update:

```bash
npx droidsuite@latest setup
```

Use `@latest`. Without it, `npx` can run the older copy you already have.

## Uninstall

1. Click **Stop** on the page, and uninstall the DroidSuite app from your phone.
2. Run:

   ```bash
   npm uninstall --global droidsuite
   ```

3. Delete the **DroidSuite** icons.

Files you received stay in `Downloads/DroidSuite`. To remove the rest, delete `.droidsuite.json` from your home folder, and `%LOCALAPPDATA%\droidsuite` on Windows or `~/.droidsuite` on Mac and Linux.

## Used APK Bridge before?

DroidSuite is its new name. It's a new package and a new phone app, so nothing moves over. Install DroidSuite and pair again, then remove the old one:

```bash
npm uninstall --global apk-bridge
```

Uninstall APK Bridge from your phone too.

---

**Next:** [Phone screen](phone-screen.md) · [Files](files.md) · [Install apps and builds](builds.md)
