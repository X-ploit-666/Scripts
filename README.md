## get-urls


:domains.txt
    |
    |
    +--> waybackurls
    |        |
    |        v
    |     way.txt
    |
    |
    +--> gau
             |
             v
          gau.txt

way.txt + gau.txt
        |
        v
   sort -u
        |
        v
   all_urls.txt

all_urls.txt
        |
        v
   Scope filtering
        |
        v
   scoped_urls.txt

scoped_urls.txt
        |
        v
      httpx
        |
        v
   live_allurls.txt

live_allurls.txt
        |
        v
      katana
        |
        v
    katana.txt

live_allurls.txt + katana.txt
        |
        v
   katana_merge.txt

Scope filtering again
        |
        v
   live_allurls.txt (updated)

live_allurls.txt
        |
        v
   XSS filtering:
      grep extensions
      grep parameters =
      uro
      Gxss
      kxss
        |
        v
   xss_output.txt

xss_output.txt
        |
        v
   qsreplace
        |
        v
   final.txt

final.txt
        |
        v
     dalfox
        |
        v
 dalfox_results.txt

 
