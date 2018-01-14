## Elasticsearch Service for Ambari

The Elasticsearch Service for Ambari stack custom service. which allows you to install and manage Elasticsearch via Ambari.  This service is not supported by Hortonworks. 

## Compatibility

This service has been tested with the following:

- CentOS 7.x
- Ambari 2.5,2.6
- HDP/HDF 2.x/3.x
- ElasticSearch 6.x


## Installation

To install this service, you need access to the Ambari Server with sudo permissions.

```
VERSION=`hdp-select status hadoop-client | sed 's/hadoop-client - \([0-9]\.[0-9]\).*/\1/'`
sudo git clone https://github.com/kchandan/elasticsearch-ambari.git /var/lib/ambari-server/resources/stacks/HDP/$VERSION/services/ELASTICSEARCH
```

If you do not have the ability to use git, you can download the repo archive and extract it to directory shown above.

After you have installed the service, you need to restart the Ambari Server.

```
sudo service ambari-server restart
```

Once the Ambari Server has been restarted, you should see Elasticsearch as an available service to install from the Add Service screen.

## Required property
```
zen_discovery_ping_unicast_hosts - FQDN of master and data nodes. seperated by comma eg. master.internal,data1.internal,data2.internal
```

## Local Dev Setup

vagrant up

You can access Ambari on http://localhost:8080

User/Pass: admin/admin

## Issues

If you find any issues please report issue.

## License
This project is based on Elasticsearch Ambari Service of <https://github.com/apache/incubator-metron/tree/master/metron-deployment/packaging/ambari/metron-mpack/src/main/resources/common-services/ELASTICSEARCH>
