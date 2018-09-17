---
title: Bonita BICI Rest API documentation
language_tabs:
  - shell: Shell
  - http: HTTP
  - javascript: JavaScript
  - javascript--nodejs: Node.JS
  - ruby: Ruby
  - python: Python
  - java: Java
  - go: Go
toc_footers: []
includes: []
search: true
highlight_theme: darkula
headingLevel: 2

---

<h1 id="Bonita-BICI-Rest-API-documentation">Bonita BICI Rest API documentation v1.1</h1>

BICI provides a set of REST Api extensions deployed by BICI intaller. This page lists all extensiosns avalaibles

Base URLs:

* <a href="/bonita/API/extension/">/bonita/API/extension/</a>

<h1 id="Bonita-BICI-Rest-API-documentation-Default">Default</h1>

## getCaseList

<a id="opIdgetCaseList"></a>

`GET /ici-case-api`

<h3 id="getcaselist-parameters">Parameters</h3>

|Parameter|In|Type|Required|Description|
|---|---|---|---|---|
|c|query|string|false|none|
|p|query|string|false|none|
|processName|query|string|false|none|
|processVersion|query|string|false|none|
|status|query|string|false|none|
|search|query|string|false|none|

> Example responses

> default Response

<h3 id="getcaselist-responses">Responses</h3>

|Status|Meaning|Description|Schema|
|---|---|---|---|
|default|Default|default response|string|

<aside class="success">
This operation does not require authentication
</aside>

