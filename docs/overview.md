---
hide:
  - navigation
---

# Overview of Bots for Cardano groups

Currently, there are 3 bots for Cardano ecosystem. Below is a high level overview for each of them:

  1. @CardanoOfficialNews_bot - This is a news propogation bot , that can used to bridge the announcements from different IOG/Emurgo/CF channels on to target groups. Changing options for any of the administrative commands is currently only available to CM leads (and maintainer of the bot).  
  2. @Modlogcollector - This bot (telegram account type: user) is to assist ambassadors with tasks to help out moderation activities across different groups, as well as provide Proof of Work for their moderation activities. Access can be gained to work with this bot by joining Moderation Logs Channel.  
  3. @Charlie_Cardano_bot (alias: @Chanti_Cardano_bot) - These bots are designed to self-moderate chats using auto-delete keywords, responses for triggers (eg: #trading will respond with pre-defined response). Access can be gained to work with this bot by joining Moderation Logs Channel.  

## Can modlog and charlie bots be merged into 1?

The reason @modlogcollector and @charlie_cardano_bot are seperate is because telegram platform limits certain capabilities to be only available to user accounts (@modlogcollector) , eg: Checking history of group - while some other tasks are only available to bot-type accounts (eg: checking message queues, using action against handles).

## What are moderation activities done by these bots?

The bots perform quite a few tasks summarised (not limited to) below:

  1. Provide auto responses to triggers to provide pre-baked responses (a moderator can hit /list in DM with Charlie to check a list of triggers). Advanced users of the bot have access to help create more trigger/responses.
  2. Provide price updates in trade groups.
  3. Auto-Delete messages for well known scam/spam patterns
  4. Auto-Ban users based on patterns (eg: sharing a private group invite or shilling a fake giveaway, or accounts with 10 char + 5 number username pattern)
  5. Provide verification mechanism - Groups who want to opt in can enable verification system where a new user needs to complete a one-time verification in DM with bot using their forum account (where an OTP is sent) before they can start talking.
  6. Maintain an offline warn system - Telegram natively does not have a warn system, but bots can help maintain warn counts across groups for each users.
  7. Provide Proof of Work for every moderator to be able to insert proof of his work for given month as image.
  8. Allow moderators to ban/unban users within group or across all groups.
  9. Propogate news across ecosystem.
  10. Get an audience member (unique vs total) count across the groups.

## Onboarding

### For ambassadors

To be eligible to work with the bots, all an ambassador needs to do is join the [Moderation logs channel](https://t.me/joinchat/R8-HXiGqAV37gO_P).

### Test access

Once joined, to test their access - they can hit `/proof` in the group, and ensure that they receive a screenshot in DM by @Modlogcollector with a summary view of their activity for current month - starting from 1st of the month.

### Basic moderation tasks

The commands below are common interactions moderators may use bots for within groups.

- **Inline actions within groups**

    Users can use administrative commands below in *reply to user's messages* in groups - to take corresponding action against that user:

    | Command             | Description                                                                    | Scope      |
    |---------------------|--------------------------------------------------------------------------------|------------|
    |`/ban reason`        | Ban user in the group                                                          | Group only |
    |`/warn reason`       | Warn user for violation of a rule (3 violations result in mute)                | All groups |
    |`/unwarn reason`     | Unban and unmute users across groups                                           | All groups |
    |`/mute 1d reason`    | Mute user for specified days (eg: `1d`), hours (eg: `1h`) or weeks (eg: `1w`)  | Group only |
    |`/btl reason`        | Kick (not ban) user from the group, they can join back again                   | Group only |
    |`/uv unverified`     | Kick unverified user across all groups                                         | All groups |

- **Actions in moderation logs group or DM with @modlogcollector bot**

    Below is a list of commands that moderators can use in DM with @modlogcollector. Same commands will also work in moderation logs channel.

    | Command               | Description                                                                    | Scope      |
    |-----------------------|--------------------------------------------------------------------------------|------------|
    |`/b #137295212 reason` | Ban user whose UUID is 137295212 across all Cardano groups                     | All groups |
    |`/u #137295212 reason` | UnBan user whose UUID is 137295212 across all Cardano groups                   | All groups |
    |`/mediaban #137295212 reason`| Restrict user whose UUID is 137295212 from sending media on Cardano groups| All groups |
    |`/backtolobby #137295212 reason`| Send user 137295212 back to lobby (kick from private groups like tech support)| Private groups |
    |`/proof 8`| Provide proof of work for top 6 groups moderator contributed to (8 is month of report)      | All groups |

