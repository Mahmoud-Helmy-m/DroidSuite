# Install apps and builds

Send apps from your computer to your phone over Wi-Fi.

## Set it up

1. On the page, go to **Builds** and enter the folder that holds your APK files. DroidSuite remembers it, and **Change** picks another.
2. On the phone, open **Home → Available builds** and tap **Install**.
3. Confirm on Android if it asks.

Supported files are `.apk`, and `.apks` or `.zip` files that contain split APK bundles. An ordinary ZIP isn't an Android app.

> [!NOTE]
> You don't need a builds folder for files, debugging or the phone screen.

## Live builds

Leave **Live** on, and every new or changed build in that folder reaches the phone by itself.

- To choose when to install, turn off **Settings → Install pushed builds automatically**.
- To stop receiving builds, turn off **Live**.

In an Android project, this watches `app/build/outputs/apk`:

```bash
droidsuite serve
```

Or name any folder:

```bash
droidsuite serve path/to/apks
```

## When Android asks you to tap

| Connection | What happens |
|---|---|
| **Android 8–11, through the phone app** | Android asks every time. |
| **Android 12+, through the phone app** | The first install asks. Updates to apps DroidSuite installed can go through with no tap, though Android may still ask. |
| **With [Debug over Wi-Fi](debugging.md) connected** | The computer installs through adb, normally with no tap. |

> [!IMPORTANT]
> **Xiaomi, Redmi, POCO:** installing through adb needs **Developer options → Install via USB** on, and each install shows a prompt lasting about 10 seconds. Keep the phone unlocked and tap **Install**. If it's refused, DroidSuite hands the install to the phone app instead.

Play Protect may also ask about an app it doesn't know, even for updates.

## When a build won't install

| You see | Do this |
|---|---|
| **Needs Android** and a version | That build requires a newer Android than your phone has. |
| **Install through your computer** | Offered after a failed install when debugging is connected. Try it. |
| Wrong signature, or a newer version is installed | Tap **Uninstall old version** or **Uninstall newer version**. This deletes that app's data. |
| `app-release-unsigned.apk` fails | Release builds must be signed before they'll install. |

---

**Next:** [Debug over Wi-Fi](debugging.md) · [Troubleshooting](troubleshooting.md)
