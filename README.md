# 💀 X-ploit-666

<p align="center">
  <img src="https://img.shields.io/badge/Bash-Automation-green?style=for-the-badge">
  <img src="https://img.shields.io/badge/Web%20Recon-XSS%20Pipeline-red?style=for-the-badge">
  <img src="https://img.shields.io/badge/Security-Bug%20Bounty-orange?style=for-the-badge">
</p>

<p align="center">
  Automated URL discovery, filtering, crawling, reflection analysis, and XSS testing pipeline.
</p>


## ⚡ Overview

**X-ploit-666** is an automated Bash-based reconnaissance pipeline designed for authorized security testing and bug bounty workflows.

The tool combines multiple powerful recon and XSS discovery utilities into a single automated workflow:

- Historical URL discovery
- URL aggregation and deduplication
- Scope filtering
- Live host validation
- JavaScript-aware crawling
- Parameter reflection analysis
- XSS payload preparation
- Automated scanning with Dalfox


The goal is to reduce manual recon time and quickly identify potentially interesting XSS attack surfaces.


---

# 🚀 Features

## 🔎 URL Discovery

Collects URLs from multiple sources:

- `waybackurls`
- `gau`

Automatically merges and removes duplicates.


## 🎯 Scope Filtering

Automatically filters discovered URLs according to your target scope.

Example:
Example:

```
example.com
```

Will include:

```
https://example.com
https://api.example.com
https://shop.example.com/product?id=1
```

While excluding unrelated domains.


---

## 🌐 Live URL Detection

Checks which URLs are currently reachable using:

```bash
httpx
```

Supports common useful status codes:

```
200
301
302
307
308
401
403
429
```


---

## 🕷️ Advanced Crawling

Uses:

```bash
katana
```

with:

- JavaScript crawling
- Depth control
- Known file discovery


Configuration:

```bash
-depth 3
-jc
-kf all
```


---

## 💉 XSS Parameter Discovery

Prepares URLs for XSS testing using:

```bash
gf xss
uro
Gxss
kxss
```

The pipeline searches for:

- Potential XSS parameters
- Reflected input points
- Interesting query strings


---

## 🦊 Automated XSS Testing

Final targets are automatically passed to:

```bash
Dalfox
```

for vulnerability verification.


---

# 📌 Workflow

```
             Target Domains
                   |
                   v
          +----------------+
          |  waybackurls   |
          +----------------+
                   |
                   v
          +----------------+
          |      gau       |
          +----------------+
                   |
                   v
          URL Deduplication
                   |
                   v
          Scope Filtering
                   |
                   v
               httpx
                   |
                   v
              Katana Crawl
                   |
                   v
          Parameter Analysis
                   |
                   v
             Gxss / kxss
                   |
                   v
                Dalfox
                   |
                   v
          XSS Results
```


---

# 🛠️ Installation

## Requirements

The following tools must be installed:


### Recon Tools

```bash
waybackurls
gau
katana
httpx
```


### XSS Tools

```bash
gf
uro
Gxss
kxss
dalfox
```


### Additional Utilities

```bash
toilet
figlet
grep
sed
sort
```


---

# 📥 Installing Dependencies

Example:

```bash
go install github.com/tomnomnom/waybackurls@latest

go install github.com/lc/gau/v2/cmd/gau@latest

go install github.com/projectdiscovery/httpx/cmd/httpx@latest

go install github.com/projectdiscovery/katana/cmd/katana@latest

go install github.com/hahwul/dalfox/v2@latest
```


Install GF:

```bash
go install github.com/tomnomnom/gf@latest
```


Install uro:

```bash
pip3 install uro
```


---

# 📂 Installation

Clone the repository:

```bash
git clone https://github.com/USERNAME/X-ploit-666.git
```

Enter directory:

```bash
cd X-ploit-666
```

Make executable:

```bash
chmod +x xploit.sh
```


---

# ▶️ Usage

Create a target file:

```
targets.txt
```

Example:

```text
example.com
api.example.com
```

Run:

```bash
./xploit.sh targets.txt
```


---

# 📁 Output Files

After execution, the following files are generated:


| File | Description |
|------|-------------|
| `wayback_urls.txt` | URLs collected from Wayback Machine |
| `gau.txt` | URLs collected from GAU |
| `all_urls.txt` | Combined unique URLs |
| `scoped_urls.txt` | URLs matching target scope |
| `live_urls.txt` | Active reachable URLs |
| `katana.txt` | URLs discovered by crawler |
| `final_live_urls.txt` | Final live URL collection |
| `xss_output.txt` | Reflection analysis results |
| `dalfox_targets.txt` | Prepared XSS targets |
| `dalfox_results.txt` | Dalfox scan results |


---

# 🖥️ Example Output

```text
[+] Gathering URLs From waybackurls...
[+] 5423 URLs Gathered

[+] Gathering URLs From gau...
[+] 3912 URLs Gathered

[+] Combining All Gathered URLs...
[+] 8120 Unique URLs

[+] Filtering In-Scope URLs...
[+] 6544 URLs are in scope

[+] Checking for Live URLs...
[+] 2301 Live URLs

[+] Crawling Live URLs With Katana...
[+] 875 URLs Gathered

[+] Preparing URLs for XSS...
[+] 42 URLs ready for Dalfox

[+] Starting Dalfox...
```


---

# ⚙️ Customization

You can modify:


## Katana Depth

Current:

```bash
-d 3
```

Increase:

```bash
-d 5
```


## HTTP Status Codes

Current:

```bash
-mc 200,301,302,307,308,401,403,429
```

Modify depending on your testing requirements.


---

# ⚠️ Legal Disclaimer

This tool is intended for:

✅ Bug bounty programs  
✅ Authorized penetration tests  
✅ Security research on owned systems  


Do **not** use this tool against systems without explicit permission.

The author is not responsible for misuse or illegal activity.


---

# 🧠 Future Improvements

Possible additions:

- [ ] Subdomain enumeration module
- [ ] Nuclei vulnerability scanning
- [ ] Secret detection
- [ ] JS endpoint extraction
- [ ] Parameter mining with Arjun
- [ ] Automated screenshots
- [ ] HTML reporting
- [ ] Multi-threaded execution


---

# 👤 Author

**X-ploit-666**

Security Research / Bug Bounty Automation


---

# ⭐ Support

If you find this project useful:

- Give it a ⭐
- Report bugs
- Suggest improvements


Happy Hunting 💀
