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
