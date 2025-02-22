
[comment]: <>  (title:Getting ready for your ASN application)
[comment]: <>  (author:Jack Cosens)
[comment]: <>  (description:A basic guide showing you the basics of the RIPE and how to create the required objects.)
[comment]: <>  (readtime:8)
[comment]: <>  (picture:https://i.ytimg.com/vi/0RI5W3hqBug/hq720.jpg)
[comment]: <>  (timestamp:2025-02-22T10:12:02.102Z)
[commend]: <> (tag:RIPE,HELP)

This guide aims to show you the basics of what you will need to supply your sponsoring LIR when starting an application for an ASN (autonomous system number) within the RIPE database.

For individuals that like to use youtube videos to learn this is a great video outlining the basics of RIPE object creation and maintenance: https://www.youtube.com/watch?v=NiqjVXhT21M&t

Prior to getting started you will need to make a RIPE account on https://ripe.net, confirm your email and set up 2-factor authentication.

# Getting started: What do I need?

For the purpose of the application you will need:

- Organisation object
- Role and maintainer pair

## Creating Role and Maintainer

The maintainer role is the most important thing within the RIPE database. A maintainer role dictates baseline permissions for other objects as well as delegated resources.
Without it you will not be able to modify or update existing objects belonging to your org.

*Within the RIPE portal navigate to the "RIPE DATABASE" > "CREATE AN OBJECT"*

![Navigating to create an object](https://i.imgur.com/0ij9Jza.png)

*Once you are in the object creator, select organisation and role pair from the dropdown*

![Select role and maintainer pair](https://i.imgur.com/GZgasIP.png)

*Fill out the details for the object, these details should be accurate and kept up to date when possible.*
*You can click on the [?] icons to get prompts about syntax and requirements for each section*

![Creating object pair](https://i.imgur.com/ltDrL1K.png)

*Success! We have created our admin-c/tech-c role as well as our maintainer role.*
*In this case our maintainer is [SBL-TUTORIAL-MNT] and our role/tech-c/admin-c is [ST14501-RIPE] we should save these for our application later!*

![created objects](https://i.imgur.com/5Ba2tG4.png)

## Creating an abuse mailbox
It is a requirement that all resources and orgs have valid email address for abuse notifications. Lets go ahead and add an abuse-mailbox entry onto our ST14501-RIPE object.

*Navigate to the RIPE DB search bar and look up the object we just made [ST14501-RIPE] when the entry pops up select the UPDATE option*

![update mailbox abuse](https://i.imgur.com/re6yMFP.png)

*Once on the edit page, click the [+] button next to the database entries, select abuse-mailbox and input the email you wish to receive abuse to. Once completed click save and we're ready!*

![adding abuse email ](https://i.imgur.com/p9QJAY7.png)

## Creating an organisation

Organisations are the company or the individual's information that holds a particular resource.
Provider Independent resources (ASN's and some IP subnets) is tied to the ORG and must be transferred to a different one.
Provider Allocated resources (IPv6 Subnets offered by Scaleblade) can be allocated to an ORG and swapped without the need for a ripe transfer request.

*To create our organisation object, lets go back to the create an object section of the RIPE database like before, this time we will select Organisation role*

![create org](https://i.imgur.com/oPJW6vQ.png)

*Fill out the information listed as follows:*

- organisation: AUTO-1
- org-name: YOUR FULL LEGAL NAME OR ENTITY NAME AS SHOWN IN DOCUMENTS
- address: ADDRESS MATCHING YOUR LEGAL ID OR ENTITY
- country: COUNTRY OF ORIGIN (OR INCORPORATION)
- e-mail: MAIN EMAIL USED FOR CONTACT
- abuse-c: [THE RIPE ROLE WE MADE EARLIER]
- mnt-ref: [MAINTAINER ROLE OF THE PREFIX HOLDER, FOR SCALEBLADE CUSTOMERS THIS IS SBL-MNT]

*After you save this you will be given another object with the "-ORG" tag added onto the end, this is randomised based on your preference set in the organisation field.*

![Creating org object](https://i.imgur.com/qaqqCU5.png)

Thats it! You're done.

You now have a maintainer, role, organisation and  some basic knowledge on how to use the RIPE database.

For any specific questions regarding getting setup in the RIPE database reach out to our support via the https://my.scaleblade.com portal for assistance.