# Troubleshooting

Find your problem below. Still stuck? [Report it](https://github.com/Mahmoud-Helmy-m/droidsuite/issues/new?template=bug_report.yml).

## Connecting

| Problem | Fix |
|---|---|
| Phone can't reach the computer | Open DroidSuite with the icon. Put both on the same network, avoid guest Wi-Fi, and turn off VPNs while checking. On Windows, set your Wi-Fi profile to **Private** and allow Node.js through the firewall. |
| Page says **DroidSuite isn't running** | Open the **DroidSuite** icon. The tab reconnects by itself. |
| No phone listed, or the file area is disabled | Pair the phone and turn **Live** on. |
| Pair code rejected | Use the current code. It changes after use and every 10 minutes. |

## Installing DroidSuite

| Problem | Fix |
|---|---|
| "irm is not recognized" | Use the full Windows line, starting with `powershell`. |
| Node.js is installed but the window can't see it | Close the window, open a new one, and run the line again. |
| Permissions error on Mac or Linux | Follow the printed instructions for npm permissions, then run the installer again. |
| `npx droidsuite setup` runs an old version | Use `npx droidsuite@latest setup`. |
| The downloaded phone app is "damaged" | Delete it, then download a fresh copy from **Get the phone app**. |

## Apps and builds

| Problem | Fix |
|---|---|
| No builds appear | Check the folder under **Builds**, and that it has supported files. |
| Builds arrive but don't install | Turn on **Settings → Install pushed builds automatically**. Allow **Install unknown apps** and notifications. |
| Install cancelled or blocked | Retry and follow Android's prompt. Closing it cancels the install. Only install apps you trust. |
| Xiaomi, Redmi, POCO blocks installs from the computer | Turn on **Developer options → Install via USB**, then tap **Install** on the prompt within about 10 seconds. Xiaomi may ask for a Mi account and SIM card. |

## Debugging and the phone screen

| Problem | Fix |
|---|---|
| Wireless debugging is off | Android can turn it off after a restart or Wi-Fi change. Turn it on, then click **Connect over Wi-Fi**. You don't need to pair again. |
| No phone found | Click **Run checks** under Debug over Wi-Fi. |
| Screen shows but taps do nothing (Xiaomi, Redmi, POCO) | Turn on **Developer options → USB debugging (Security settings)**, restart the phone, and reconnect. |
| Screen is black | Click **Wake** and unlock the phone. Banking and password screens stay black. |
| **Paused** or **In another tab** | Click **Resume**, or use the tab where you started the view. |

## Files and clipboard

| Problem | Fix |
|---|---|
| Receive page rejects the PIN | Use the PIN shown now. After five wrong tries, wait 30 seconds. |
| Clipboard asks you to unlock | Unlock the phone and try again. Android restricts the clipboard while locked. |
| Browser refuses clipboard access | Allow it for the page, or use <kbd>Ctrl</kbd>+<kbd>V</kbd> on the running picture. |

## Before you report a problem

Run this and include the result:

```bash
droidsuite debug doctor
```

On startup problems, the log is at `%LOCALAPPDATA%\droidsuite\serve.log` on Windows, and `~/.droidsuite/serve.log` on Mac and Linux.

> [!WARNING]
> Check anything you paste first. Remove pairing codes, PINs and personal details.
