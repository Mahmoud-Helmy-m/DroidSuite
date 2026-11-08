# Android versions

DroidSuite works on Android 8 and newer. Your phone's exact limits appear in the app under **Settings → This phone**, and on the computer's page under **Phones on Live**.

| Feature | 8–9 | 10 | 11 | 12 | 13+ |
|---|---|---|---|---|---|
| **Installs through the phone app** | Tap each time | Tap each time | Tap each time | Updates can skip the tap | Same as 12 |
| **Debug over Wi-Fi** | USB after each restart | USB after each restart | Wireless; turns off after a restart or Wi-Fi change | Wireless | Wireless |
| **Files received on the phone** | DroidSuite's own folder | `Downloads/DroidSuite` | `Downloads/DroidSuite` | `Downloads/DroidSuite` | `Downloads/DroidSuite` |
| **Notifications** | On | On | On | On | Allow when asked |
| **Screen view restarts** | Every 3 minutes or so | Every 3 minutes or so | Every 3 minutes or so | Every 3 minutes or so | Android 13 only |

- With [Debug over Wi-Fi](debugging.md) connected, builds can install through the computer without the phone-app prompts. See [Install apps and builds](builds.md).
- The [Phone screen](phone-screen.md) needs a debugging connection on every version.
- The screen-view restart is brief, and the picture comes back by itself. Android 14 and newer don't have it.

---

**Next:** [Troubleshooting](troubleshooting.md)
