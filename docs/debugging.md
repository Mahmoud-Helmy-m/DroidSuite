# Debug over Wi-Fi

Connect adb to your phone with no cable. This powers the [Phone screen](phone-screen.md), and it works with logcat and Android Studio.

It's a separate connection from pairing the phone app.

## 1. Turn on Developer options

In Android **Settings**, find the item below and tap it **seven times**.

| Phone | Tap this seven times | Developer options is in |
|---|---|---|
| Most phones (Pixel, Motorola, Nokia) | About phone → **Build number** | System |
| Samsung | About phone → Software information → **Build number** | Bottom of Settings |
| Xiaomi, Redmi, POCO | About phone → **MIUI version** or **OS version** | Additional settings |
| OPPO, realme, OnePlus | About device → Version → **Build number** | Additional settings or System settings |
| vivo | About phone → **Software version** | System management |
| Huawei, Honor | About phone → **Build number** | System & updates |

The phone app's **Guide** (the **?** on Home) has buttons that open these screens.

## 2. Connect

### Android 11 and newer

1. On the page, go to **Debug over Wi-Fi**. Click **Install adb** if it's offered, then **Start setup**.
2. On the phone, open DroidSuite → **Settings → Debug over Wi-Fi → Open Wireless debugging**. Turn it on and tap **Allow**.
3. On Android's Wireless debugging screen, tap **Pair device with QR code**, and scan the code inside the page's setup. Use Android's scanner here, not DroidSuite's.
4. Wait for it to connect, then click **Done**.

<details>
<summary>The QR code won't scan</summary>

Tap **Pair device with pairing code** on the same Android screen. Enter the **Wi-Fi pairing code** and the **IP address & Port** under it into the page's setup, and keep that dialog open while you do.

If setup later asks for a connection address, use the **IP address & Port** at the top of the Wireless debugging screen. It's a different port.

</details>

You only pair once. Android turns Wireless debugging off after a restart or a Wi-Fi change, on some versions, so if it drops, turn it back on and click **Connect over Wi-Fi**.

### Android 8 to 10

These versions have no Wireless debugging, so they need a USB cable once after each restart.

1. Pair the phone app, and turn **Live** on.
2. On the phone, turn on **Developer options → USB debugging**.
3. Connect the cable and tap **Allow**.
4. On the page, under **Debug over Wi-Fi**, click **Switch to Wi-Fi**. Unplug when it says you can.

## From the terminal

```bash
droidsuite debug setup    # guided setup, once
droidsuite debug          # connect, whatever port the phone picked today
droidsuite debug doctor   # explain why it isn't connecting
droidsuite adb devices    # run adb, even if it isn't on your PATH
```

## Three different codes

| Code | Shown on | Used in |
|---|---|---|
| **Code** | The computer, under Pair your phone | Phone app → Pair → Type a code instead |
| **PIN** | The phone's Receive screen | The browser page at the phone's address |
| **Wi-Fi pairing code** | Android's Wireless debugging | The page's Debug over Wi-Fi setup |

> [!TIP]
> Stuck? Click **Run checks** under Debug over Wi-Fi, or run `droidsuite debug doctor`. Both say what's wrong and what to do next.

---

**Next:** [Phone screen](phone-screen.md) · [AI coding agents](ai-agents.md)
