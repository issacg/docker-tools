## Non-swarm services

The service definitions here represent the few cases where limitations
of Docker's swarm implementation made it difficult or impossible to
run them via 'docker stack deploy'. Examples:

* Etcd instances require IP address settings on command line and thus
far Docker doesn't provide a way to assign static IPs (or separate DNS
host names) via compose in swarm mode.

* mt-daapd (iTunes server) needs to run on host network for mDNS (avahi) service
discovery.

* samba's nmbd daemon needs to run on host network.

* weewx (weather station) needs a 'devices' directive.

Each service defined here is invoked via docker-compose from one of
the docker hosts.  Failover requires manual intervention.

