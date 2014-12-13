## Zabbix Template for Parallels Cloud Server

This is a template for [Zabbix](http://www.zabbix.com/),
allowing to monitor servers with [Parallels Cloud Server](http://www.parallels.com/products/pcs/).

If you're just getting started with Zabbix, it is highly recommended that you
read the official [Zabbix official documentation](https://www.zabbix.com/documentation/2.2/manual) first.

### Features
The Parallels Cloud Server template supports all available PCS values provided by SNMP.

### How to setup SNMP in Parallels Cloud Server

* yum install -y rmond
* service snmpd start
* chkconfig snmpd --levels 2345 on

Unfortunately there is no possibility to monitor Parallels Cloud Storage
via SNMP by default. But there is workaround (use it on your own risk)
with gathering data with custom OID and
[Parallels Cloud Storage command line tools](http://sp.parallels.com/products/pcs/documentation/):

```
service snmpd stop
echo 'rouser pstorage_user priv' >> /etc/snmp/snmpd.conf
echo 'extend  .1.3.6.1.4.1.2021.51  license pstorage -c STORAGE_NAME view-license | grep "status"' >> /etc/snmp/snmpd.conf
echo 'createUser pstorage_user MD5 pstorage_password DES' >> /var/lib/snmp/snmpd.conf
service snmpd start 
```

where `pstorage_password` need at least 8 characters and
`pstorage_user` consists only from characters.

### Installation

1. Import **Zabbix_Parallels_Cloud_Server_Template.xml** file into Zabbix.
2. Associate **Template SNMP OS Parallels Cloud Server** template to the host.

### Contributing to the Parallels Cloud Server Zabbix template

To work on the `Zabbix-PCS-Template` plugin development, clone this repository:

```
$ git clone https://github.com/ligurio/Zabbix-PCS-Template
$ cd Zabbix-PCS-Template
```

### Sending a Pull Request
If you're ready to send your changes, please follow the next steps:

1. Fork the 'Zabbix-PCS-Template' repository and ad it as a new remote (`git add
remote my-fork <fork_url>`)
2. Create a branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am "Added a sweet feature"`)
4. Push the branch to your fork (`git push fork my-new-feature`)
5. Create a pull request from your `my-new-feature` branch into `master` of
`Zabbix-PCS-Template` repo

### Getting Help
Having problems while using the template? Ask your question to Zabbix forum:
[Zabbix support forum](https://www.zabbix.com/forum/)

If you get an error while using the Parallels provider or discover a bug,
please report it on the [IssueTracker](https://github.com/ligurio/Zabbix-PCS-Template).

### Requirements

The template has been tested on Parallels Cloud Server 6.0 and Zabbix 2.2.2.


### License, Authors, Copyright

This template is distributed under the terms of BSD license.

Copyright (c) Sergey Bronnikov

Author: Sergey Bronnikov [@estet](https://twitter.com/estet) (estetus@gmail.com)

