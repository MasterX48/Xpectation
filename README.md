# XPECTATION — meet jr.X  (closed-source, freeware edition)

A voice-and-text AI desktop assistant with an animated orb UI, created by **MasterX**.
Works with Google Gemini, any OpenAI-compatible API, or a model running on your own PC (Ollama, LM Studio, llama.cpp).
Licence: see LICENSE (proprietary freeware). Third-party parts: THIRD_PARTY_NOTICES.md.

## For users
Run **jrX-Setup-x.y.z.exe**, press Next. Start jr.X from the Desktop / Start-menu icon. On first launch paste your free
Gemini API key (https://aistudio.google.com/apikey) — or choose a local model in ⚙ Settings → Engine.

## For the developer (making the installer)
Read **INSTALLER_GUIDE.md**. Short version: install Python 3.11–3.13 and Inno Setup 6, then double-click
**`make_installer.bat`**. It builds the app, runs the self-test and writes `installer_output\jrX-Setup-<version>.exe`.

## Settings highlights
- **Audio:** choose your microphone and speaker (or leave on System default), with a speaker test button.
  - *Voice clean-up* (Standard / Strong / Off): evens out how loud you are (quiet or distant speech is lifted, shouting is pulled down), removes rumble and steady background hum, and keeps the very start of each phrase so the first word isn't lost. Strong is for noisy rooms or sitting far from the mic. If it ever seems to hear you worse, switch it to Off.
  - *Languages I speak*: e.g. "English, Hindi" — tells jr.X to expect your accent and phrases mixed from other languages.
- **Wake / Talk:** two independent switches.
  - *Wake word* (default phrase "hey junior x", change it to anything): jr.X sleeps until it hears the phrase, stays awake for N seconds after the last activity, then sleeps again. Detection is offline (Vosk), so nothing is sent to Google while asleep. First use downloads a ~40 MB model.
  - *Push to talk* (default key F9): mic is live only while the key — or the on-screen **Hold to talk** button — is held.
  - Both on = either works. Both off = always listening.
- **Background:** the first launch asks once whether jr.X may keep running in the system tray after you close the window. Your answer is remembered (change it under Settings → Background). While in the tray it isn't in the taskbar; click the tray icon or the shortcut again to reopen, and use tray → Quit to exit fully. "Start hidden" launches straight to the tray.
- Logs: `~/.xpectation/jrx.log`.

## Stop / interrupt
Press **⏹ Stop** (next to Send), hit **Esc** in the window, use tray → "Stop what jr.X is doing", press the global **F8** key (change or turn it off under Settings → Wake / Talk), or just say "stop". jr.X immediately cancels the browser action, terminal command, desktop task or reply in progress, goes quiet, and won't pick that task up again unless you ask.

## The preview card
When jr.X runs a terminal command or does research, a small card pops up in the **top-right corner** of the screen — even if the main window is hidden in the tray. Command output streams into it live; research shows its progress and then the finished summary with clickable sources. It pops up **the moment you ask** — as soon as jr.X hears words like research, summarise, compare, find out, terminal, PowerShell or "run a command", it is already on screen saying **Searching…** or **Starting the terminal…**, then fills in the progress and the finished result. For terminal work it appears before the approval question, and a refused command is shown as "not run". If nothing ends up being started it tells you so. A finished research result always appears on the card (even if you closed it while it was working), and late speech recognition can no longer overwrite it. The card forces itself to the front (above Chrome, terminals and other windows) when it opens, when the result arrives, and keeps itself there while work is running. You can **drag it by its title bar** to move it anywhere (even to another monitor) and **drag the bottom-right corner** to resize it; jr.X remembers where you left it. It is never shown at start-up and stays until you press **✕ Close** (this only hides the card; **⏹ Stop** on the card cancels the work). Turn it off per plugin in Plugins → settings.

## MCP quick start
**Easiest:** ⚙ Settings → **MCP** tab. Press **＋ Add server** and fill in the form (a program like `npx`/`uvx` plus its arguments, or a remote web address with optional headers), or press **Paste JSON…** and paste the config from any MCP server's README. **Test connection** starts the server and lists its tools. Works for official and unofficial servers alike. Edits there are saved straight away; **Delete** removes a server, **Switched off** keeps it listed without connecting, and **trusted** (off by default) stops jr.X asking before that server's tools change things.

**Or by hand:**
Create `~/.xpectation/mcp.json` (jr.X makes an empty one the first time the MCP tool is used):
```json
{"mcpServers": {"files": {"command": "npx", "args": ["-y", "@modelcontextprotocol/server-filesystem", "C:/Users/me/Documents"]}}}
```
Restart jr.X (or say "connect to files") and ask for things: "list the files in my Documents", "what can the files server do?". Server messages are logged in `~/.xpectation/data/mcp/`.

## Things to say
"Open YouTube and search lo-fi music" · "Scroll down" · "Click the second result" · "What does this page say?" · "Search images of red sports cars" · "Make Chrome full screen" · "Minimise Spotify" · "Close Notepad" · "Switch to Discord" · "Open Settings and turn on dark mode" (does it step by step, by sight) · "How much disk space is free?" · "What's my IP address?" · "Run git status in my project folder" · "Start the dev server" · "Open a terminal" · "Research the best budget laptops and summarise" · "Compare solar vs wind power from several sources" · "What can my MCP servers do?".

## Using it
- Voice mode: just talk. Use the mic button to mute. Text mode: type and press Enter.
- Ask "who created you?" — jr.X always answers MasterX (locked core memory).
- 🧠 Memory: view/add/remove things jr.X remembers. 🧩 Plugins: turn plugins on/off and set them up. ⚙ Settings: name, voice, accent colour, models.

## Built-in plugins
| Plugin | What it does |
|---|---|
| sheets | Builds real .xlsx files (headers, numbers, SUM totals, charts) into ~/Desktop/XPECTATION |
| quiz | Interactive quizzes with grading |
| doc_review | Reads PDF/DOCX/TXT and shows a findings panel |
| water | Hydration tracking + reminders |
| telegram_remote | Control jr.X from Telegram — allow-list + one-time pairing code, rate-limited |
| chat_reply | Drafts replies to the chat on screen; asks you to confirm before sending (autopilot is time-boxed) |
| games | Lists/launches/updates **Steam** games |
| browser | Drives a real **Chrome** window like a person: open, search (web/images/videos/news/maps), read pages, click, type, scroll, tabs, look at the page with vision, full-screen/minimise. Uses its own Chrome profile, so sign in to your sites once and it stays signed in. Refuses to type passwords or card numbers. Falls back to Edge, then Chromium (`python -m playwright install chromium`). |
| (pointer) | jr.X has **its own mouse pointer**. In the browser it's a glowing "jr.X" cursor drawn on the page that glides, hovers, clicks, double/right-clicks and drags using real mouse input — your own mouse isn't touched, and it works on canvas, hover menus, custom widgets and drag-and-drop. If something has no name to click, jr.X finds it by sight ("click the red play button"). For other apps it shows the same pointer on screen wherever it clicks. Both can be switched off in Plugins → settings. |
| terminal | Uses the **terminal** like a person: runs a command and reads the result (PowerShell on Windows, bash elsewhere), keeps long-running things going (servers, ping) and lets jr.X check on them, type into them or stop them, remembers the current folder, and can pop open a real terminal window. **Safe by design:** read-only commands (`dir`, `ls`, `git status`, `ping`…) run immediately; anything that could change files, settings or software shows you the exact command and what it does and waits for your OK (default answer: No); catastrophic commands (wipe a disk, `rm -rf /`, format, fork bombs…) are refused outright. Commands can't wait for keyboard input, are stopped after a time limit, and every one is logged (ask "what did you run?"). Plugins → settings lets you ask before every command, or turn the prompts off (not recommended). |
| research | **Multi-site research with no browser window.** Say "research…", "summarise…", "compare…", "what do people say about…" and jr.X searches the web, reads up to 8–15 sites in parallel in the background, and writes one summary with numbered sources. Web pages are treated as information only, never as instructions; only public websites are fetched. Sites that need JavaScript or a login can't be read this way — use the browser plugin for those. |
| mcp | **Use any app that has an MCP server** (files, GitHub, Blender, Spotify, Notion, databases, smart home…). List your servers in `~/.xpectation/mcp.json` (same format as Claude Desktop). jr.X sees each server's tools and calls them. Tools that only read run straight away; anything that changes things shows you the server, tool and exact arguments and waits for your OK (default: No) — unless you mark that server `"trusted": true` in the file yourself. jr.X can add a server only after you approve the exact command, and it is never trusted automatically. Needs `pip install mcp`; most servers also need Node.js (`npx`) or `uv` (`uvx`). |
| desktop | Any app: list / focus / minimise / maximise / full-screen / snap / close windows, type, press keys, click, scroll — and `do`: look at the screen and carry out a task step by step. Asks permission before taking over the mouse (setting); move the mouse to the top-left corner to abort. |

## Your own plugins
jr.X makes a plugin folder for you on first run: `C:\Users\<you>\.xpectation\plugins` (**Plugins → Open plugins folder**
opens it; the Start-menu shortcut "jr.X plugins folder" too). It already holds a `README.txt`, a `_template.py` and a working
`_example_hello.py`.

1. Copy `_template.py` to `mine.py` (no leading `_`), edit it.
2. In jr.X open 🧩 **Plugins → Rescan**. Your plugin appears tagged **[yours]**, switched **off**.
3. Tick it and press Close. jr.X reloads its tool list; ask for what the plugin does.

Built-in plugins (browser, terminal, desktop, research, MCP…) ship inside the app and are tagged **[built-in]**. A plugin can
use everything jr.X itself uses: the whole Python standard library, mouse/keyboard (`pyautogui`), screenshots (`mss`),
`requests`, `psutil`, `Pillow`, `playwright`, `openpyxl`, `python-docx`, `pypdf`, `numpy`, `pyperclip`, and `ctx.*` helpers
(say, confirm, screenshot, settings, a private data folder, the result card). Other packages: put them in
`.xpectation\plugin_libs` (`pip install --target "%USERPROFILE%\.xpectation\plugin_libs" <package>`).
Plugins run with your rights — only switch on code you trust.

```python
from xpectation.sdk import tool

@tool("hello", "Greets someone", {"name": {"type": "string", "description": "who"}}, required=["name"])
def hello(ctx, name):
    return f"Hello {name}!"
```

## Notes
- Wake word and push-to-talk are optional and off by default; with both off, voice mode listens while the app is open.
- Push-to-talk's global key needs `pynput`: on macOS grant Accessibility/Input Monitoring permission; on Linux Wayland use the on-screen button.
- Reply speed (Settings → General): Fast / Balanced / Patient controls how quickly jr.X decides you've finished talking.
- Window control: Windows and macOS work out of the box; Linux needs `wmctrl` (and `xdotool` for minimise) on X11.
- No sound? jr.X now reopens the speaker if it drops, falls back to the system default speaker / the device's own sample rate, and shows a 🔇 message if it truly can't play. If you plug in headphones mid-session, pick them in Settings → Audio and Save. Use "Test speaker" to check.
- Memory of the chat: jr.X remembers the whole conversation until you Quit from the tray (hiding the window, voice reconnects, switching voice/text and changing settings all keep it). 🗑 New chat clears it. Long-term facts you tell it to remember (🧠 Memory) are separate and permanent.
- Voice reconnects: network drops and server limits are retried automatically and quietly — jr.X no longer falls back to text-only unless the key/model/quota is wrong. If replies arrive without sound twice in a row it reconnects voice by itself.
- Hearing you better: the microphone signal is cleaned before it's sent (see Voice clean-up), the first ~160 ms before you start speaking is kept, and if your mic refuses 16 kHz jr.X opens it at its own rate and converts properly instead of failing. If jr.X still cuts you off mid-sentence, set Reply speed to Balanced or Patient.
- Browser closing / repeating: a pop-up or tab that closes itself no longer takes the whole browser with it; if the real window died it is reopened and a safe action is retried once; if Chrome keeps closing right after opening (3 restarts in 90 s) jr.X stops and tells you instead of looping, and leftover Chrome processes holding its profile are cleaned up. Any call repeated with the same result is refused after two goes. Details are in `~/.xpectation/jrx.log`.
- Voice uses Gemini's Live API; if it fails 3 times jr.X falls back to text mode.
- Run tests: `pip install pytest && python -m pytest`

## Phone remote
Control jr.X from your phone's browser, no app needed. In jr.X press **📱 Phone** (or the tray menu → *Phone remote…*),
tick **Allow control from my phone**, and scan the QR code with a phone on the same Wi-Fi. The page shows the same chat
and the result pop-up text; type a command or tap 🎤 to speak one (Chrome on Android; if the browser blocks the mic on
plain http, use the 🎤 on your keyboard). ⏹ stops what jr.X is doing. It is off by default, local-network only, protected
by a secret in the QR link (**New link** signs every phone out), and approval questions still appear on the PC.
If Windows asks about the firewall, allow *Private networks*.

## Engines, models and local voice (Settings → Engine)
- **Model ladder.** Gemini text calls (typed chat, research summaries...) go through an ordered list of models. A quota (429), a
  timeout or an outage steps to the next model; a failed model is parked for a while (quota 5 min, outage/timeout 10–15 min, "your key
  can't use it" 6 h) and the best one is used again as soon as it recovers. Names your key doesn't have are skipped. Edit the list in
  Settings → Engine. Gemini Live (voice) keeps its own two-step fallback.
- **Choose your brain.** Gemini, or any OpenAI-compatible server: Ollama, LM Studio, llama.cpp, vLLM, OpenAI, Groq, DeepSeek,
  Mistral, xAI, OpenRouter, or a custom URL. Each has its own model list (also a ladder) and tools work when the model supports them;
  small local models get short tool descriptions. `localhost` is turned into `127.0.0.1` and a machine-wide proxy is never used to
  reach local servers.
- **Choose your voice.** *Gemini Live*, or *Local*: Whisper (faster-whisper, CPU) hears you and a Windows voice speaks, offline. Whisper
  follows the language you speak (a switch needs a confident detection and at least three words); the Windows voice for that
  language is used if you have it installed (Windows Settings → Time & language → Speech). Whisper's model downloads the first time.

### Local models: install, auto-start, auto-stop (UNDER WORKING PHASE🚫)
Settings → **Engine** → *Engine: Local app on this PC* → pick **Ollama**, **LM Studio** or **llama.cpp** → pick a model from the
list (or type any name, e.g. `qwen3:8b`) → **Install this model**. jr.X downloads it (with progress), and from then on starts the
app and loads the model every time it opens, and turns the model off when you quit. A server you were already running is left
alone; only the model is unloaded. Untick *Start it with jr.X…* to manage the app yourself. The app itself (Ollama / LM Studio)
must be installed once; the tab shows a download link if it isn't.
