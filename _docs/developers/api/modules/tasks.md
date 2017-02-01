---
title: Tasks
permalink: /docs/api/modules/tasks/
jumbotron:
  title: Tasks
  tagline: ""
  breadcrumbs:
  -
    label: Developers &raquo; API
    url: /docs/api/
---

* TOC
{:toc}

# Create

**POST /tasks/create.json**

Create a task object.

### Parameters
{: .no_toc}

|---
| Field | Type | 
|-|-|-
| `completed` | timestamp
| `due` | timestamp
| `is_completed` | bit
| `title` | string | **required**
| `updated` | timestamp
| `custom_*` | mixed | 

### Example
{: .no_toc}

<pre>
<code class="language-php">
$postfields = array(
    array('title','Finish documentation'),
);
$out = $cerb->post($base_url . 'tasks/create.json', $postfields);
</code>
</pre>

# Retrieve

**GET /tasks/`<id>`.json**

Retrieve a task object.

### Examples
{: .no_toc}

<pre>
<code class="language-php">
$out = $cerb->get($base_url . 'tasks/1.json');
</code>
</pre>

# Update

**PUT /tasks/`<id>`.json**

Update a task object.

### Parameters
{: .no_toc}

|---
| Field | Type | 
|-|-|-
| `completed` | timestamp
| `due` | timestamp
| `is_completed` | bit
| `title` | string
| `updated` | timestamp
| `custom_*` | mixed | 

### Example
{: .no_toc}

<pre>
<code class="language-php">
$postfields = array(
    array('title','Complete documentation'),
    array('assignee_id', '1'),
);
$out = $cerb->put($base_url . 'tasks/1.json', $postfields);
</code>
</pre>
	
# Search

**POST /tasks/search.json**

Perform a search for task objects.

### Parameters
{: .no_toc}

|---
| Field | Description | Type
|-|-|-
| `expand` | The keys to expand for each object as a comma-separated list | string
| `limit` | The number of results to display per page | integer
| `page` | The page of results to display given limit | integer
| `q` | Filters to add using quick search syntax | string
| `sortAsc` | `0` _(descending)_ or `1` _(ascending)_ | bit
| `sortBy` | The field to sort results by | string
| `subtotals[]` | Multiple subtotal sets can be returned | string 

**sortBy**

|---
| Field | Type | 
|-|-|-
| `completed` | timestamp
| `due` | timestamp
| `id` | integer
| `is_completed` | bit
| `title` | string
| `updated` | timestamp
| `watchers` | integer[]
| `custom_*` | mixed | 

**subtotals[]**

|---
| Field | Description | 
|-|-|-
| `fieldsets` | Custom fieldsets on the addresses
| `is_completed` | Tasks by completion status
| `links` | Objects linked to addresses
| `watchers` | Watchers on addresses

### Examples
{: .no_toc}

<pre>
<code class="language-php">
$postfields = array(
    array('q','due:today'),
    array('sortBy','id'),
    array('sortAsc','1'),
    array('page','1'),
);
$out = $cerb->post($base_url . 'tasks/search.json', $postfields);
</code>
</pre>

<pre>
<code class="language-php">
$postfields = array(
    array('criteria[]','title'),
    array('oper[]','like'),
    array('value[]','t*'),
    array('criteria[]','watchers'),
    array('oper[]','in'),
    array('value[]','[1,2,3]'),
    array('sortBy','id'),
    array('sortAsc','1'),
    array('page','1'),
);
$out = $cerb->post($base_url . 'tasks/search.json', $postfields);
</code>
</pre>

{% include api_toc.html %}