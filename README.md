# zapgix
Zabbix Agent - PostgreSQL

# Dependencies
Only tested on Ubuntu 18.04 LTS and Postgresql 10

# Deploy
## Zabbix

Create a zabbix user in the postgresql database.
Enable pg_buffercache for PostgreSQL

```
#~ su - postgresql
#~ createuser -s zabbix
#~ CREATE EXTENSION pg_buffercache;
#~ exit
```

Needs to be superuser for wal-count to work otherwise 
GRANT pg_read_all_stats TO zabbix;
should be enough.

Then you can run the deploy_zabbix script

```
#~ git clone https://github.com/sergiotocalini/zapgix.git
#~ sudo ./zapgix/deploy_zabbix.sh
#~ sudo systemctl restart zabbix-agent
```

*Note: the installation has to be executed on the zabbix agent host and you have to import the template on the zabbix web. The default installation directory is /etc/zabbix/scripts/agentd/zapgix/*
