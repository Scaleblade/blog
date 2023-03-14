[comment]: <>  (title:Creating an effective disaster recovery plan for your SaaS business.)
[comment]: <>  (author:Jack Cosens)
[comment]: <>  (description:Having an effective disaster recovery plan could make or break a company, especially in the cyber or hosting sphere. This blog post aims to cover some of the basics of building a secure and reliable disaster recovery plan for your business, protecting yourself and your customers.)
[comment]: <>  (readtime:6)
[comment]: <>  (picture:https://images.unsplash.com/photo-1485617359743-4dc5d2e53c89)
[comment]: <>  (timestamp:2023-03-14T16:24:40.412Z)
[commend]: <>  (tag:Cloud)

It’s something we all forget about until it's too late.

Having an effective disaster recovery plan could make or break a company, especially in the cyber or hosting sphere. This blog post aims to cover some of the basics of building a secure and reliable disaster recovery plan for your business, protecting yourself and your customers.

## What is classed as a disaster?

Well, anything that could result in long term disruption to your business and/or clients really! Think of what might happen if your datacenter flooded and ruined your core router, how long is it going to take to replace that? Will there be any lost data? What can you do for your customers in the meantime?

It’s not just *flash flooding, global warming and a failing economy* that could affect your services, think smaller and much simpler. What happens if a core service suffers from drive failure? How do you simultaneously recover your service while ensuring that all of your data is good to go?

We developed a 3 phase approach to live-production recovery which is applicable to almost any online business!

## Step 1 - DATA

It’s the liquid gold of the 21st century. It's valuable to have, difficult to use and depending on where you operate very, very expensive to irresponsibly lose. Keep in mind that it’s not just the impact of your data being lost to your company - you can also receive large fines based on GDPR and Data Protection laws in your region.

Naturally this will be the most important part of your disaster recovery plan, but it doesn’t have to be expensive!

*Follow 3-2-1 rule! 3 copies, 2 formats, 1 off-site.*

**3** - We suggest making backups a minimum of daily for essential services, and even hourly for more business critical infrastructure. When creating these backups make sure to generate them at the source (your database server, etc). 3 copies of a corrupt database file ain’t useful to anyone!

  

**2** - Having your backups in 2 different formats is always a good idea! Where possible we will keep a copy of the database saved locally on the same machine for quick reference and easy restoring as well as cloning a copy to our SATA SSD NAS in each site.

For smaller (more budget constraint operations) this could easily be achieved by your favorite hosting provider's “block storage” (or similar) product.

  

If your provider offers a “snapshot” service then this would also be applicable here.

  

*JUST BE CAREFUL!* Some providers may consolidate their block storage on the same physical device as your main server (especially if you’re running an array of VM’s). Check with your provider to make sure that your storage is separated from your existing storage or use a new provider in the same region if you're super cautious!

**1** - Keep a copy off-site or with a trusted cloud service provider. In the situation where your datacenter is overrun by facebook branded lizards or a tornado blows the entire building away, it's crucial that you have an off-site backup that you can restore to! Some cloud providers will automatically replicate storage across multiple sites anyway giving you that extra data security.

If a cloud backup solution is a little out of budget, [then getting another block storage vps or server with a different provider](https://scaleblade.com/products/metal) (in a different location, even country if possible) is also good!

  

## Step 2 - COMMUNICATION

Keeping your customers informed is more difficult than it sounds. Never speculate or guess. As much as it may suck when it happens to you a simple “We’re currently investigating the issue” will do. Here is a simple list of do’s and don’ts:

  

**DO:**

-   Acknowledge the issue, let your customers know you’re working on resolving it.
    
-   Notify your team/employees about the disruption and establish a central communication channel where your support team can get the latest information to relay to your customers.
    
-   (if you’re aware of the cause) Inform your team that you have identified the issue and no further information on their behalf is needed.
    
-   (if you’re unaware of the cause) Inform your team that you are looking for x,y,z information to help identify the cause of concern.
    
-   In the event of a data breach, seek immediate legal advice on the correct way to proceed to best protect your customers and your company.
    

  

Having open, clear communication within your team is crucial.

  

**DONT:**

-   Use words like “think”, “might” or “may”. If you’re not 100% certain on the issue, don’t disclose what it could be. This will just cause confusion and panic.
    
-   Not acknowledge the issue. If something is inaccessible a simple “We are aware, and are working on a resolution” can go a long way.
    

  

## Step 3 - TEMPORARY INFRASTRUCTURE

In the worst case scenario your primary infrastructure is going to be out of action for a sustained period of time, or forever (or is on fire); then it's always good to have alternative options on hand.

  

There are plenty of [affordable on-demand options on the market](https://scaleblade.com), most providers will have a form of “instant deployment” or “on-demand” service. This may be more expensive than your typical infrastructure but if you’re just using it for a few days (or even hours) it could be a critical first step when keeping you and your business online.

  

When choosing “backup infrastructure” we suggest going with a separate company than your primary service provider - what we regularly find is that during an outage of one service, customer service and support channels may be flooded or effectively reduced for the time period. Not helpful if you need assistance with your backup service!

  

Remember to notify your clients/customers of this change, they may need to expect slower application speeds or data rates if your temporary service isn’t as advanced as your primary.

  

## CONCLUSION

Having an agile, regularly updated and well thought out disaster recovery plan does not have to be expensive or complex. We hope that breaking it down into 3 simple steps can help a lot of smaller service providers think about the hypotheticals - the last thing anyone wants is to wake up and not have their business anymore.

  

If you’re struggling or have any questions in regards to your own disaster recovery plan(s) then feel free to reach out and we can assist with advice and point you in the right direction of best practices in the industry for your setup.