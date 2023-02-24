# zabbix_xmr_mining
Zabbix Tools to Monitor XMR Mining Stats

## p2pool_stats
### Requirements
* ruby
* vcr gem (built with version 6.1.0)
* webmock gem (built with version 3.18.1)
### Setup
* Place the following in your zabbix-agent.conf
```
AllowKey=system.run[/usr/local/bin/p2pool_stats*]
```
* Add a User Defined Macro in your Zabbix called {$XMR_ADDR} with your XMR mining address for the value
* Ensure that /tmp/p2pool_data exists before running p2pool
* Use the following switches when you start p2pool: ```--data-api /tmp/p2pool_data --local-api```
* Place p2pool_stats into /usr/local/bin and make sure it is executable for the Zabbix user
* Create an Item (type Text) in Zabbix with Key
```system.run[/usr/local/bin/p2pool_stats {$XMR_ADDR}]```

## xmr_hr
### Requirements
* jq
### Setup
* Place the following in your zabbix-agent.conf
```
AllowKey=system.run[/usr/local/bin/xmr_hr*]
```
* Use the following switches when you start XMRig: "--http-host=127.0.0.1 --http-port=80"
* Place xmr_hr into /usr/local/bin and make sure it is executable for the Zabbix user
* Create 3 Items (type Float) in Zabbix with Keys:
```
system.run[/usr/local/bin/xmr_hr -1]
system.run[/usr/local/bin/xmr_hr -2]
system.run[/usr/local/bin/xmr_hr -3]
```
