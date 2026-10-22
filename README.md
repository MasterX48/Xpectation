
XPECTATION — meet jr.X

A voice-and-text AI desktop assistant with an animated orb UI, created by MasterX. Closed source / Proprietary. Free for personal non-commercial use only. Source code is not publicly released. See LICENSE for full terms.

Install & Launch (Windows)

1. Download the single jrX_Setup.exe installer.
2. Double-click the file to install jr.X directly to your system.
3. Launch the application using the new jr.X Desktop shortcut or your Start Menu.
4. On first launch, paste your free Gemini API key (aistudio.google.com/apikey).

Features & Usage


🎙️ Voice & Talk

• Audio Settings: Choose your preferred microphone and speaker directly in the UI, featuring a built-in speaker test button.
• Voice Clean-Up: Select between Standard, Strong, or Off to automatically balance volume, remove rumble, and cut background hum while preserving your speech patterns.
• Multilingual Accents: Configure spoken languages (e.g., "English, Hindi") so jr.X perfectly understands mixed accents.
• Wake Word: Respond to default phrase “hey junior x”. The assistant sleeps until it hears the phrase, then stays awake briefly. Detection is entirely offline.
• Push to Talk: Bind a custom key (Default: F9) or use the on-screen Hold to talk button. Both options can run concurrently or be disabled entirely for always-listening mode.

🖥️ Desktop Control & Virtual Pointer

• Screen Interaction: jr.X actively reads your display and controls your mouse and keyboard.
• Visual Anchor: A glowing virtual pointer displays precisely where the assistant is clicking or typing.
• Safety & Overrides: Enable optional settings to require explicit user confirmation before the AI takes physical control. You can immediately abort its action at any time by moving your mouse cursor to the top-left corner of your screen.

🌐 Browser Automation

• Playwright Engine: Full web automation capabilities out-of-the-box.
• Reliability: Handles complex multi-tab management, bypasses invasive pop-ups, and features auto-recovery if a browser window crashes.

📱 Phone Remote

• Setup: Navigate to Settings → Remote and toggle Allow control from my phone.
• Local Connection: Scan the generated QR code using a phone connected to the exact same Wi-Fi network.
• Usage: The phone's web page mirrors the chat interface and results. Speak or type commands directly from your mobile device. This operates entirely on your local network protected by a unique token inside the QR link (Approval prompts still safely appear on the PC).

🎛️ Background, Tray, & Controls

• System Tray: Choose to let jr.X minimize cleanly into the system tray when closing the primary window. Click the tray icon to bring it back instantly.
• Start Hidden: Launch option to send jr.X straight to the system tray on PC startup without breaking focus.
• Preview Card: When compiling terminal items or running heavy background research, a compact floating status card anchors to the top-right corner of your monitor. You can drag and resize it freely.
• Instant Interrupt: Press the ⏹ Stop button, hit Esc, use the global hotkey F8, use the system tray context menu, or simply say "stop" out loud to instantly terminate active terminal operations, scripts, browser workflows, or vocal replies.
• System Logs: Saved locally at ~/.xpectation/jrx.log.

🧩 Plugins

• Built-in Suite: Toggable modular plugins for terminal management, web research, desktop overrides, browser engines, document reviews, spreadsheet mapping, quizzes, games, Telegram remotes, chat assistance, hydration reminders, and more.

Engines & Models (Settings → Engine)


🧠 Choose Your Brain

• Model Ladder: Run an ordered fallback list of models. If your primary choice hits a rate limit, timeout, or network outage, jr.X auto-steps down to the next model in line. Offline or failed models are temporarily parked and tested for recovery later.
• Supported Integrations: Connect seamlessly to Gemini or any OpenAI-compatible server architecture (Ollama, LM Studio, llama.cpp, vLLM, OpenAI, Groq, DeepSeek, Mistral, xAI, OpenRouter, or custom network endpoints).

🛠️ Offline LLMs & Local Voice (Under Construction)

• Local Models: Connect to Ollama, LM Studio, or llama.cpp to install and initialize models straight from our in-app directory with visible progress tracking.
• Local Voice: Toggle fully offline vocal workflows combining Whisper (Speech-to-Text) and Piper (Text-to-Speech) spanning dozens of dialect options.
• Note: While these features are in a fully working zone, they are actively being polished and optimized. You may encounter minor imperfections as they undergo active development.

Executable Environment Requirements

The installer bundles jr.X internally. Certain features depend on native system software being present on the target host computer:

Feature	Target PC Requirement
Browser Control	Google Chrome or Microsoft Edge installed on the system
Local LLM Engines	Ollama or LM Studio running locally on the system
Mouse / Screen Control	Works natively out of the box (Windows)
Phone Remote Companion	Must allow jr.X through Windows Firewall (Private network profile)
Local Voice Processing	Optional; downloadable models found in Settings → Engine


Diagnostics & Troubleshooting

Run a health self-test by opening a terminal window inside the installation root path and running:
cmd
jr.X.exe --selftest
Use code with caution.

License

Proprietary. Free for personal non-commercial use only. See LICENSE for full terms. All rights reserved by MasterX.
