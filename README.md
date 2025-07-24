# 🗣️ Voice Recognition & Translation Assistant

This Python-based project uses **Selenium**, **Speech Recognition (via Web Speech API)**, and **mtranslate** to create a browser-based voice recognition tool that captures spoken input, translates it to English, and formats it for downstream processing.

## 🚀 Features

- Real-time speech-to-text using browser’s speech recognition (Web Speech API)
- Customizable input language via `.env` file
- Automatic punctuation and formatting of queries
- Translation to English using `mtranslate`
- Headless Chrome browser integration with fake media input for automation
- Status handling via file I/O for inter-process communication

## 🧰 Requirements

- Python 3.7+
- Google Chrome
- ChromeDriver (auto-managed via `webdriver_manager`)
- `.env` file with input language setting (e.g. `InputLanguage=en-US`)

## 📦 Installation

1. **Clone this repo or download the files.**

2. **Install dependencies:**
   ```bash
   pip install selenium webdriver-manager mtranslate
   ```

3. **Create the required folder structure:**
   ```
   .
   ├── Data/
   │   └── audio.html         # Auto-generated
   ├── Frontend/
   │   └── files/
   │       └── Status.data    # Auto-generated
   ├── .env
   └── speech_to_text.py
   ```

4. **Create a `.env` file in the root directory:**
   ```
   InputLanguage=en-US
   ```

   Replace `en-US` with any valid BCP-47 language code (e.g., `fr-FR`, `es-ES`, `hi-IN`).

## 🧪 How It Works

1. The script creates a simple HTML file using the Web Speech API for voice input.
2. It opens the page in a headless Chrome browser with fake mic input.
3. Captured speech is displayed in the browser and stored for further usage.
4. Transcribed text is:
   - Translated to English
   - Properly punctuated
   - Stored for use by other components (e.g., voice assistant, chatbot)

## 🧩 Functions Overview

| Function               | Purpose                                           |
|------------------------|---------------------------------------------------|
| `SetAssistantStatus()` | Writes assistant status to `Status.data` file.    |
| `QueryModifier()`      | Adds punctuation and capitalizes the input text.  |
| `UniversalTranslator()`| Translates any text to English using `mtranslate`.|

## 🛠️ Chrome Options in Use

The script configures Chrome WebDriver with the following options:

- `--headless=new`: Run Chrome in headless mode.
- `--use-fake-ui-for-media-stream`: Automatically grant mic permissions.
- `--use-fake-device-for-media-stream`: Use fake audio input for automation.
- Other options that disable unnecessary services for better performance.

## 📌 Notes

- Web Speech API is only supported in **Chrome**, not Firefox or Safari.
- Headless mode may not work well with real mic input — use regular mode if needed.
- Ensure mic permissions are granted for Chrome if running non-headless.

## 🧼 TODOs / Improvements

- Add support for saving full transcript history.
- Add real-time console logging of voice input.
- Replace `mtranslate` with a more accurate translation API.
- Improve punctuation logic for complex queries.

##
## Feel free to Use, and Let me Know if any modification needs 
