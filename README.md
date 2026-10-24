# Web Security Academy — SQL Injection & XSS Write-Up

**Challenge:** "Discover Your First Vulnerability in 4 Days" (تحدي اكتشاف اول ثغرة في اربع ايام)
**Author:** Ghadi Alzahrani
**Tools:** PortSwigger Web Security Academy, Burp Suite Community Edition
**Status:** 13/15 labs fully solved and documented; 2 labs documented as partial attempts (time-boxed / tooling-limited — see report for details)

## Overview

This repository contains my write-up for a 4-day hands-on challenge covering 15 labs from PortSwigger's Web Security Academy, split across two vulnerability classes:

- **SQL Injection (7 labs)** — login bypass, UNION-based data extraction via `information_schema`, blind SQLi via time delays, blind SQLi via conditional errors, and blind SQLi via out-of-band (OAST) data exfiltration.
- **Cross-Site Scripting (8 labs)** — reflected XSS, DOM-based XSS (various sinks: `document.write`, `innerHTML`, jQuery `.attr()`), and an AngularJS sandbox escape bypassing a CSP.

Each lab in the report follows a consistent structure: screenshot, HTTP request, HTTP response, notes, exploitation steps, and security impact.

## Methodology

All labs were approached manually using Burp Suite Community Edition — intercepting and modifying traffic through Proxy/Repeater, and using Intruder for character-by-character blind extraction where applicable. No automated scanners were used.

## Honest limitations

Two labs (blind SQLi via conditional time delays, and blind SQLi via out-of-band interaction) are documented as **partial attempts** rather than fully solved:
- One was stopped mid-extraction due to the 4-day time limit, after confirming the underlying technique works.
- The other's final verification step requires Burp Suite **Professional**'s Collaborator client (not available in the Community Edition used here); the payload was confirmed syntactically correct, but out-of-band callback verification could not be completed.

Both are documented transparently in the report rather than presented as complete.

## Contents

- `Vulnerability_Discovery_Writeup.pdf` — the full write-up (22 pages).

## Note

HTTP requests/responses in this report include session tokens issued by PortSwigger's temporary, per-user lab instances. These labs auto-expire and are deleted after a period of inactivity, so the tokens shown have no ongoing validity.
