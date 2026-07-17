## get-urls
> Automated URL discovery and XSS reconnaissance pipeline using waybackurls, gau, httpx, katana, Gxss, kxss, uro, and Dalfox.

# X-ploit URL Recon Pipeline

## Workflow

```mermaid
flowchart TD

A[domains.txt] --> B[waybackurls]
A --> C[gau]

B --> D[way.txt]
C --> E[gau.txt]

D --> F[all_urls.txt]
E --> F

F --> G[Scope Filtering]
G --> H[scoped_urls.txt]

H --> I[httpx]
I --> J[live_allurls.txt]

J --> K[Katana<br/>-jc -d 3 -kf all]
K --> L[katana.txt]

J --> M[katana_merge.txt]
L --> M

M --> N[Scope Filtering]
N --> O[live_allurls.txt<br/>Final]

O --> P[XSS Filtering<br/>grep params<br/>uro<br/>Gxss<br/>kxss]

P --> Q[xss_output.txt]

Q --> R[qsreplace]
R --> S[final.txt]

S --> T[Dalfox]
T --> U[dalfox_results.txt]
```

## Files Generated

| File | Description |
|------|-------------|
| `way.txt` | First stage - URLs gathered from waybackurls |
| `gau.txt` | Second stage - URLs gathered from gau |
| `all_urls.txt` | Merge of way.txt + gau.txt (unique URLs) |
| `scoped_urls.txt` | URLs filtered to only targets inside scope |
| `live_allurls.txt` | Alive URLs after httpx check |
| `katana.txt` | New URLs discovered by Katana crawling |
| `live_allurls.txt` | Final live URL list after merging Katana results |

## Pipeline

```
Waybackurls + GAU
        |
        v
   URL Collection
        |
        v
   Scope Filtering
        |
        v
      httpx
        |
        v
     Katana
        |
        v
 Parameter Discovery
        |
        v
     Dalfox
        |
        v
    XSS Results
```
