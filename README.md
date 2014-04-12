## Zabbix Template for Parallels Cloud Server

This is a template for [Zabbix](http://www.zabbix.com/),
allowing to monitor servers with [Parallels Cloud Server](http://www.parallels.com/products/pcs/).

If you're just getting started with Zabbix, it is highly recommended that you
read the official [Zabbix official documentation](https://www.zabbix.com/documentation/2.2/manual) first.

### Features
The Parallels Cloud Server template supports all available PCS values provided by SNMP.

* rmondVeId STRING
* rmondVeName STRING
* rmondVeState INTEGER
* rmondVePerfectNode STRING
* rmondVeMemoryTotal Counter64
* rmondVeMemoryUsage Counter64
* rmondVeSwapTotal Counter64
* rmondVeCpuNumber INTEGER
* rmondVeCpuLimit INTEGER
* rmondVeCpuUnits INTEGER
* rmondVeCpuSystem INTEGER
* rmondVeCpuUser INTEGER
* rmondVeType INTEGER
* rmondVeUuid STRING
* rmondVeDiskName STRING
* rmondVeDiskTotal Counter64
* rmondVeDiskUsage Counter64
* rmondVeDiskReadRequests Counter64
* rmondVeDiskWriteRequests Counter64
* rmondVeDiskReadBytes Counter64
* rmondVeDiskWriteBytes Counter64
* rmondVeDiskHash1 Counter32
* rmondVeDiskHash2 Counter32
* rmondVeNetworkInterface STRING
* rmondVeNetworkInBytes Counter64
* rmondVeNetworkOutBytes Counter64
* rmondVeNetworkInPackets Counter64
* rmondVeNetworkOutPackets Counter64
* rmondVeNetworkMacAddress STRING
* rmondLocalVeNumber INTEGER
* rmondVeLimit INTEGER
* rmondLicenseVeNumber INTEGER
* rmondLicenseCtNumber INTEGER
* rmondLicenseVmNumber INTEGER
* rmondLicenseVmNumber

### How to setup SNMP in Parallels Cloud Server

* yum install -y rmond
* service snmpd start
* chkconfig snmpd --levels 2345 on

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

The template has been tested on Parallels Cloud Server 6.0 and Zabbix 2.0.0.


### License, Authors, Copyright

This template is distributed under the terms BSD license.

Copyright (c) Sergey Bronnikov

Author: Sergey Bronnikov [@estet](https://twitter.com/estet) (estetus@gmail.com)

