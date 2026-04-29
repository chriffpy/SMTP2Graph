# SMTP2Graph (Sharpflix fork)

> **This is a patched fork of [SMTP2Graph/SMTP2Graph](https://github.com/SMTP2Graph/SMTP2Graph)**, maintained by **Sharpflix GmbH** (Solingen, Germany), with three production-reliability fixes for Linux bulk-mail relay:
>
> 1. **EML filename uniqueness** — guarantees the on-disk filename stays unique even when two SMTP sessions are issued the same `session.id` within a millisecond (otherwise the second message overwrites the first and is silently lost under concurrent bulk sends).
> 2. **Reverts upstream PR #52** — the EML writeStream handler is back on `'finish'` instead of `'close'`. On Linux + production webpack build, `'close'` does not fire reliably and every received message was dropped before reaching the queue. **This fork is Linux-only**; Windows users should use upstream.
> 3. **Always-on verbose mailer logs** — adds `log()` calls in `Mailer` around the send pipeline (`Preparing to send mail …`, `Sending message as …`, `Message sent successfully …`, etc.) and hardcodes the build-time `DEBUG` flag to `true` so production bundles stay at log level `verbose`. Required for any external log-based monitoring.
>
> Tags follow the pattern `v<upstream>-bsg.<n>` — current tag is `v1.1.4-bsg.2`. The Docker image built from this source is published as [`ghcr.io/chriffpy/better-smtp2graph`](https://github.com/chriffpy/better-smtp2graph). All changes are GPL-3.0, inherited from upstream.
>
> ---

> SMTP2Graph is a robust, versatile and lightweight multiplatform application that will run an SMTP server which relays messages over Microsoft 365/Exchange Online using the Microsoft Graph API.

[![GitHub Last Release](https://img.shields.io/github/v/release/SMTP2Graph/SMTP2Graph?style=for-the-badge)](https://github.com/SMTP2Graph/SMTP2Graph/releases)
[![GitHub Last Release Date](https://img.shields.io/github/release-date/smtp2graph/smtp2graph?style=for-the-badge)](https://github.com/SMTP2Graph/SMTP2Graph/releases)
[![GitHub Sponsors](https://img.shields.io/github/sponsors/smtp2graph?style=for-the-badge&logo=githubsponsors)](https://github.com/sponsors/SMTP2Graph)
[![GitHub Repo stars](https://img.shields.io/github/stars/smtp2graph/smtp2graph?style=for-the-badge&logo=github&color=E3B341)](https://github.com/SMTP2Graph/SMTP2Graph/stargazers)
[![Docker pulls](https://img.shields.io/docker/pulls/smtp2graph/smtp2graph?style=for-the-badge&logo=docker)](https://hub.docker.com/r/smtp2graph/smtp2graph)

## Documentation
[Full documentation](https://www.smtp2graph.com) | [Installation](https://www.smtp2graph.com/#/installation)

## What is it

SMTP2Graph is an SMTP server that will send messages over the Microsoft 365/Exchange Online platform. You don't need a userlicense for this, but you need to create an application registration in Entra ID (Azure AD) and assign it the desired permissions.

## Features

- SMTP AUTH support (PLAIN and LOGIN)
- TLS support
- IP whitelist
- FROM whitelist
- Rate limiter
- Brute force protection
- No issues with SPF/DKIM/DMARC (it's handled by M365)

## Support the project

If you like this project, please consider supporting its development.

[![GitHub Sponsors](https://img.shields.io/badge/Sponsor-Github?style=for-the-badge&logo=githubsponsors&label=GitHub)](https://github.com/sponsors/SMTP2Graph)
[![Paypal donation](https://img.shields.io/badge/Donate-2997D8?style=for-the-badge&logo=paypal&label=Paypal)](https://paypal.me/roelvbdev)
