[comment]: <> (title:BGP Communities)
[comment]: <> (author:Scaleblade NOC)
[comment]: <> (description:Documentation on all of Scaleblade's peering and customer bgp communities)
[comment]: <> (readtime:5)
[comment]: <> (picture:https://i.imgur.com/vLBeBq4.png)
[comment]: <> (timestamp:2025-09-03T00:00:00.000Z)
[commend]: <> (tag:ARTICLE,HELP)

This guide outlines the BGP communities available for use by customers on our network.

# Where a route has been received
52041:[100-222]:XXX for route learned.

| Community  | Description |
|--|--|
| 52041:110:XXX | Route learnt in GB, LON by upstream ASXXX |
| 52041:111:XXX | Route learnt in US, MCI by upstream ASXXX |
| 52041:112:XXX | Route learnt in US, DAL by upstream ASXXX |
| 52041:222:XXX | Route learnt by downstream |

# Ingress communities
**The following communities can not be used in conjunction with 52041:999:0 (Enable DDoS Protection)**

52041:0:XXX do not advertise to peer.
52041:[1-3]:XXX prepend to peer [1-3] times.
52041:X:[65000-65500] do not advertise to region.

Peer based communities:
| Community  | Description |
|--|--|
| 52041:0:3257 | do not advertise to GTT |
| 52041:0:9002 | do not advertise to RETN |
| 52041:0:174 | do not advertise to Cogent |
| 52041:0:32097 | do not advertise to Wholesale Internet |

Local IX communities:
| Community  | Description |
|--|--|
| 52041:0:8714 | do not advertise to London Internet Exchange |
| 52041:0:40542 | do not advertise to Kansas City Internet Exchange |

Regional communities and prepends:

| Community  | Description |
|--|--|
| 52041:0:65000 | do not advertise to Europe |
| 52041:0:65010 | do not advertise to North America |
| 52041:0:65020 | do not advertise to Asia |
| 52041:[1-3]:65000 | prepend [1-3] to Europe peers |
| 52041:[1-3]:65010 | prepend [1-3] to North America peers |
| 52041:[1-3]:65020 | prepend [1-3] to Asia peers |

# Special communities
| Community  | Description |
|--|--|
| 52041:666:0 | Blackhole prefix on peers edge |
| 52041:999:0 | Enable DDoS mitigation for prefix (must be enabled on customer portal/with account manager). |