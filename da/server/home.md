---
title: About expressional.social
description: 
published: true
date: 2023-01-02T19:59:02.836Z
tags: 
editor: markdown
dateCreated: 2023-01-02T16:54:43.825Z
---

# Home

Hello from Copenhagen, Denmark! 🇩🇰 The server is public and welcomes everyone who follows the rules.

Click here for [Abuse, reporting, and moderation details](#reporting-and-moderation)

> **_expressional_ (/ɪkˈspɹɛʃ.ən.əl/, /ɛkˈspɹɛʃ.ən.əl/)**
>
> *Of or pertaining to expression; having the power of expression; particularly, in the fine arts, embodying a conception or emotion; representing a definite meaning or feeling.*
{.is-info}

## Intro

This server is adhering to the [Mastodon Server Covenant](https://joinmastodon.org/covenant){target=_blank}, which mean that we have:

* Active moderation against racism, sexism, homophobia, and transphobia
* Daily backups
* At least one other person with emergency access to the server infrastructure
* A commitment to giving users at least 3 months of advance warning in case of shutting down

## About the server

Our goal is to host a stable, secure, safe, and well-moderated Mastodon server that follows all Danish and European laws and best practices.

Beyond the strict local and international legal requirements, We also want to make the server a safe space for minorities of any kind, aggressively pruning out trolls and bad-faith actors and servers.

As mentioned in the [`choosing a server`](/en/learn/choosing-a-Mastodon-server){target=_blank} section, there is a lot of things to consider when choosing a server.

If you don't know me, picking my server is a leap of faith, and I don't take that responsibility lightly - thank you.

### Longevity promise

> We follow (and in many ways, exceed) the [Mastodon Server Covenant](https://joinmastodon.org/covenant){target="_blank"}
{.is-info}

I'm very committed to the longevity of this Mastodon server. I use it myself to follow friends, colleagues, and industry experts within my interests and hobbies.

If _and it's a big if_, I ever decided to stop this server, I promise at least 3-month advance notice as per the Mastodon Server Covenant.

Mastodon has very robust [account migration between servers](https://expressional.social/move){target="_blank"} built into the service that will ensure you will never lose your followers or data.

You can always [import and export your data](https://expressional.social/settings/export){target="_blank"} on demand from your profile settings interface.

### Stability promise

> I can guarantee that there will *not* be 100% uptime. 100% uptime is a lie. It doesn't exist. Not even on Twitter
{.is-info}

I'm very committed to running a stable and fast Mastodon server. My goal is at least [99.5% uptime](https://uptime.is/99.5){target="_blank"}. It will very, very likely be significantly better; other services I run usually sit at or above [99.95% uptime](https://uptime.is/99.95){target="_blank"}.

I'm offering the service for free, so I'm not making any guarantees, so consider it a "best effort." That being said, I take uptime and service stability very seriously; having great uptime is what I'm paid to do in my day job.

Most interruptions will likely be short (~5min or less) as part of maintenance work on the server or software.

You can see [server utilization and uptime monitoring in this public dashboard](https://expressional.social/monitor){target="_blank"}

### Security model

Security will never be perfect; it's constantly evolving with new threat models, software bugs, and 0-day vulnerabilities. I'm not going to claim my Mastodon server security posture is perfect; it probably isn't.

To the best of my ability, I've taken multiple steps to secure your data (and mine!), and the following sections outline these steps.

> The following security information is a bit technical and may even look like technobabble to regular people. Feel free to skip it
{.is-info}

#### Physical access

I can physically touch the server that hosts the Mastodon server, and there are *no* 3rd parties that have any kind of physical or virtual access to it.

#### Logical access

The Mastodon server is running on an isolated virtual machine with no other services running on that machine. Furthermore, Mastodon is running inside Docker containers locked down with `read-only` volumes where possible, and unprivileged users are running the services within each Docker container.

Remote access via SSH only accepts secure cryptographic keys. Static passwords and other insecure authentication methods are disabled.

All accounts are, of course protected by *strong* (long) passwords and [Two-Factor Authentication (2FA)](https://en.wikipedia.org/wiki/Multi-factor_authentication){target=_blank}.

#### Network

![access.png](/about/access.png)

The Mastodon server runs on an isolated VLAN network with a default `DENY` policy for all ingress network traffic.

There are no ingress port forwarding to the server, but rather the instance connects to the Cloudflare network via [Cloudflare Tunnel](https://www.cloudflare.com/products/tunnel/){target=_blank}, that in turn forwards traffic to the server.

Access to the server from the public internet is only possible through [Cloudflare Access Zero Trust](https://www.cloudflare.com/products/zero-trust/access/){target=_blank} - this is true for *all* traffic flowing through the `expressional.social` domain in general.

This setup prevents any *direct* access to the server from the public internet. It puts Cloudflare along with their [security capabilities](https://www.cloudflare.com/waf/){target=_blank} and [DDoS protection](https://www.cloudflare.com/ddos-hub/){target=_blank} in between attackers and the server itself.

The setup also enforces full end-to-end encryption from your device, over the internet, and onto the Mastodon server. The server doesn't accept traffic not coming through Cloudflare in the first place, so bypassing it is (probably) impossible.

Cloudflare also provides [Content Delivery Network (CDN)](https://www.cloudflare.com/cdn/){target=_blank}, ensuring fast global access to images and other resources on the page, ensuring a snappy experience for everyone - and reduced cost and workload on the Mastodon server itself.

#### Admin & Mod access

The Mastodon admin and moderation UI that show sensitive user information such as IP addresses and e-mail addresses are additionally placed behind [Cloudflare Access](https://www.cloudflare.com/products/zero-trust/access/){target=_blank}, which enforces me (and potentially future moderators) to *double authenticate* with both our Google account and our regular Mastodon user + password + [Two-Factor Authentication (2FA)](https://en.wikipedia.org/wiki/Multi-factor_authentication){target=_blank}.

This Google account authentication step happens `at the edge` before traffic gets to the Mastodon server itself. This help blocks any *potential* exploits in the Mastodon software that could attack or try to bypass these elevated and sensitive pages. Any authenticated sessions accessing sensitive data automatically expire after 1 hour to avoid any lingering elevated access that potentially could be abused.

This setup also allows for a clear audit trail of who accessed the sensitive pages and when in case of abuse.

### Economy

Currently I'm happy to pay for the server out of pocket without accepting donations. The mastodon server is using idle capacity on an existing server, so there are no additional cost associated with running the server at this time.

If the server grows to a point where the cost gets significant, or a dedicated server is needed, I will probably open up for donations for anyone wanting to contribute a bit.

The longevity of the server will *not* be tied to donations from people on the server. I would rather stop accepting new signups and cap cost that way, rather than turn off the server due to increasing costs.

Before creating this Mastodon server and making it public, I had already made up my mind that I would be fine paying for a decently sized server out of pocket if needed, without any donations. Basically, a decent amount of cost is already factored into my private financial planning, avoiding any kind of service disruptions due to cost increases.

### Server / hardware / internet

The mastodon server is using idle capacity on an existing server, so there are a decent amount of capacity to grow into.

Technically the server specs are:

- CPU: i7-10700
- RAM: 64 GB
- Disk: 2x2 TB SSD in RAID-1 + 2 TB NVMe without raid + ~20 TB NAS for backup/storage
- WAN: 1000/1000
- LAN: 10 GbE / 10 GbE

You can follow the resource usage on our [public monitoring dashboard](https://expressional.social/monitor){target="_blank"}

### Who has access to my data?

Only the owner ([@jippi](https://expressional.social/@jippi){target="_blank"}) has physical or virtual access to the data hosted on this server.

No moderators have access to data beyond what's needed to do content moderation. Moderators do not have access to your _direct messages_.

### How is my data protected?

The server is backed up twice daily (10am and 10pm), ensuring any potential data loss can easily be recovered with minimal data loss.

The backups are stored locally in Copenhagen, Denmark, and on remote storage via [Backblaze](https://www.backblaze.com/){target="_blank"} - both local and remote backups are encrypted.

I will never sell or hand over the server or data to someone else.

### Where is my data located?

The server is physically located in Copenhagen, Denmark.

### Who owns the server?

Hi, hello, mojn! 👋

I'm Christian, a 38-ish-year-old, happily married, Aspergers + ADHD guy living in Copenhagen, Denmark, that loves to tinker with technology and servers (the `magic` box that runs this Mastodon server, for example).

To finance my hobbies, I work as Staff Engineer (senior++) on the Platform team for an American ticketing company called [SeatGeek](https://seatgeek.com/){target="_blank"}. Basicallly my job is to make servers work reliably, fast and secure.

You can [follow me on Mastodon](https://expressional.social/@jippi) or [check out my website](https://jippi.dev){target="_blank"}.

## How do I join your server?

If you **don't** have a Mastodon account elsewhere, then [sign up and create a user](https://expressional.social/auth/sign_up){target=_blank}.

If you have an account on another Mastodon server, please see the [How do I move my existing account to your server?](https://expressional.social/move){target=_blank} guide.

## Collaboration

If you are passionate about creating vibrant and safe communities, I would be interested in collaborating - please reach out.

In particular, I'm interested in a non-profit structure/entity that could own and manage the server so that the server would have longevity beyond my single human engagement and interest - and a better-governing structure that isn't tied to me alone.

## Reporting and moderation

When reporting accounts, please include at least a few posts showing rule-breaking behavior when applicable. If there is any additional context that might help make a decision, please also include it in the comment. This is especially important when the content is in a language nobody on the moderation team speaks.

We usually handle reports within 24 hours. Please mind that you are not notified when a report you have made has led to punitive action and that not all punitive actions are externally visible. For first-time offenses, we may opt to delete offending content, escalating to harsher measures on repeat offenses.

## Team

> For moderation/spam/reporting please use the built-in reporting functionality rather than reaching out to the team directly
{.is-warning}

- 🇩🇰 [@jippi](https://expressional.social/@jippi){target=_blank rel=me} - Owner
- 🇩🇰 [@aphandersen](https://expressional.social/@aphandersen){target=_blank rel=me} - Admin
- 🇩🇰 [@bot](https://expressional.social/@bot){target=_blank rel=me} - Official Bot
