
[comment]: <>  (title:June 3rd Outage Post-mortem)
[comment]: <>  (author:Jack Cosens)
[comment]: <>  (description:On Monday 3rd June 2024 our LON2 site was affected by a fibre cut connecting our LON1 networking pop directly.)
[comment]: <>  (readtime:10)
[comment]: <>  (picture:https://www.colo-x.com/wp-content/uploads/2020/08/IPHouse-colo-web.jpg)
[comment]: <>  (timestamp:2024-06-05T11:46:37.102Z)
[commend]: <> (tag:RFO)

On Monday 3rd June 2024 our LON2 site was affected by a fibre cut connecting our LON1 (networking pop) directly.
This blog post aims to break down exactly what happened providing our clients a clearer timeline as to what happened and our response, we also dissect what went wrong and how we are looking to do better in the future.

## Timeline of events
14:08 - Fault with fiber occurred.

14:15 - Outage was identified by internal monitoring tools and automatic alerts notified the team.

14:17 - Team acknowledged the outage and proceeded to setup internal emergency ops comms as well as identify the scope of the outage.

14:22 - It was identified to be an issue with connectivity between LON1 and LON2 via our dedicated fibre line (although the actual fault was not determined at this time).

14:23 - Scaleblade engineer was dispatched to site.

**14:24 - Outage was acknowledged publicly in our community discord server.**

**14:30 - Status page updated to show details surrounding the outage and to notify clients not in discord server.**

14:34 - Critical fault ticket was sent to euNetworks (primary fibre provider) to request any ongoing faults within the area.

14:50 - Scaleblade reached out to IP-House (LON2) to verify there was no ongoing situation on-site with power.

14:55 - IP-House confirms datacenter power feeds have not been disrupted, proceeds to assist with preliminary diagnostics with active equipment side B (check returned OKAY).

15:41 - Scaleblade engineer is on-site in LON1 (network pop) to swap optic and verify active equipment side A was functional (check returned OKAY).

16:02 - Scaleblade engineer arrives on-site in IP-House (LON2).

16:21 - Active equipment side B was confirmed working and configured correctly, optic was confirmed to be OK and working.

16:28 - euNetworks were notified of our confirmed checks and were requested to dispatch fibre engineers to identify potential faults on their end.

16:37 - IP-House begin signal integrity testing of cross connect between Scaleblade and euNetworks in IP-House (16:40 confirmed OKAY).

16:47 - Internal discussion begins around temporary solution as we are aware fibre cuts like this are notoriously difficult to debug and resolve, we have no concrete ETA on when this could be resolved, so a plan B needs to go into action.

16:51 - IP-House datacenter manager arrives on-site and re-runs XC integrity test to verify again (also confirmed OKAY).

17:43 - Temporary backup plan is in place and Scaleblade requests temporary transit port from IP-House

18:08 - IP House completes temporary cross connect and supplies Scaleblade with IPs

18:28 - Connectivity is confirmed to LON2 via temporary link, Scaleblade engineers begin configuring an offloaded tunnel between LON1 + LON2 to provide temporary connectivity.

19:00 - Connectivity between LON1 and LON2 restored via temporary tunnel.

19:11 - Brief loss of tunnel due to misconfiguration, quickly rectified and tunnel restored.

19:44 - Issue with DDoS Protected services being down over tunnel due to asymmetric traffic routing resolved.

19:51 - Connectivity restored for IPv4 services (IPv6 was still down due to network stack issue)

**20:48 - Update provided to status page to notify customers of service restoration over temporary link.**

_From 21:00 to approx 22:45 various other services were monitored and configurations changed to allow them to continue to operate under this temporary situation._

21:08 - Scaleblade requests update of progress from euNetworks.

21:54 - euNetworks escalates open case further up their internal comms chain.

22:00 - Scaleblade were told that euNetworks had placed the ticket on hold due to a miscommunication between LON1 and euNetworks during an earlier XC debugging ticket. This was clarified and they dispatched fibre engineers to site immediately.

23:42 - Scaleblade was requested to shut down active equipment ports on both ends to assist with debugging.

01:28 - euNetworks notifies Scaleblade that issue has been resolved.

_From 1:30am to 4:00am we monitor and run tests over the fibre to ensure we are happy with the euNetworks resolution._

**04:22 - Status page updated to notify clients that fibre had been restored and that services would slowly be moved back over to the fibre.**

**06:09 - Status page updated to notify clients that all services had been moved back over the fibre and no further disruption was expected.**

## Why did this happen?
Ultimately this outage was on us. LON2 is a new site that has only been operating a few months, we released this site earlier than anticipated to allow us to fulfil a backlog of orders we had. This resulted in the deployment being reliant on a single connection between LON1 and LON2.
This single point of failure had always been known to us, in-fact we're still in negotiations now with different providers regarding our backup/redundant link, we were just unlucky that we ran into the eventuality a lot sooner than we could of anticipated.

## What are we changing?
We learnt a lot from this outage, both in our underlying infrastructure but also how we prioritise outages as a team. This outage in particular was difficult due to some of our team members being on vacation during the outage.

 - Discussions regarding our backup connection will be expedited. We expect to have a viable (redundant) connectivity option connecting LON1 and LON2 within the next 14 days. This backup connection will be capable and configured to take on ALL traffic and services within LON2 at any given time with no further route changes or configuration to take place. This was **expected** of us, and I can only apologise and thank you for your patience while we get this in place.
 - Fault monitoring and notification delay. In the timeline you can see a 7 minute delay between when the fault happened and when it was identified/notified to the team. Although 7 minutes wouldn't have made much of a difference in this outage, it could in future. We aim to reduce this by deploying a suite of new monitoring and alerting software that is redundant across all of our LON and DFW sites.
 - Lines of communication and api availability. Due to our services being hosted in LON2 during this outage our panel and customer api were also unavailable. This caused customers who were not aware of our status page or discord community confusion and panic as they were not able to receive updates. We plan to make upgrades to our internal infrastructure to allow our customer portal to be resilient to a full-site outage.
 - Communication between our partners and providers has room for improvement. We found a significant delay in there being an actionable request from when we opened the issue with euNetworks to the issue being resolved, we are going to do internal retrospectives on this to ensure that we are able to provide more clarity - quicker in these situations.

## Big thanks and kudos
**IP-House** was a huge help during this time. We had completely lost connectivity to the site and they were able to provide consistent and well written updates around our own equipment while our engineer was getting to the site for further investigation.
The team there were able to provision us an emergency 10GbE connection in under half an hour. This allowed us to get our clients back online significantly quicker than we otherwise would have.

**Customers** a big thank you to our loyal customers that were affected by the outage. We appreciate your patience with us and we hope that this blog post gives you the faith to continue working with us as we grow and improve our services.

## SLA and Compensation
Over the next few days we will automatically issue SLA in the form of account credit of your next monthly invoices with us. This will be in-line with our SLA policy.
If you have any questions regarding this outage or compensation related to it please reach out to us via a support ticket at https://my.scaleblade.com
