# 🎥 yt-dlp Full Guide (Windows | macOS | Linux)

📺 Also, check out my YouTube channel for more tutorials: Codebash YouTube

yt-dlp is a powerful open-source tool for downloading videos and audio from YouTube and many other sites.\
This guide provides **detailed setup and usage instructions** for **Windows, macOS, and Linux**.

---

## 📑 Table of Contents

- [Windows](#️-windows)
  - [Installation](#installation-windows)
  - [Usage](#usage-windows)
- [macOS](#-macos)
  - [Installation](#installation-macos)
  - [Usage](#usage-macos)
- [Linux](#-linux)
  - [Installation](#installation-linux)
  - [Usage](#usage-linux)
- [Common Commands](#⚡-common-commands)
- [Updating yt-dlp](#🔄-updating-yt-dlp)
- [Troubleshooting](#🛠️-troubleshooting)
- [Thanks](#-thanks)

---

## 🖥️ Windows

### Installation (Windows)

1. **Download the executable**

   - Go to 👉 [yt-dlp Releases](https://github.com/yt-dlp/yt-dlp/releases/latest)
   - Download `yt-dlp.exe`

2. **Place the file**

   - Put `yt-dlp.exe` in a folder, e.g., `C:\yt-dlp`

3. **Add to PATH (optional but recommended)**

   - Search *Environment Variables* in Windows.
   - Edit `Path` → Add `C:\yt-dlp`.
   - Now you can run `yt-dlp` from any directory.

4. **Alternative: Install with pip**

   ```bash
   pip install -U yt-dlp
   ```

### Usage (Windows)

Open **Command Prompt (cmd)** or **PowerShell** and run:

```bash
yt-dlp https://youtube.com/watch?v=abcd1234
```

📸 Example:\


---

## 🍏 macOS

### Installation (macOS)

**Using Homebrew (Recommended):**

```bash
brew install yt-dlp
```

**Using pip:**

```bash
pip3 install -U yt-dlp
```

**Manual binary installation:**

```bash
sudo curl -L https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp -o /usr/local/bin/yt-dlp
sudo chmod a+rx /usr/local/bin/yt-dlp
```

### Usage (macOS)

```bash
yt-dlp "https://youtube.com/watch?v=abcd1234"
```

📸 Example:\


---

## 🐧 Linux

### Installation (Linux)

**Using pip:**

```bash
pip install -U yt-dlp
```

**Download binary:**

```bash
sudo wget https://github.com/yt-dlp/yt-dlp/releases/latest/download/yt-dlp -O /usr/local/bin/yt-dlp
sudo chmod a+rx /usr/local/bin/yt-dlp
```

**Arch Linux (AUR):**

```bash
yay -S yt-dlp
```

### Usage (Linux)

```bash
yt-dlp https://youtube.com/watch?v=abcd1234
```

📸 Example:\


---

## ⚡ Common Commands

```bash
# Download video
yt-dlp <video_url>

# Download audio only (mp3)
yt-dlp -x --audio-format mp3 <video_url>

# Custom output filename
yt-dlp -o "%(title)s.%(ext)s" <video_url>

# Download playlist
yt-dlp <playlist_url>

# Download specific items from playlist
yt-dlp <playlist_url> --playlist-items 1,3,5

# Download with subtitles
yt-dlp --write-subs --sub-lang en <url>

# Limit download speed
yt-dlp --limit-rate 500K <url>

# Resume interrupted download
yt-dlp -c <url>
```

---

## 🔄 Updating yt-dlp

- **Windows (pip users):**
  ```bash
  pip install -U yt-dlp
  ```
- **Linux/macOS (binary users):**
  ```bash
  yt-dlp -U
  ```

---

## 🛠️ Troubleshooting

- **SSL errors** → Update Python to the latest version.
- **Permission denied** → Run with `sudo` (Linux/macOS) or as **Administrator** (Windows).
- **Outdated extractor** → Run:
  ```bash
  yt-dlp -U
  ```

---

## 🙏 Thanks

Thanks for using the **yt-dlp full guide ❤️**\
If you found this helpful, don’t forget to ⭐ star the repo and share 🚀

---

