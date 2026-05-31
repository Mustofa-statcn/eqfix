# ✦ EqFix — AI Equation Repair Tool

> Paste any broken or garbled math from an AI chat, PDF, or copied text — get back clean **LaTeX**, **MathML**, and **Unicode** with a live rendered preview.

![EqFix Screenshot](https://placehold.co/800x420/0d0d0f/a599ff?text=EqFix+%E2%80%94+Equation+Repair+Tool&font=montserrat)

---

## 🔍 What It Does

When you copy equations from AI responses, PDFs, or plain-text sources, the formatting is usually broken — Greek letters become question marks, fractions collapse into ASCII slashes, and subscripts vanish. EqFix sends the raw text to Claude AI and returns:

- ✅ Valid **LaTeX** (inline `$...$` and display `$$...$$` ready)
- ✅ Well-formed **MathML** markup
- ✅ Readable **Unicode** math (∫ ∑ √ × ≤ …)
- ✅ A **live rendered preview** via MathJax
- ✅ A plain-English **explanation** of what the equation means

---

## ✨ Features

| Feature | Details |
|---|---|
| 🤖 AI-powered | Uses Claude Sonnet via the Anthropic API |
| 🎨 Dark & Light theme | Toggle button with preference saved to localStorage |
| 📋 One-click copy | Copy LaTeX, MathML, Unicode, inline, or display format |
| 👁️ Live preview | MathJax renders the equation so you can verify it |
| ⌨️ Keyboard shortcut | `Ctrl+Enter` / `Cmd+Enter` to fix |
| 💡 6 example equations | From E=mc² to Maxwell's equations |
| 📱 Responsive | Works on desktop and mobile |
| 🔒 No data stored | Everything is processed in-browser per request |

---

## 🚀 Live Demo

👉 **[eqfix.Mustofa-statcn.github.io](https://Mustofa-statcn.github.io/eqfix)**

---

## 🛠️ Tech Stack

- **Vanilla HTML/CSS/JS** — zero build step, zero dependencies to install
- **Anthropic Claude API** (`claude-sonnet-4-20250514`) — equation parsing & conversion
- **MathJax 3** — browser-side LaTeX rendering
- **Google Fonts** — DM Serif Display, DM Sans, Fira Code

---

## 📦 Project Structure

```
eqfix/
├── index.html      ← The entire app (single file)
└── README.md       ← This file
```

---

## ⚡ Getting Started Locally

No build tools needed. Just open the file:

```bash
git clone https://github.com/your-username/eqfix.git
cd eqfix
open index.html        # macOS
# or
start index.html       # Windows
# or
xdg-open index.html    # Linux
```

> **Note:** The Anthropic API key is injected automatically when served from Claude.ai. For standalone hosting, see [API Key Setup](#-api-key-setup) below.

---

## 🔑 API Key Setup

The app calls the Anthropic API directly from the browser. To host it yourself:

1. Get an API key from [console.anthropic.com](https://console.anthropic.com)
2. Open `index.html` and find the `fetch` call (around line 690)
3. Add your key to the headers:

```js
headers: {
  "Content-Type": "application/json",
  "x-api-key": "sk-ant-YOUR_KEY_HERE",      // ← add this
  "anthropic-version": "2023-06-01",          // ← add this
  "anthropic-dangerous-direct-browser-access": "true"  // required for browser
},
```

> ⚠️ **Security note:** Embedding an API key in a public HTML file exposes it to anyone who views the source. For production use, proxy the API call through a serverless function (Cloudflare Workers, Vercel Edge, etc.) that keeps the key server-side.

---

## 🌐 Deploying to GitHub Pages

### Step 1 — Create the repository

1. Go to [github.com/new](https://github.com/new)
2. Name it `eqfix` (or anything you like)
3. Set visibility to **Public**
4. Leave "Initialize with README" **unchecked** (you have your own)
5. Click **Create repository**

### Step 2 — Push your files

```bash
# In your project folder:
git init
git add index.html README.md
git commit -m "Initial commit — EqFix equation repair tool"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/eqfix.git
git push -u origin main
```

### Step 3 — Enable GitHub Pages

1. In your repo, go to **Settings → Pages**
2. Under **Source**, select **Deploy from a branch**
3. Choose branch: `main`, folder: `/ (root)`
4. Click **Save**
5. Wait ~60 seconds, then visit:

```
https://Mustofa-statcn.github.io/eqfix/
```

GitHub will show the live URL at the top of the Pages settings once it's deployed.

### Step 4 — Update the README link

Edit `README.md` and replace the placeholder demo URL with your real GitHub Pages URL, then:

```bash
git add README.md
git commit -m "Update live demo link"
git push
```

---

## 🔄 Updating the App

After making changes to `index.html`:

```bash
git add index.html
git commit -m "Your description of the change"
git push
```

GitHub Pages redeploys automatically within about a minute.

---

## 🧪 Example Inputs

| Broken input | What EqFix returns |
|---|---|
| `E = mc^2` | `E = mc^{2}` |
| `x = (-b ± √(b²-4ac)) / 2a` | `x = \frac{-b \pm \sqrt{b^2 - 4ac}}{2a}` |
| `∫_{-∞}^{∞} e^(-x²) dx = √π` | `\int_{-\infty}^{\infty} e^{-x^2}\,dx = \sqrt{\pi}` |
| `∇ × B = μ₀J + μ₀ε₀ ∂E/∂t` | `\nabla \times \mathbf{B} = \mu_0 \mathbf{J} + \mu_0 \varepsilon_0 \frac{\partial \mathbf{E}}{\partial t}` |

---

## 🤝 Contributing

Pull requests are welcome! To contribute:

1. Fork the repo
2. Create a branch: `git checkout -b feature/my-improvement`
3. Make your changes to `index.html`
4. Commit: `git commit -m "Add my improvement"`
5. Push: `git push origin feature/my-improvement`
6. Open a Pull Request on GitHub

---

## 📄 License

MIT — do whatever you want with it. Attribution appreciated but not required.

---

## 🙏 Credits

- Built with [Claude](https://claude.ai) by Anthropic
- Math rendering by [MathJax](https://www.mathjax.org/)
- Fonts by [Google Fonts](https://fonts.google.com/)
