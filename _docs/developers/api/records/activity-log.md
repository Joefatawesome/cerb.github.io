---
title: Activity Log
permalink: /docs/api/records/activity-log/
jumbotron:
  title: Activity Log
  tagline: ""
  breadcrumbs:
  -
    label: Developers &raquo; API &raquo;
    url: /docs/api/
  -
    label: Records
    url: /docs/api/#records
---

* TOC
{:toc}

# Records API

**URI:** `activity_log`

Refer to the [/records](/docs/api/modules/records/) API.

# Examples

## Get an activity log record by ID

**Request:**

<pre>
<code class="language-http">
GET /rest/records/activity_log/1.json?expand=custom_&show_meta=0 HTTP/1.1
Cerb-Auth: XXXX:XXXX
Date: Fri, 10 Nov 2017 22:21:26 GMT
Host: cerb.example
Content-Type: application/x-www-form-urlencoded; charset=utf-8
</code>
</pre>

**Response:**

<pre>
<code class="language-json">
{
  "__build": 2017110901,
  "__status": "success",
  "__version": "8.2.2",
  "_context": "cerberusweb.contexts.activity_log",
  "_label": "Kina Halpue logged in from ::1 using Safari 10.1.1 for Macintosh",
  "activity_point": "worker.logged_in",
  "actor__context": "cerberusweb.contexts.worker",
  "actor_id": "1",
  "created": "1497056804",
  "event": "Worker Logged In",
  "id": "1",
  "target__context": "",
  "target_id": "0"
}
</code>
</pre>

## Search activity log entries on a specific record

**Request:**

<pre>
<code class="language-http">
GET /rest/records/activity_log/search.json?q=activity:worker.logged_in&show_meta=0 HTTP/1.1
Cerb-Auth: XXXX:XXXX
Date: Fri, 10 Nov 2017 22:44:45 GMT
Content-Type: application/x-www-form-urlencoded; charset=utf-8
Host: cerb.example
</code>
</pre>

**Response:**

<pre>
<code class="language-json">
{
  "__build": 2017110901,
  "__status": "success",
  "__version": "8.2.2",
  "count": 10,
  "page": 1,
  "results": [
    {
      "_context": "cerberusweb.contexts.activity_log",
      "_label": "Kina Halpue logged in from ::1 using Safari 10.1.1 for Macintosh",
      "id": "1",
      "activity_point": "worker.logged_in",
      "created": "1497056804",
      "event": "Worker Logged In",
      "actor__context": "cerberusweb.contexts.worker",
      "actor_id": "1",
      "target__context": "",
      "target_id": "0"
    },
    ...
  ],
  "total": "1000"
}
</code>
</pre>

## Create an activity log entry

**Request:**

<pre>
<code class="language-http">
POST /rest/records/activity_log/create.json?show_meta=0 HTTP/1.1
Cerb-Auth: XXXX:XXXX
Date: Fri, 10 Nov 2017 22:47:53 GMT
Content-Type: application/x-www-form-urlencoded; charset=utf-8
Host: cerb.example
</code>
</pre>

<pre>
<code class="language-text">
fields[activity_point]=custom.other
&fields[actor__context]=worker
&fields[actor_id]=1
&fields[created]=1510354073
&fields[params][message]=This is a custom message on another worker.
&fields[target__context]=worker
&fields[target_id]=3
</code>
</pre>

**Response:**

<pre>
<code class="language-json">
{
  "__build": 2017110901,
  "__status": "success",
  "__version": "8.2.2",
  "_context": "cerberusweb.contexts.activity_log",
  "_label": "This is a custom message on another worker.",
  "activity_point": "worker.logged_in",
  "actor__context": "cerberusweb.contexts.worker",
  "actor_id": "1",
  "created": "1510354073",
  "event": "(Other)",
  "id": "2615",
  "target__context": "cerberusweb.contexts.worker",
  "target_id": "3"
}
</code>
</pre>

{% include api_toc.html %}
