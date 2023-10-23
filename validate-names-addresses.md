---
title: Validate company names and email addresses
ms.topic: how-to
ms.date: 1/11/2023
ms.service: partner-dashboard
ms.subservice: partnercenter-customers
description: Learn how to validate company names and email addresses in Partner Center.
author: jischulz
ms.author: jischulz
---

# Validate company names and email addresses

**Appropriate roles**: Global admin | User management admin | Admin agent | Sales agent

This article describes how to validate company names and email addresses in Partner Center. As part of our commitment to help partners and customers run their business based on trust, Microsoft requires that customer information be completed before accepting a partner relationship request or creating a new order through the CSP program.

In order to ensure an efficient customer verification process, make sure the Global Admin of the Customer tenant can ensure accuracy of their account information from the [Billing Accounts page](https://portal.office.com/adminportal/home?ref=/BillingAccounts/billing-accounts/AccountDetails) in the Microsoft Admin Center.

## Company name rules

As of September 22, 2021, these validation rules apply.

When you're entering a company name, the following aren't permitted:

- Using only one character
- Using only special characters, such as &$^# (See [Special characters that are allowed](#special-characters-that-are-allowed) below.)
- Using only spaces and/or tabs
- Using standalone abbreviations from the restricted list, such as llc, Inc, etc. (See the [Abbreviations that are allowed](#abbreviations-that-are-allowed), below.)

The following entries produce the warning, "*Please make sure your company name is correct. Your company name is used to approve your account creation*":

- Using names with internet Top-Level Domain (TDL) extensions, for example *.com*, *.org*, *.edu*, *.club*, and so on. (See [Top-level domain extensions that are allowed](#top-level-domain-extensions-that-are-allowed), below)
- Using the same character repeated three or more times with no other characters, for example "999"
- Using spaces or tabs mixed with individual characters, for example "1 2 3"

## Email address rules

When entering a customer email address:

- The address can't contain *@microsoft.com*.
- The address can't contain the same domain name as the partner. For example, a partner called *ABC* can't create a customer email address ending with *@abc.com*.

## Characters, abbreviations, and extensions that are allowed

### Special characters that are allowed

| Chars. | Chars. | Chars. | Chars. |
| ----- | ----- | -----| ----- |
| '~' | '-' |  '=' |  '_' |
|  '#' | '.' |  '%' |  '-' |
|  '+' |  ':' |  '^' |  '[' |
|  '$' |  '–' |  '&' |  ']' |
|  '@' |  '—' |  '*' |  '(' |
|  ',' |  ')' |  '"' |  '⟩' |
|  '`' |  '<' |  '!' |  '\\' |
|  '(' |  '>' |  '"' |  '/' |
|  ')' |  '{' |  '‘' |  '\|' |
|  '\' |  '}' |  '،' |  ':' |
|  ';' |  '⟨' |  ''' | '?' |
|  '"' |  '⟩' |  '\\' |  |

### Abbreviations that are allowed

| Abbr. | Abbr. | Abbr. | Abbr. |
| ----- | ----- | ----- | ----- |
|" c p a" | "pty" | "l. l. c." | "gmbh" |
| "c.p.a." | "pty ltd" | "l.l.c." | "plc" |
| "l.l.p." | "pte ltd" | " l l p" | "wll" |
| "c. p. a." | "private limited" | "corp" | "lda" |
| "l. l. p." | "pvt" | "corporation" | "sarl" |
| " l l c" | "pvt ltd" | "inc" | "kft" |
| "corp." | "zrt" | "incorporated" | "ltd" |
| "llc." | "ooo" | "limited" | "ltd." |
| "llp." | "llp" | "llc" | "sdn bhd"

### Top-level domain extensions that are allowed

| Ext.  | Ext.  | Ext.  | Ext. |
| ----- | ----- | ----- | ----- |
| .ac | .ba | .ca | .de |
| .ad | .bb | .cc | .dj |
| .ae | .bd | .cd | .dk |
| .af | .be | .cf | .dm |
| .ag | .bf | .cg | .do |
| .ai | .bg | .ch | .dz |
| .al | .bh | .ci | .fm |
| .am | .bi | .ck | .fo |
| .an | .bj | .cl | .fr |
| .ao | .bl | .cm | .ga |
| .aq | .bm | .cn | .gb |
| .ar | .bn | .co | .gd |
| .as | .bo | .cr | .ge |
| .at | .bq | .cu | .gf |
| .au | .br | .cv | .gg |
| .aw | .bs | .cw | .gh |
| .ax | .bt | .cx | .gi |
| .az | .bv | .cy | .gl |
| .ec | .bw | .cz | .gm |
| .ee | .by | .eu | .gn |
| .eg | .bz | .fi | .gp |
| .eh | .es | .fj | .gq |
| .er | .et | .fk | .gr |
| .gs | .gw | .hm | .ht |
| .gt | .gy | .hn | .hu |
| .gu | .hk | .hr | .id |
| .ie | .kz | .mo | .nz |
| .il | .la | .mp | .om |
| .im | .lb | .mq | .pa |
| .in | .lc | .mr | .pe |
| .io | .li | .ms | .pf |
| .iq | .lk | .mt | .pg |
| .ir | .lr | .mu | .ph |
| .is | .ls | .mv | .pk |
| .it | .lt | .mw | .pl |
| .je | .lu | .mx | .pm |
| .jm | .lv | .my | .pn |
| .jo | .ly | .mz | .pr |
| .jp | .ma | .na | .ps |
| .ke | .mc | .nc | .pt |
| .kg | .md | .ne | .pw |
| .kh | .me | .nf | .py |
| .ki | .mf | .ng | .qa |
| .km | .mg | .ni | .re |
| .kn | .mh | .nl | .ro |
| .kp | .mk | .no | .rs |
| .kr | .ml | .np | .ru |
| .kw | .mm | .nr | .rw |
| .ky | .mn | .nu | .sa |
| .sb | .tf | .vc | .中国 |
| .sc | .tg | .ve | .中國 |
| .sd | .th | .vg | .భారత్ |
| .se | .tj | .vi | .ලංකා |
| .sg | .tk | .vn | .ભારત |
| .sh | .tl | .vu | .भारतम् |
| .si | .tm | .wf | .भारत |
| .sj | .tn | .ws | .भारोत |
| .sk | .to | .ಭಾರತ | .укр |
| .sl | .tp | .한국 | .香港 |
| .sm | .tr | .ଭାରତ | .台湾 |
| .sn | .tt | .ভাৰত | .台灣 |
| .so | .tv | .ভারত | .мон |
| .sr | .tw | .சிங்கப்பூர் | .tc |
| .ss | .tz | .sz | .td |
| .st | .ua | .বাংলা | .uz |
| .su | .ug | .қаз | .va |
| .sv | .uk | .срб | .мкд |
| .sx | .um | .бг | .ею |
| .sy | .us | .бел | uy |
| .tc | .uz | .мкд |  |
