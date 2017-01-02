## Zabbix Template for Virtuozzo

This is a template for [Zabbix](http://www.zabbix.com/), allowing to monitor
servers with [Virtuozzo](https://virtuozzo.com/products/virtuozzo/).

If you're just getting started with Zabbix, it is highly recommended that you
read the official [Zabbix official
documentation](https://www.zabbix.com/documentation/2.2/manual) first.

The Virtuozzo template supports all available Virtuozzo values provided by SNMP.

### How to use

```
* yum install -y rmond
* service snmpd start
* chkconfig snmpd --levels 2345 on
```

Unfortunately there is no possibility to monitor Virtuozzo via SNMP by default.
But there is a workaround (use it on your own risk) with gathering data with
custom OID and [Virtuozzo Command Line
Reference](http://docs.virtuozzo.com/virtuozzo_7_command_line_reference/index.html):

```
service snmpd stop
echo 'rouser pstorage_user priv' >> /etc/snmp/snmpd.conf
echo 'extend  .1.3.6.1.4.1.2021.51  license pstorage -c STORAGE_NAME view-license | grep "status"' >> /etc/snmp/snmpd.conf
echo 'createUser pstorage_user MD5 pstorage_password DES' >> /var/lib/snmp/snmpd.conf
service snmpd start 
```

where `pstorage_password` need at least 8 characters and
`pstorage_user` consists only from characters.

Import **zabbix_virtuozzo_template.xml** file into Zabbix and associate
**Template SNMP OS Virtuozzo** template to the host.

### Requirements

The template has been tested on Virtuozzo 6.0 and Zabbix 2.2.2.

### License, Authors, Copyright

This template is distributed under the terms of BSD license.

Copyright (c) Sergey Bronnikov

Author: Sergey Bronnikov [@estet](https://twitter.com/estet) (estetus@gmail.com)
