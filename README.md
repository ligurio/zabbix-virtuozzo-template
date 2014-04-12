Author: Sergey Bronnikov (estetus@gmail.com)

The template has been tested on Parallels Cloud Server 6.0

### How to setup SNMP in Parallels Cloud

* yum install -y rmond
* service snmpd start
* chkconfig snmpd --levels 2345 on
