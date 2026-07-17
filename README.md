## get-urls

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

| File | Description | Lines |
|------|-------------|------:|
| `way.txt` | URLs from waybackurls | 22371 |
| `gau.txt` | URLs from gau | 10542 |
| `all_urls.txt` | Unique URLs from waybackurls + gau | 22371 |
| `scoped_urls.txt` | URLs filtered to target scope | 22338 |
| `live_allurls.txt` | Live URLs after httpx | 13379 |
| `katana.txt` | URLs discovered by Katana crawling | 240093 |
| `final.txt` | URLs ready for Dalfox | - |
| `dalfox_results.txt` | XSS scan results | - |

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
