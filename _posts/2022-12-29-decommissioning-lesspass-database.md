---
layout: post
title: "Decommissioning LessPass Database"
author: "Guillaume Vincent"
---

TLDR: LessPass Database server will be turned off on March 1th, 2023. The static version of LessPass, the web extension and the mobile versions remain in place.

# We deviate from the original idea

LessPass doesn't save any passwords: it computes them from your login and site, on demand. It eliminates database dependency.

For this to work, all sites must accept complex passwords of length 16 (default length of LessPass) with symbols and numbers. And surprise it is far from being the case. To overcome this problem, I quickly created the LessPass Database connected version after launching LessPass. An API that allows you to save your password profiles.

By doing this we were slowly deviating from the main benefit of LessPass: "Stop wasting your time synchronizing your encrypted vault."

# Lastpass Data Breach

Last December 22, Lastpass (one of the most popular password managers) made an worrying announcement: a data breach exposed users' encrypted password vaults. We don't know how many password vaults were compromised in the breach and how many users were affected. We also know that some information such as URLs of registered sites were not encrypted.

The more I read articles on the subject, the more I discovered the danger in which the users of Lastpass were because of this unencrypted data. Even data like URLs. I realized that my users were potentially in more danger than I thought. All password profiles are not encrypted in LessPass Database. An example password profile:

```
     {
          "id": "uuid",
          "login": "contact@lesspass.com",
          "site": "example.org",
          "lowercase": true,
          "uppercase": true,
          "symbols": false,
          " numbers": true,
          "counter": 1,
          "length": 16,
          "version": 2,
          "created": "2019-11-03T11:12:25.987522Z",
          "modified": "2021-11-03T11 :12:25.987603Z"
     }
```

These profiles should be encrypted. It takes a lot of work to encrypt current user data.

# Maintenance cost

Maintain the LessPass service for free has a cost. It's a cost in time, in money to pay the server, the software licenses ($315/year). I want to reduce those loads to focus on something else.

# Find the motivation

On LessPass I always liked developing on it, but over time, I lost motivation. Nevertheless, I have a taste of unfinished work in the world of stateless password managers. I don't know if by freeing up my time I will be able to develop more on LessPass, or if I will regain my motivation. But I need to slow down.

# And oh wait, how am I doing?

For all LessPass Database users, I added an option on the CLI (`--export`) and soon on the web extension to export their passwords in plain text in a CSV file that works with Bitwarden and Google Passwords. If you want to export your LessPass passwords, you can.

# I didn't know my data was not encrypted, can I delete my account ?

To completely delete your account from LessPass Database, simply use the iOS or Android application and click on `My account` > `Danger Zone` > `Delete my account`. It deletes everything. 2 weeks later you would completely disappear from the backups of the LessPass database.

# I'm sorry

It's not easy to give up. LessPass is the biggest project I've worked on, had fun on, learned from. The community is wonderful. Thank you for using LessPass. :heart:

LessPass will still exist but in its static version. Without database. Back to basics.

# Calendar

- ASAP: update web extension to help user exporting they passwords
- ASAP: update all applications to refuse new accounts
- ASAP: update all applications to show this blog post
- March 1, 2023: I will stop the server
- June 1, 2023: I will delete the latest backup forever
