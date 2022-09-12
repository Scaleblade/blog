
[comment]: <>  (title:Community Update #1)
[comment]: <>  (author:Jack Cosens)
[comment]: <>  (description:The beginning of our monthly community updates for CosmicV)
[comment]: <>  (readtime:3)
[comment]: <>  (picture:https://cdn.discordapp.com/attachments/1016684864868724806/1016684941276364911/FiveM_b2545_GTAProcess_2022-09-06_21-48-58.png)
[comment]: <>  (timestamp:2022-09-12T23:20:23.453Z)
[comment]: <>  (tag:Community Update)
[commend]: <> (tag:CosmicV)

# Creating a new multiplayer battlefield to support 700,000 users.
The team are hard at work beginning v3 of our King of the Hill framework. We are taking a few things into consideration when writing this framework and learning from the mistakes of the one we currently have in use. This short community post should detail what our goals and objectives are for these and hopefully over the next few months you will be able to follow along with us as we progress further with these goals.

## What do we aim to solve starting from scratch?
Quite frankly, the current one is awful. KoTH v2 (internally tagged) was developed through the tail-end of 2020 into the early months of 2021 where it was finally released April that year. This framework was an upgrade from our v1 and allowed us to support 300 player-slots (up from 120), we also decided to add support for "lobby based" gamemodes which players from early 2021 will of remembered from our server selector experiment where people we able to choose what map they played on connect.
Ultimately this feature was abandoned and removed as the adoption rate was far below what we expected.
Through early 2022 leading all the way up to August 2022 our player base grew exponentially. 
As of writing this post we have over 700,000 unique users and we average 290 players in our peak times, with times where we are exceeding this by 100 additional players (our current record is set at 392 players) far above the average 190 we were expecting/receiving in early 2021.

## What issues are we having?
- Shop sorting is handled server-side, during peak times we observe issues where this system can be overloaded especially on game start/end
- Having 300+ players all running towards one singular point on the map is causing issues with *clients* rendering that many players
- The codebase is becoming more complex and difficult to maintain due to the abandoned lobby-mode support

## Spoilers
Alright, we get it. Its been a lot of chat and nothing to show for it. Good news is this rewrite will be jam packed of updates.
 - New shop backend, faster purchases, faster loading, featured vehicles
 - Attachments! Our entire prestige system will be reworked to add a more progressive/fair attachments system.
 - Performance upgrades. We are putting a lot of effort into upgrading our physical infrastructure alongside our codebase. We are looking into additional methods that can be implemented during peak-hours to better deal with performance on the client when rendering the mp_playermodels.
 
![Screenshot of new plane strike killstreak reward](https://cdn.discordapp.com/attachments/794359734852648970/982726232464584714/unknown.png)

Check back here next month for another update on where we are at, and what new features are ready.
We will also be announcing a new BETA team in the next few weeks which will detail how some of you guys can get involved with the research and development of our work!