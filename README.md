<a href="https://github.com/canarywatch/canary"><img src="https://raw.githubusercontent.com/canarywatch/canary/main/site/assets/brand/banner.png" width="100%" alt="canary. Every new package on npm and PyPI, read before anyone installs it."></a>

<div align="center">
<a href="https://github.com/canarywatch/canary"><img src="https://img.shields.io/badge/canary-the%20wall-FFD23F?style=for-the-badge&labelColor=0A0B0D" alt="the wall"></a>
<a href="https://github.com/canarywatch/canary"><img src="https://img.shields.io/badge/agent-source-0A0B0D?style=for-the-badge&logo=github&logoColor=FFD23F&labelColor=0A0B0D" alt="agent source"></a>
<a href="https://canary.162-35-122-197.sslip.io/state.json"><img src="https://img.shields.io/badge/agent-live%20json-3DDC84?style=for-the-badge&labelColor=0A0B0D" alt="live json"></a>
<img src="https://img.shields.io/github/followers/canarywatch?style=for-the-badge&logo=github&logoColor=FFD23F&color=0A0B0D&labelColor=0A0B0D&label=followers" alt="followers">
<a href="https://github.com/canarywatch/canary/stargazers"><img src="https://img.shields.io/github/stars/canarywatch/canary?style=for-the-badge&logo=github&logoColor=FFD23F&color=0A0B0D&labelColor=0A0B0D&label=stars" alt="stars"></a>
</div>

<br>

### 🐤 What canary is

```toml
[canary]
is = "every new release on npm and PyPI, read before anyone installs it"
reads = "install hooks, hidden layers, secret files next to a network call, wallet grabs, shell shapes, stray binaries, lookalike names"
never = "installs or runs a package. bytes are read from an in-memory archive, nothing else"
tripped = "our rules' word: enough weight, with the file and the line that did it"
confirmed = "the public record's word: a malware advisory at OSV / OpenSSF for exactly that version"
trusted = "a year old, or 50k downloads a week: heuristics alone never put it on the wall"
check = "paste a package.json, a lockfile or a requirements.txt: what is on the record, nothing stored"
mint = "posted here and on the project account on launch day"
```

### 🧰 Stack

<p align="center">
<img src="https://img.shields.io/badge/Python-0A0B0D?style=for-the-badge&logo=python&logoColor=FFD23F" alt="Python">
<img src="https://img.shields.io/badge/npm-0A0B0D?style=for-the-badge&logo=npm&logoColor=FFD23F" alt="npm">
<img src="https://img.shields.io/badge/PyPI-0A0B0D?style=for-the-badge&logo=pypi&logoColor=FFD23F" alt="PyPI">
<img src="https://img.shields.io/badge/OSV.dev-0A0B0D?style=for-the-badge&logoColor=FFD23F" alt="OSV">
<img src="https://img.shields.io/badge/Caddy-0A0B0D?style=for-the-badge&logo=caddy&logoColor=FFD23F" alt="Caddy">
</p>
<p align="center">
<img src="https://img.shields.io/badge/systemd%20sandbox-0A0B0D?style=for-the-badge&logo=linux&logoColor=FFD23F" alt="systemd">
<img src="https://img.shields.io/badge/Solana-0A0B0D?style=for-the-badge&logo=solana&logoColor=FFD23F" alt="Solana">
<img src="https://img.shields.io/badge/Netlify-0A0B0D?style=for-the-badge&logo=netlify&logoColor=FFD23F" alt="Netlify">
<img src="https://img.shields.io/badge/Claude%20Code-0A0B0D?style=for-the-badge&logo=claude&logoColor=FFD23F" alt="Claude Code">
</p>

### ⚙️ How a package gets on the wall

| Step | What happens |
|---|---|
| 📡 **Feed** | npm's `_changes` stream and PyPI's update feeds, polled every 20 seconds. New name or new version, it is fetched |
| 📦 **Bytes** | the tarball is unpacked **in memory** by an extractor that drops `..`, absolute paths, symlinks and oversize files. Nothing touches the disk, nothing is imported |
| 🔎 **Read** | seven rules, each hit keeps its file, line and text. Base64 blobs that decode to code are read too. Tests, docs and CI files count for nothing unless an install script points at them |
| ⚖️ **Score** | a rule counts once, at its strongest hit. Score 7 with one strong line puts a new package on the wall as **tripped**. Three weak hits never do |
| 📜 **Record** | every package is looked up at OSV. A hit is **confirmed**. A tripped catch is re-asked every six hours for a month, and the feed says how many hours after the rules the record caught up |

> A name never goes on the wall without its lines. A wrong catch is cleared by a person, in public, with the reason. The recall number is published even when it is unflattering.

### 📏 The rules

| rule | weight | trips on |
|---|---|---|
| `install-hook` | 1–5 | a script that runs at install time; 5 when it downloads something or is a `.pth` |
| `obfuscation` | 2–5 | eval over decoded data, hex runs, base64 that decodes to code, exec over a literal payload |
| `exfil` | 1–5 | reads secret files **and** sends somewhere, in one file; a webhook alone is 4 |
| `wallet` | 4–5 | a hardcoded address next to clipboard access, or reaching into browser credential storage |
| `shell` | 1–5 | reverse shell shapes, download-and-run, persistence with a shell; official installers count 1 |
| `binary` | 2–3 | executables shipped with an install hook and no native build declared |
| `typosquat` | 2–4 | a new name one keystroke from a popular one; scoped names are their own namespace |

### 🚫 Hard limits

<div align="center">
<img src="https://img.shields.io/badge/never-installs%20or%20runs%20a%20package-FF4D5E?style=for-the-badge&labelColor=0A0B0D" alt="never installs">
<img src="https://img.shields.io/badge/never-a%20name%20without%20its%20lines-FF4D5E?style=for-the-badge&labelColor=0A0B0D" alt="never without lines">
<img src="https://img.shields.io/badge/never-confirmed%20on%20its%20own%20word-FF4D5E?style=for-the-badge&labelColor=0A0B0D" alt="never confirmed alone">
<img src="https://img.shields.io/badge/never-keeps%20what%20you%20paste-FF4D5E?style=for-the-badge&labelColor=0A0B0D" alt="never keeps">
<img src="https://img.shields.io/badge/never-posts%2C%20never%20trades-FF4D5E?style=for-the-badge&labelColor=0A0B0D" alt="never posts">
</div>

<br>

<p align="center"><a href="https://github.com/canarywatch/canary"><img src="https://img.shields.io/badge/github.com%2Fcanarywatch%2Fcanary-open%20the%20repo-FFD23F?style=for-the-badge&logo=github&logoColor=0A0B0D&labelColor=0A0B0D" alt="canary repo"></a></p>

<p align="center"><sub>the rules as the agent runs them. the public json: <a href="https://canary.162-35-122-197.sslip.io/state.json">state</a> · <a href="https://canary.162-35-122-197.sslip.io/catches.json">catches</a> · <a href="https://canary.162-35-122-197.sslip.io/events.json">events</a> · <a href="https://canary.162-35-122-197.sslip.io/rules.json">rules</a></sub></p>

<p align="center"><sub>built in public · <a href="https://github.com/canarywatch/canary">canarywatch/canary</a></sub></p>
