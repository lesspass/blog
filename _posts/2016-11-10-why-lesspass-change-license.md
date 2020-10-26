---
layout: post
title: "Why LessPass changed its license?"
author: "Guillaume Vincent"
redirect_from:
  - /why-lesspass-changed-its-license-4d3bf6045845
---

TL;DR: An open community starts with a good license. That’s why we decided to change LessPass license from MIT to GPLv3.


When we started the project we wanted a permissive license in order to be **developers-friendly**. If someone want to use lesspass-core in his software (closed or open source) he can. So when we initiated the repo, in November 2015, we chose the MIT license.
> # *But what’s the biggest problem an open source password manager can encounter ?*

In our opinion, it would be that someone found a breach in the code and don’t share it with the community.

As a community we are in ability to study open source code other programs. The bigger the community becomes, the more interesting it will be for an attacker to crack LessPass. So, we need to **encourage our community to go in the right direction and this should be done by design**, not accidentally.

The goal is to fight our –developers– bias to do highly technical stuff that only a few can use, and instead think **how we can offer, not just more, but better freedom to the community**. As without our community we don’t exists.

### 4 Principles of Free Software

1. The freedom to run the program as you wish, for any purpose ;

1. The freedom to study how the program works, and change it so it does your computing as you wish. Access to the source code is a precondition for this ;

1. The freedom to redistribute copies so you can help your neighbor ;

1. The freedom to distribute copies of your modified versions to others. By doing this you can give the whole community a chance to benefit from your changes. Access to the source code is a precondition for this.

The last point is very important :
> # *Give the whole community a chance to benefit from your changes*

### John Doe can be bad

Now, imagine someone, let’s call him *John Doe*, is making a closed-source software, distributing it and using lesspass-core. If John Doe found a bug, it could be interesting for him to stay silent and gain either financial or competitive benefits from that. This is bad for the community as it means bugs are not fixed as fast as they should and even could lead to potential exploit.
> *So we should try to prevent this behavior as much as we can.*

### License change

One way for us to do that is through the license we use and it should forbid the above mentioned use-case.

We choose the [GNU General Public License v3.0](http://choosealicense.com/licenses/gpl-3.0/), aka GNU GPLv3, which is a license that forbids our software to be used in a distributed closed source software. *Distributed* means *share to each of a number of recipients*. So if someone want to use LessPass in a closed source software without distributing it, he can. Actually one company making closed software is using lesspass-cli, and it’s totally fine. But if he try to distribute it, **he should open the source code to be compliant with the license**.

With Édouard we think about the community we want to build. We want to protect our community from dangerous things that can happen as much as we can.

We thank Taziden and Aeris for expressing their views on the subject. It helped us to ask ourself the right questions.

I would like to thank **Maxime** for his thorough re-reading of this article.
