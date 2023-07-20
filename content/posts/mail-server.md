---
title: mail-server
date: 2023-07-20T12:16:13+08:00
draft: False
featuredImage: https://images.unsplash.com/photo-1544215818-53eb272de57f?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE2ODk4MjY1MDR8&ixlib=rb-4.0.3
featuredImagePreview: https://images.unsplash.com/photo-1544215818-53eb272de57f?ixid=M3w0NjAwMjJ8MHwxfHJhbmRvbXx8fHx8fHx8fDE2ODk4MjY1MDR8&ixlib=rb-4.0.3
---

# [stalwartlabs/mail-server](https://github.com/stalwartlabs/mail-server)

# Stalwart Mail Server

[![Test](https://github.com/stalwartlabs/mail-server/actions/workflows/test.yml/badge.svg)](https://github.com/stalwartlabs/mail-server/actions/workflows/test.yml)
[![Build](https://github.com/stalwartlabs/mail-server/actions/workflows/build.yml/badge.svg)](https://github.com/stalwartlabs/mail-server/actions/workflows/build.yml)
[![License: AGPL v3](https://img.shields.io/badge/License-AGPL_v3-blue.svg)](https://www.gnu.org/licenses/agpl-3.0)
[![](https://img.shields.io/discord/923615863037390889?label=Chat)](https://discord.gg/jtgtCNj66U)
[![](https://img.shields.io/twitter/follow/stalwartlabs?style=flat)](https://twitter.com/stalwartlabs)

**Stalwart Mail Server** is an open-source mail server solution with JMAP, IMAP4, and SMTP support and a wide range of modern features. It is written in Rust and designed to be secure, fast, robust and scalable.

Key features:

- **JMAP** server:
  - JMAP Core ([RFC 8620](https://datatracker.ietf.org/doc/html/rfc8620))
  - JMAP Mail ([RFC 8621](https://datatracker.ietf.org/doc/html/rfc8621))
  - JMAP over WebSocket ([RFC 8887](https://datatracker.ietf.org/doc/html/rfc8887))
  - JMAP for Sieve Scripts ([DRAFT-SIEVE-13](https://www.ietf.org/archive/id/draft-ietf-jmap-sieve-13.html))
- **IMAP4** server:
  - IMAP4rev2 ([RFC 9051](https://datatracker.ietf.org/doc/html/rfc9051)) full compliance.
  - IMAP4rev1 ([RFC 3501](https://datatracker.ietf.org/doc/html/rfc3501)) backwards compatible.
  - ManageSieve ([RFC 5804](https://datatracker.ietf.org/doc/html/rfc5804)) server.
  - Numerous [extensions](https://stalw.art/docs/development/rfcs#imap4-and-extensions) supported.
- **SMTP** server:
  - Built-in [DMARC](https://datatracker.ietf.org/doc/html/rfc7489), [DKIM](https://datatracker.ietf.org/doc/html/rfc6376), [SPF](https://datatracker.ietf.org/doc/html/rfc7208) and [ARC](https://datatracker.ietf.org/doc/html/rfc8617) support for message authentication.
  - Strong transport security through [DANE](https://datatracker.ietf.org/doc/html/rfc6698), [MTA-STS](https://datatracker.ietf.org/doc/html/rfc8461) and [SMTP TLS](https://datatracker.ietf.org/doc/html/rfc8460) reporting.
  - Inbound throttling and filtering with granular configuration rules and Sieve scripting.
  - Virtual queues with delayed delivery, priority delivery, quotas, routing rules and throttling support.
- **Flexible**:
  - **LDAP** directory and **SQL** database authentication.
  - Full-text search available in 17 languages.
  - Disk quotas.
  - Sieve scripting language with support for all [registered extensions](https://www.iana.org/assignments/sieve-extensions/sieve-extensions.xhtml).
  - Email aliases, mailing lists, subaddressing and catch-all addresses support.
  - Integration with **OpenTelemetry** to enable monitoring, tracing, and performance analysis.
- **Secure**:
  - OAuth 2.0 [authorization code](https://www.rfc-editor.org/rfc/rfc8628) and [device authorization](https://www.rfc-editor.org/rfc/rfc8628) flows.
  - Access Control Lists (ACLs).
  - Rate limiting.
- **Robust and scalable**:
  - **FoundationDB** or **SQLite** database backends.
  - **S3-compatible** blob storage support.
  - Memory safe (thanks to Rust).

## Get Started

Install Stalwart Mail Server on your server by following the instructions for your platform:

- [Linux / MacOS](https://stalw.art/docs/install/linux)
- [Windows](https://stalw.art/docs/install/windows)
- [Docker](https://stalw.art/docs/install/docker)

All documentation is available at [stalw.art/docs/get-started](https://stalw.art/docs/get-started).

## Support

If you are having problems running Stalwart Mail Server, you found a bug or just have a question,
do not hesitate to reach us on [Github Discussions](https://github.com/stalwartlabs/mail-server/discussions),
[Reddit](https://www.reddit.com/r/stalwartlabs) or [Discord](https://discord.gg/aVQr3jF8jd).
Additionally you may become a sponsor to obtain priority support from Stalwart Labs Ltd.

## Funding

Part of the development of this project was funded through the [NGI0 Entrust Fund](https://nlnet.nl/entrust), a fund established by [NLnet](https://nlnet.nl/) with financial support from the European Commission's [Next Generation Internet](https://ngi.eu/) programme, under the aegis of DG Communications Networks, Content and Technology under grant agreement No 101069594.

If you find the project useful you can help by [becoming a sponsor](https://github.com/sponsors/stalwartlabs). Thank you!

## License

Licensed under the terms of the [GNU Affero General Public License](https://www.gnu.org/licenses/agpl-3.0.en.html) as published by
the Free Software Foundation, either version 3 of the License, or (at your option) any later version.
See [LICENSE](LICENSE) for more details.

You can be released from the requirements of the AGPLv3 license by purchasing
a commercial license. Please contact licensing@stalw.art for more details.
  
## Copyright

Copyright (C) 2023, Stalwart Labs Ltd.
