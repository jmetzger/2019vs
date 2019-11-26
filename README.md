# 2019vs
Schulung MariaDB Galera Cluster 

## Doku 

http://schulung.t3isp.de/documents/pdfs/mariadb/mariadb-galera-cluster.pdf

## 1. License MaxScale 

```
Version is going to be GPL on Change Data or after 4 years (whatever is earlier) 

https://mariadb.com/projects-using-bsl-11/

Change Date: 2020-01-01 (MaxScale 2.2), 2021-09-01 (MaxScale 2.4.2). For MaxScale 2.4.3 and above, change date is four years from release date.

Before that in BSL 1.1 and 1.0 (from MaxScale 2.0 on), may be used without License Coss
with LESS than 3 Servers 
```

## 2. Comparison Feature ProxySQL and MaxScale 

https://mariadb.com/wp-content/uploads/2019/10/mariadb-maxscale-proxysql-comparison_datasheet_1043.pdf


## 3. Performance Galera Cluster  

### 3a. RTT determines tps 

Good article on performance MaxScale 

https://severalnines.com/database-blog/improve-performance-galera-cluster-mysql-or-mariadb

as is:
tps restricted by RTT (Round Trip Time)

Quote ():
"[In a Galera cluster] a given row can’t be modified more than once per RTT"

Hence, transactions per second can be estimated by dividing RTT (in second) into 1 second:

Minimum tps: 1 / 0.00134 (max RTT) = 746.26 ~ 746 tps
Average tps: 1 / 0.000431 (avg RTT) = 2320.19 ~ 2320 tps
Maximum tps: 1 / 0.000111 (min RTT) = 9009.01 ~ 9009 tps

Slowest node tears performance down. 

## 3b. Performance metrics galera cluster 

https://severalnines.com/database-blog/monitoring-galera-cluster-mysql-or-mariadb-understanding-metrics-updated

## 4. Start after total crash of cluster 
cat grastate.dat 
# GALERA saved state
version: 2.1
uuid:    930fb23a-0f7f-11ea-ab82-23d67453fbbc
seqno:   -1
safe_to_bootstrap: 0
root@mu111:/var/lib/mysql# 

## 5. MySQL Performance Guide

http://schulung.t3isp.de/documents/pdfs/mysql/mysql-performance.pdf

## 6. Manual SST with mariabackup (galera) 

https://mariadb.com/kb/en/library/manual-sst-of-galera-cluster-node-with-mariabackup/

## 7. Geo-Distributed Galera Cluster

https://galeracluster.com/2015/07/geo-distributed-database-clusters-with-galera/
https://www.dropbox.com/s/cbxmr6pu0mwt830/Screenshot%202019-11-26%2010.53.26.png?dl=0
https://de.slideshare.net/SakariKeskitalo/using-galera-replication-to-create-geo-distributed-clusters-on-the-wan-62923322

## 8. Documentation for MaxScale 
https://maxscale.readthedocs.io/en/latest/
https://mariadb.com/kb/en/mariadb-maxscale-21-maxadmin-admin-interface/

## 9. Network Ports Galera

```
Network Ports
Galera Cluster needs access to the following ports:

Standard MariaDB Port (default: 3306) - For MySQL client connections and State Snapshot Transfers that use the mysqldump method. This can be changed by setting port.
Galera Replication Port (default: 4567) - For Galera Cluster replication traffic, multicast replication uses both UDP transport and TCP on this port. Can be changed by setting wsrep_node_address.
IST Port (default: 4568) - For Incremental State Transfers. Can be changed by setting ist.recv_addr in wsrep_provider_options.
SST Port (default: 4444) - For all State Snapshot Transfer methods other than mysqldump. Can be changed by setting wsrep_sst_receive_address.
```
https://mariadb.com/kb/en/library/configuring-mariadb-galera-cluster/
