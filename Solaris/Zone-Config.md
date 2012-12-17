# Zone creation and configuration
```text
~# zonecfg -z ZONE1
Use ‘create’ to being configuring a zone
zonecfg:ZONE1> create
zonecfg:ZONE1> set zonepath=/export/zones/ZONE1
zonecfg:ZONE1> set autoboot=true
zonecfg:ZONE1> add net
zonecfg:ZONE1:net> set address=ZONE1
zonecfg:ZONE1:net> set physical=nxge0
zonecfg:ZONE1:net> end
zonecfg:ZONE1> add dedicated-cpu
zonecfg:ZONE1:dedicated-cpu> set ncpus=4-8
zonecfg:ZONE1:dedicated-cpu> end
zonecfg:ZONE1> add capped-memory
zonecfg:ZONE1:capped-memory> set physical=4g
zonecfg:ZONE1:capped-memory> set swap=512m
zonecfg:ZONE1:capped-memory> set locked=512m
zonecfg:ZONE1:capped-memory> end
zonecfg:ZONE1> verify
zonecfg:ZONE1> commit
zonecfg:ZONE1> exit
```
