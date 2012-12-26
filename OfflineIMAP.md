# OfflineIMAP  
For synchronizing shizzle!  

## Generating CA Certificates  
### Why ```sslcacertfile``` and not ```cert_fingerprint``` ?  
Because fingerprints change. Nuff said.  
  
### Using OpenSSL  
```bash
$ openssl s_client -CApath /etc/ssl/certs -connect ${hostname}:imaps -showcerts | perl -ne 'print if /BEGIN/../END/; print STDERR if /return/' > $sslcacertfile 
^D
```
