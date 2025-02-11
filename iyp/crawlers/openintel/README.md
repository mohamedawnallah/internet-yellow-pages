# OpenINTEL -- https://www.openintel.nl/

The OpenINTEL measurement platform captures daily snapshots of the state of large parts of the
global Domain Name System (DNS) by running a number of forward and reverse DNS measurements.

While OpenINTEL runs measurements to a variety of domain names, IYP currently only fetches data for
the [Tranco top 1 million list](https://data.openintel.nl/data/tranco1m/) and the CISCO Umbrella 
top 1 million list since it combines rankings.
IYP also get the list of authoritative names servers seen by OpenINTEL.

IYP uses only `A` queries to add IP resolution for DomainName and AuthoritativeNameServer nodes.

A crawler of mail servers is also implemented but not used as it creates a very large number
of links and this dataset is currently not requested/needed by anyone.

## Graph representation

IP resolution for  popular domain names:
```Cypher
(:DomainName {name: 'google.com'})-[:RESOLVES_TO]->(:IP {ip: '142.250.179.142'})
```

IP resolution of authoritative name servers:
```Cypher
(:AuthoritativeNameServer {name: 'ns1.google.com'})-[:RESOLVES_TO]->(:IP {ip: '216.239.32.10'})
```
## Dependence

This crawler is not depending on other crawlers.
