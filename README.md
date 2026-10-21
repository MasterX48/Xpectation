# XPECTATION — meet jr.X

**jr.X** is an advanced closed-source AI desktop assistant featuring an animated orb UI. It functions as an autonomous voice-and-text agent that controls desktops, runs system terminal tasks, and performs deep parallel web research.

* **Developer:** MasterX
* **License:** Closed Source / Proprietary. Free for personal, non-commercial use only. (See `LICENSE` for full terms).
* **Core Engine:** Powered by Google Gemini.

---

## 🚀 Quick Setup

1. **Launch:** Run the compiled `jrX_Setup.exe` binary.
2. **API Key Setup:** Obtain a free API key from [Google AI Studio]([https://aistudio.google.com/api-keys]). Paste it into the window prompt on the first launch.

---

## 🌟 Key Features

### 🎙️ Audio Clean-Up & Routing
* **Voice Normalization:** Automatically adjusts speech levels—boosting quiet phrases and dampening shouting while avoiding clipped audio starts.
* **Noise Suppression:** Includes *Standard* and *Strong* filters to remove rumbles and persistent background room hums.
* **Accent Tuning:** Optimizes local recognition for mixed language accents (e.g., "English, Hindi").

### 🤫 Wake Word & Push-to-Talk (PTT)
* **Offline Detection:** Responds to your custom wake phrase (default: *"hey junior x"*). Processing runs completely offline to maintain private tracking until activated.
* **PTT Mode:** Map a hotkey (default: `F9`) or use the on-screen *Hold to talk* action to toggle mic input.

### 🖥️ On-Screen Preview Card
* **Live Feeds:** Streams terminal strings and research tasks in a compact top-right overlay window that sits above other apps.
* **Instant Activation:** Pops up immediately upon hearing trigger words (*research, summarise, terminal*). The overlay is fully resizable and draggable across multi-monitor setups.

### 🌐 Browser & System Autopilot
* **Visual Navigation:** Drives a isolated Chrome user profile to scroll, read page layouts, and click elements by sight. *Blocks password and card input zones for security.*
* **Virtual Cursor:** Displays a distinct glowing mouse overlay to perform commands without stealing control of your physical mouse.

### 📟 Protected Terminal Automation
* **Execution Safeguards:** Instantly processes read-only metrics (`dir`, `git status`). Triggers a confirmation check overlay for file edits and outright refuses catastrophic system sweeps.

### 🧠 System Tray & Memory
* **Long-Term Data:** View, append, or purge records kept in core visual memory maps.
* **Background Mode:** Runs silently from the Windows system tray; includes a "Start hidden" toggle.

---

## 🧩 Built-in Plugins

* **sheets:** Programmatically exports native `.xlsx` files with charts and dynamic formulas straight to the Desktop.
* **quiz:** Generates responsive interactive quizzes featuring auto-grading stats.
* **doc_review:** Scans PDF, DOCX, and TXT inputs into a summary panel.
* **water:** Local countdown logs with automated desktop hydration notifications.
* **telegram_remote:** Encrypted desktop management access using one-time token sync controls.
* **chat_reply:** Pulls context from screen text to instantly draft communication templates.
* **games:** Tracks, manages, and executes games from your local Steam library.

---

## 🗣️ What You Can Say

* *"Research the best budget laptops and summarise"*
* *"Open YouTube and search lo-fi music"*
* *"Run git status in my project folder"*
* *"Open Settings and turn on dark mode"*
* *"Compare solar vs wind power from several sources"*

---

## 🛑 Instant Interruption
Kill active voice lines, web automation tracking loops, or terminal scripts by:
* Hitting global **`F8`** or **`Esc`** when focused.
* Clicking **⏹ Stop** on the primary layout or the overlay card.
* Saying the wake phrase **"stop"** out loud.
