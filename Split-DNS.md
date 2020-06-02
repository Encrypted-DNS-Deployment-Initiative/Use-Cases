## Split-DNS DoH Use case
***



## SPLIT DNS

Defined as having an apex (or root) different to the public ICANN root.
Selection of a resolver implies selection of an apex.
Encryption of DNS makes this selection stronger.

### Multihoming (both per interface and per application) affects many of these below.

Fallback, when selected resolver is no longer available
Can imply a change of apex and change of behaviour
Or loss of DNS service if no fallback allowed

### Home
See [Consumer Home](./Consumer%20home)
Resolution of the CPE itself, by devices in the home trying to find it. Not possible if DNS is tunnelled to external world.

### Enterprise
Need for querying both internal and external domains
Only some resolvers are configured to know about which namespaces are handled where.
Generally these are the enterprises’ internal resolvers.
Use and misuse of adhoc TLDs in enterprises .local, .corp, .intra
Selection of appropriate resolver for queries under these TLDs is critical
These can leak to the root DNS

### Datacenters
DCs using DNS as a database for application data.
Clients can be microservices or general enterprise clients/desktops.

### Captive portals
- needs to be considered and explored

### VPNs
Which policies would be the user be bound to?


### Use of bonjour services
Printer comes into a network in a department and announces itself

## Questions and issues to consider

### Will split DNS decline in popularity?
As a reaction to issues with split DNS being only partly available?
Would enterprises publish into public DNS?
Is there a solution for dynamic locally-available devices that doesn’t rely on split DNS?

### Canary domains
Use of canary domain to disable encrypted DNS
Use of canary domain to change selected resolver

### Nominated resolvers
Reachability
Different apex per user
Security implications. Adds new ability to observe queries to your domain.


***
## Development History 
Use case discussion on Split-DNS situations.  Originally developed during EDDI virtual session on 5/13/2020
