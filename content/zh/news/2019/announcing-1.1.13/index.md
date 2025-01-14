---
title: Announcing Istio 1.1.13
description: Istio 1.1.13 patch release.
publishdate: 2019-08-13
attribution: The Istio Team
release: 1.1.13
aliases:
    - /zh/about/notes/1.1.13
    - /zh/blog/2019/announcing-1.1.13
    - /zh/news/announcing-1.1.13
---

We're pleased to announce the availability of Istio 1.1.13. Please see below for what's changed.

{{< relnote >}}

## Security update

This release contains fixes for the security vulnerabilities described in [our August 13th, 2019 news post](/news/security/istio-security-2019-003-004/).  Specifically:

__ISTIO-SECURITY-2019-003__: An Envoy user reported publicly an issue (c.f. [Envoy Issue 7728](https://github.com/envoyproxy/envoy/issues/7728)) about regular expressions matching that crashes Envoy with very large URIs.
  * __[CVE-2019-14993](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-14993)__: After investigation, the Istio team has found that this issue could be leveraged for a DoS attack in Istio, if users are employing regular expressions in some of the Istio APIs: `JWT`, `VirtualService`, `HTTPAPISpecBinding`, `QuotaSpecBinding`.

__ISTIO-SECURITY-2019-004__: Envoy, and subsequently Istio are vulnerable to a series of trivial HTTP/2-based DoS attacks:
  * __[CVE-2019-9512](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-9512)__: HTTP/2 flood using `PING` frames and queuing of response `PING` ACK frames that results in unbounded memory growth (which can lead to out of memory conditions).
  * __[CVE-2019-9513](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-9513)__: HTTP/2 flood using PRIORITY frames that results in excessive CPU usage and starvation of other clients.
  * __[CVE-2019-9514](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-9514)__: HTTP/2 flood using `HEADERS` frames with invalid HTTP headers and queuing of response `RST_STREAM` frames that results in unbounded memory growth (which can lead to out of memory conditions).
  * __[CVE-2019-9515](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-9515)__: HTTP/2 flood using `SETTINGS` frames and queuing of `SETTINGS` ACK frames that results in unbounded memory growth (which can lead to out of memory conditions).
  * __[CVE-2019-9518](https://cve.mitre.org/cgi-bin/cvename.cgi?name=CVE-2019-9518)__: HTTP/2 flood using frames with an empty payload that results in excessive CPU usage and starvation of other clients.
  * See [this security bulletin](https://github.com/Netflix/security-bulletins/blob/master/advisories/third-party/2019-002.md) for more information

Nothing else is included in this release except for the above security fixes.
