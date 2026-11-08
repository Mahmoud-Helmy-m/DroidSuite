# Privacy and security

## What stays on your network

Your apps, files and phone screen travel directly between your devices. They don't go through any DroidSuite server, and there's no account.

## What uses the internet

| What | When |
|---|---|
| **npm** | Installing or updating DroidSuite |
| **npm, once a day** | Checking for a newer version. It sends nothing about you or your phone. To turn it off, set `DROIDSUITE_NO_UPDATE_CHECK=1`. |
| **Google** | Downloading adb, if you choose to; the computer page may also load fonts |

## Keep these private

The big pairing QR code and its code connect a phone to your computer. Don't share them, or show them in a screenshot, video or issue.

To disconnect a phone, use **Settings → Computers → Forget** in the app. Android's debugging trust is separate: remove it under **Wireless debugging → Paired devices**.

## Who can connect

| Connection | How it's allowed |
|---|---|
| **Paired phone** | It holds a secret key from pairing. |
| **Computer page** | Only the computer running DroidSuite can open its controls. |
| **Receive mode** | The current PIN, a browser you approved with **Allow**, a remembered browser, or a paired computer. |

Before tapping **Allow**, check that the two-digit code matches. Five wrong PINs cause a 30-second lockout.

## Use a network you trust

App and file sharing use ordinary HTTP, so DroidSuite doesn't encrypt that traffic. Someone able to watch your local network could see it. Avoid public Wi-Fi.

Paired transfers are checked for damage. Browser transfers in Receive mode don't have the same check.

## What the phone shares

- While connected, the phone sends details such as its name and Android version to your computer.
- Screen viewing starts only when you press **Start**.
- Files are read only when you send or offer them.
- The clipboard isn't monitored. It's read only when you click **Copy the phone's clipboard here**.

## AI agents

If you add the [skill](ai-agents.md), anything your agent reads, such as logs and screenshots, goes to that agent's AI provider.

## Reporting a security problem

Please see the [security policy](../SECURITY.md).
