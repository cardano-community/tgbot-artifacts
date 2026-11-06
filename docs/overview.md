---
hide:
  - navigation
---

# Overview of Bots for Cardano groups

Currently, there are 3 bots for Cardano ecosystem. Below is a high level overview for each of them:

  1. @CardanoOfficialNews_bot - This is a news propagation bot that posts a short link preview for new announcements from different IOG/Emurgo/CF channels into target groups. Changing options for any of the administrative commands is currently only available to CM leads (and maintainer of the bot).
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
  9. Propagate news across ecosystem.
  10. Get an audience member (unique vs total) count across the groups.

## Onboarding

### For ambassadors

To be eligible to work with the bots, all an ambassador needs to do is join the [Moderation logs channel](https://t.me/joinchat/R8-HXiGqAV37gO_P). Access follows channel membership: leaving the channel removes the moderator from @Modlogcollector's admin list.

### Test access

Once joined, to test their access - they can send `/proof` in a DM to @Modlogcollector, and ensure that they receive a screenshot with a summary view of their activity for current month - starting from 1st of the month.

## Command reference

All the commands below are issued by moderators. Unless stated otherwise, the commands are restricted to the moderators of the group/channel they are used in.

The accepted command prefixes depend on the bot:

  - @Charlie_Cardano_bot and @Chanti_Cardano_bot accept `/`, `!` and `#` - eg: `/ban`, `!ban` and `#ban` are the same command.
  - @modlogcollector accepts `/` and `!` in a direct message - eg: `/proof` and `!proof` are the same command. It no longer processes commands in the moderation logs channel.
  - @CardanoOfficialNews_bot only accepts `/`.

Users can be referred to by their Telegram UUID (eg: `#137295212` or `#u_137295212`) or by their handle (eg: `@rdlrt`). A numeric UUID works even if the bot has not seen the user; an `@handle` only resolves for users the bot already knows, so the UUID form is the reliable one.

Groups also answer to the trigger keywords (eg: `#trading`, `/rules`, `#price`) - the full list is published in [triggers.json](../JSONs/triggers.json) and can be downloaded with `/list` in a DM with @Charlie_Cardano_bot.

### Inline actions within groups (@Charlie_Cardano_bot / @Chanti_Cardano_bot)

Users can use administrative commands below in *reply to user's messages* in groups - to take corresponding action against that user:

| Command             | Description                                                                    | Scope      |
|---------------------|--------------------------------------------------------------------------------|------------|
|`/ban reason`        | Ban user in the group                                                          | Group only |
|`/warn reason`       | Warn user for violation of a rule (2nd warning mutes for 1 hour, 3rd warning mutes indefinitely) | Warn count: all groups |
|`/unwarn reason`     | Remove a warning and unmute the user                                          | Warn count: all groups |
|`/mute 1d reason`    | Mute user for the given period - only `h` (hours, eg: `1h`) and `d` (days, eg: `1d`) are parsed. Any other value is treated as an indefinite mute | Group only |
|`/btl reason`        | Kick (not ban) user from the group, they can join back again                   | Group only |
|`/uv reason`          | Kick unverified user across all verify-enabled groups                          | Verify-enabled groups |
|`/report`            | Forward the replied message to the moderation logs channel and notify the admins | Group only |
|`/rm`                | Delete the replied message and the command                                    | Group only |
|`/q`                 | Show the forum account and verification status of the replied user (`/q #u_137295212` in the moderation logs channel) | Group only |
|`/news`              | Post the latest Cardano headlines in the group                                | Group only |
|`/price`              | Post the current ADA price in a trade group                                   | Group only |
|`/remindmein 1h text`| Set a reminder for the group (admins only) - the period is given as `30s`, `2h`, `1d`, `1w`, `1m` or `1y` (`m` is months, not minutes). The reminder is posted in the same forum topic. Enabled on @Charlie_Cardano_bot only | Group only |

Administrative actions are refused when the target is an administrator or the bot account itself.

### Actions in DM with @modlogcollector bot (DM only)

Below is a list of commands that moderators can use in DM with @modlogcollector. The bot no longer processes commands in the moderation logs channel; any other command sent to it is redirected to @Charlie_Cardano_bot. It also no longer scans group messages for auto-deletion - that is handled by @Charlie_Cardano_bot. The moderation logs channel itself is excluded from the recent-action scan and is not added by `/upd`, so activity there is not mirrored back into it.

| Command               | Description                                                                    | Scope      |
|-----------------------|--------------------------------------------------------------------------------|------------|
|`/ping`                | Check that the moderator is alive and report how many groups/admins it watches | All groups |
|`/upd`                 | Rebuild the group list (including groups without a public handle) and the moderator list the bot watches; stale groups and moderators who left the log channel are removed | All groups |
|`/uvall #group`        | Mute unverified users in `#group` (defaults to `#catalystproposers`), skipping administrators and bots | Selected group |
|`/proof 8`             | Provide proof of work for top 6 groups moderator contributed to (8 is month of report)      | All groups |
|`/proof @rdlrt 8`      | Provide the proof of work of another moderator (CF moderators only)            | All groups |
|`!audience_numbers`    | Report the member count of every group watched by the bot (CF members only)    | All groups |

Notes:

  - `/proof` accepts an optional month and an optional year - eg: `/proof 8 2021`. Without them the current month is used.
  - `/uvall` mutes the unverified users, it does not ban them.
  - The moderator list is rebuilt from the current members of the moderation logs channel at startup, on membership changes and on `/upd`; leaving the channel removes access.

### Cross-group actions in DM with @Charlie_Cardano_bot (or in the moderation logs channel)

These commands are handled by @Charlie_Cardano_bot. Each action is queued and applied in the background across all moderated groups, and the result is posted in the moderation logs channel.

They are enabled on @Charlie_Cardano_bot (`modcommands`); @Chanti_Cardano_bot keeps them disabled.

| Command               | Description                                                                    | Scope      |
|-----------------------|--------------------------------------------------------------------------------|------------|
|`/b #137295212 reason` | Ban user whose UUID is 137295212 across all Cardano groups                     | All groups |
|`/u #137295212 reason` | UnBan user whose UUID is 137295212 across all Cardano groups                   | All groups |
|`/mediaban #137295212 reason`| Restrict user whose UUID is 137295212 from sending media on Cardano groups| All groups |
|`/backtolobby #137295212 reason`| Send user 137295212 back to lobby (kick from private groups like tech support)| Private groups |

Notes:

  - `/b` and `/u` also accept the aliases `/banu` and `/unban`/`/unmute`.
  - The target can be given as a numeric UUID (`#137295212` or `#u_137295212`) or as an `@handle` for a user the bot already knows.
  - Moderator access for these commands follows the @Modlogcollector admin list, which follows membership of the moderation logs channel; @Charlie_Cardano_bot also keeps its own configured admins as a fallback.

### Verification commands in DM with @Charlie_Cardano_bot bot

| Command               | Description                                                                    |
|-----------------------|--------------------------------------------------------------------------------|
|`/verify`              | Start the verification process (also available as `/start`)                    |
|`/forum <forum-id>`    | Submit your Cardano forum account - an OTP is sent to it                       |
|`/otp <code>`          | Submit the OTP received on the forum to complete the verification              |

### Administration commands in DM with @Charlie_Cardano_bot bot

| Command               | Description                                                                    |
|-----------------------|--------------------------------------------------------------------------------|
|`/help`                | List the administration commands of the bot                                     |
|`/list`                | Download the full list of triggers and their descriptions                      |
|`/taglist`             | List the groups the bot is part of, with their relay status and language       |
|`/on #group`           | Turn the broadcast reception on for a group                                    |
|`/off #group`          | Turn the broadcast reception off for a group                                   |
|`/rm #group`           | Remove a group from the broadcast recipient list                               |
|`/readmin`             | Refresh the moderator list and re-promote the moderators in the groups          |
|`/counts`              | Report the member count of every group and channel                             |
|`/delwordadd word`     | Add a word (case insensitive) to the auto-delete list                           |
|`/delwordrm word`      | Remove a word from the auto-delete list                                         |
|`/delwordlist`         | List the words used for auto-deleting messages                                  |
|`/banwordadd word`     | Add a word (case insensitive) to the auto-ban list                              |
|`/banwordrm word`      | Remove a word from the auto-ban list                                            |
|`/banwordlist`         | List the words used for auto-banning                                            |
|`/trigger name en text`| Set the response of a trigger for a language                                    |
|`/ctrigger name en yes`| Turn the auto response of a trigger on or off for a language                   |
|`/triggerdesc name text`| Set the description of a trigger                                               |
|`/ul_f5`               | Clean up the empty entries left in the bot's user database                      |

### Administration commands in DM with @CardanoOfficialNews_bot bot

| Command               | Description                                                                    |
|-----------------------|--------------------------------------------------------------------------------|
|`/help`                | List the administration commands of the bot                                     |
|`/addme <password>`    | Register yourself as an authorized user of the bot                              |
|`/rmme`                | Remove your own registration as an authorized user of the bot                  |
|`/on #group`           | Turn the broadcast reception on for a group                                    |
|`/off #group`          | Turn the broadcast reception off for a group                                   |
|`/rm #group`           | Remove a group from the broadcast recipient list                               |
|`/con #channel`        | Turn the broadcast from a source channel on                                    |
|`/coff #channel`       | Turn the broadcast from a source channel off                                   |
|`/crm #channel`        | Remove a channel from the broadcast source list                                |
|`/taglist`             | List the groups the bot relays to, with their relay status                     |
|`/ctaglist`            | List the source channels the bot relays from, with their send status           |

Newsbot relays a short message with a preview link to the original announcement. It does not keep a copy of relayed messages, so edits and deletions in the source channel are not mirrored.

### Group onboarding

| Command               | Description                                                                    | Scope      |
|-----------------------|--------------------------------------------------------------------------------|------------|
|`/activatecharlie`     | Add the group to the list of groups moderated by @Charlie_Cardano_bot (admins only) | Group only |
