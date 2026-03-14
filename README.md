# 🔊 Faah Terminal Alerts

> Immediate auditory feedback for terminal errors — so you never miss a failed build again.

Terminal Error Sound monitors your VS Code Integrated Terminal and background build tasks, emitting a configurable notification sound whenever a process exits with a non-zero exit code. Stay in flow without constantly watching your terminal for failures.

---

## ✨ Features

- **Precise failure detection** — Relies on native process exit codes rather than output parsing, ensuring reliable alerts with no false positives.
- **Cross-platform support** — Works seamlessly on macOS, Windows, and Linux.
- **Zero-configuration setup** — Fully functional immediately after installation; no initial configuration required.
- **Flexible customization** — Override the default sound with a custom audio file, adjust playback volume, and toggle the extension on or off directly from the status bar.
- **Intelligent debouncing** — Throttles audio alerts during cascading or rapid successive errors to prevent alert fatigue.

---

## 🚀 Installation

1. Install the extension from the [VS Code Marketplace](https://marketplace.visualstudio.com/) (or install manually via the `.vsix` file).
2. Open the VS Code Integrated Terminal.
3. Run any command that exits with an error — the audio alert will trigger automatically.
4. Use the **"Error Sound"** indicator in the status bar to toggle the extension on or off at any time.

---

## ⚙️ Configuration

The following settings are available via `settings.json` or the VS Code Settings UI (`Ctrl+,` / `Cmd+,`):

| Setting | Default | Description |
|---|---|---|
| `terminalErrorSound.enabled` | `true` | Globally enables or disables the error notification sound. |
| `terminalErrorSound.volume` | `75` | Sets the playback volume on a scale of 0–100. *(Currently effective on macOS only.)* |
| `terminalErrorSound.soundFile` | `""` | Absolute path to a custom audio file. **Note:** Windows users *must* use a `.wav` file. macOS/Linux users can use `.wav` or `.mp3`. |

---

## 📋 Commands

The following commands are available via the Command Palette (`Cmd+Shift+P` on macOS, `Ctrl+Shift+P` on Windows/Linux):

| Command | Description |
|---|---|
| `Terminal Error Sound: Toggle On/Off` | Enables or disables the extension globally. |
| `Terminal Error Sound: Test Sound` | Plays the currently configured audio file to verify volume and file path settings. |

---

## 🛠️ Troubleshooting

This extension listens exclusively to the **Integrated Terminal** and **Background Tasks**. If a failure occurs in the **Output** or **Debug Console** panels — such as when using "Play" buttons or the debugger — no audio alert will be triggered, as those environments are isolated from the terminal.

To ensure the extension captures your errors, route execution through the Integrated Terminal using the relevant configuration below.

### Code Runner

1. Open VS Code Settings (`Ctrl+,` / `Cmd+,`).
2. Search for `code-runner.runInTerminal`.
3. Enable the setting to route all Code Runner executions through the Integrated Terminal.

### Python Extension

1. Open VS Code Settings (`Ctrl+,` / `Cmd+,`).
2. Search for `Python: Terminal Execute In File Dir`.
3. Enable the setting to ensure Python scripts run directly in the terminal.

### Node.js Debugger (F5)

Add the following property to your run configuration in `.vscode/launch.json` to direct debugger output to the Integrated Terminal:

```json
"console": "integratedTerminal"