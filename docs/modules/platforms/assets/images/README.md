# Platform screenshots

Screenshots used by the `platforms` module pages. One set per platform, captured
from the **Fruit** edition so both sets show the same theme.

| File | Screen |
| --- | --- |
| `menu.png` | Main menu — best score, leaderboard card, Play, Daily Challenge |
| `gameplay.png` | A run in progress — score, danger line, power-up rail, piece ladder |
| `settings.png` | The Settings screen at its defaults |
| `pause.png` | The pause overlay, captured during an Endless run so *Finish game* is visible |

## How they were captured

Android — Medium Phone API 36.1 emulator, 1080×2400:

```sh
scripts/build_pack.sh fruits_classic apk --release        # in the app repository
adb install -r build/app/outputs/flutter-apk/app-release.apk
adb exec-out screencap -p > menu.png
```

iOS — iPhone 16 Pro Max simulator, iOS 18.5, 1320×2868:

```sh
flutter build ios --simulator --debug                     # in the app repository
xcrun simctl install <udid> build/ios/iphonesimulator/Runner.app
xcrun simctl io <udid> screenshot menu.png
```

Both sets were then scaled to a maximum dimension of 1400 px with
`sips -Z 1400`.

Set the run timer to **Endless** in Settings before capturing gameplay: a timed
run ends before the jar has filled enough to photograph well, and *Finish game*
only appears in the pause menu during an endless run.
