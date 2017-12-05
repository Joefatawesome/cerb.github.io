---
title: API Responses
permalink: /docs/api/topics/responses/
jumbotron:
  title: API Responses
  tagline: ""
  breadcrumbs:
  -
    label: Docs &raquo;
    url: /docs/home/
  -
    label: API &raquo;
    url: /docs/api/
---

The Web API answers requests with one or more **objects** encoded in JSON or XML.  Each response is a single-level **dictionary** of **key**/**value** pairs.

* TOC
{:toc}

# Dictionaries

Suppose we send this `GET` request to the API to retrieve ticket #123 in JSON format:

<pre>
<code class="language-http">
GET /rest/tickets/123.json
</code>
</pre>

The response is a dictionary with several keys:

<pre>
<code class="language-json">
{
    __build: 2017013001,
    __status: "success",
    __version: "7.3.0",
    _context: "cerberusweb.contexts.ticket",
    _label: "[#JCA-16346-351] Do you offer volume discounts?",
    bucket__context: "cerberusweb.contexts.bucket",
    bucket_id: 6,
    closed_at: 0,
    created: 1360990928,
    elapsed_resolution_first: "0",
    elapsed_response_first: "0",
    group__context: "cerberusweb.contexts.group",
    group_id: 6,
    id: 123,
    initial_message__context: "cerberusweb.contexts.message",
    initial_message_id: 1195,
    initial_message_sender__context: "cerberusweb.contexts.address",
    initial_message_sender_org__context: "cerberusweb.contexts.org",
    initial_message_worker__context: "cerberusweb.contexts.worker",
    initial_message_worker_address__context: "cerberusweb.contexts.address",
    initial_message_worker_address_org__context: "cerberusweb.contexts.org",
    initial_response_message__context: "cerberusweb.contexts.message",
    initial_response_message_id: 0,
    initial_response_message_sender__context: "cerberusweb.contexts.address",
    initial_response_message_sender_org__context: "cerberusweb.contexts.org",
    initial_response_message_worker__context: "cerberusweb.contexts.worker",
    initial_response_message_worker_address__context: "cerberusweb.contexts.address",
    initial_response_message_worker_address_org__context: "cerberusweb.contexts.org",
    latest_message__context: "cerberusweb.contexts.message",
    latest_message_id: 1195,
    latest_message_sender__context: "cerberusweb.contexts.address",
    latest_message_sender_org__context: "cerberusweb.contexts.org",
    latest_message_worker__context: "cerberusweb.contexts.worker",
    latest_message_worker_address__context: "cerberusweb.contexts.address",
    latest_message_worker_address_org__context: "cerberusweb.contexts.org",
    mask: "JCA-16346-351",
    num_messages: "1",
    org__context: "cerberusweb.contexts.org",
    org_id: 51,
    owner__context: "cerberusweb.contexts.worker",
    owner_address__context: "cerberusweb.contexts.address",
    owner_id: 0,
    reopen_date: 0,
    spam_score: 0.0001,
    spam_training: "",
    status: "open",
    subject: "Do you offer volume discounts?",
    updated: 1360990928,
    url: "https://cerb.example.com/profiles/ticket/JCA-16346-351"
}</code>
</pre>

A dictionary is an array of **keys** and their associated **values**.  You may recognize some of the keys in the example above, because these dictionaries are also used by features like [bots](/docs/bots/), snippets, [dashboard widgets](/docs/dashboards/), and [worklist](/docs/workspaces/#worklists) exports.

Dictionaries have a hierarchal structure, but all of the keys within a dictionary are at the same level.  Keys are logically partitioned using namespaces to represent distinct records with parent/child relationships.

Let's consider a real-world example to demonstrate this concept.

A simplified ticket record has a hierarchal relationship with several other records:

* Ticket
	* Group
	* Latest Message
	* Owner
        
Some of the children of a parent ticket record also have their own children::

* Ticket
	* Group
		* Bucket
	* Latest Message
		* Sender
			* Organization
	* Owner
		* Email Address

Generally, parent/child relationships are modeled using *nested* data structures like objects or arrays.

The above model could be represented in JSON like:

<pre>
<code class="language-json">
{
    ticket: {
        id: 123,
        subject: "Do you offer volume discounts?",
        group: {
            id: 2,
            name: "Support",
            bucket: {
                id: 0,
                name: "Inbox"
            }
        },
        latest_message: {
            id: 2,
            content: "...",
            sender: {
                id: 5
                name: "William Portcullis",
                email: "customer@example.com",
                organization: {
                    id: 6,
                    name: "Macrotough"
                }
            },
        },
        owner: {
            id: 3,
            name: "Steven Métier",
            email: "worker@example.com"
        }
    }
}</code>
</pre>

These relationship hierarchies can become quite complex.  You can imagine how difficult it would be to use this model in a feature like snippets or [bots](/docs/bots/).

To iterate through all the key/value pairs, you would need to use recursion[^recursion].

The keys are also not globally unique within the model (e.g. `id`, `name`).

Additionally, the method of accessing a child can be inconsistent depending on whether it is a primitive like a string, integer, or float; an array (`[...]`), or an object (`{...}`).

The above complexity can be reduced considerably by modeling the hierarchal relationships in a single-level dictionary.  Since all key names would need to be unique (because two keys with the same name can't exist at the same level), keys from different records could be logically partitioned using namespaces.  Every value can be represented using simple data types like strings; and data type hints can be given for more complex values.

The nested model in the previous example could be represented as the following single-level dictionary:

<pre>
<code class="language-json">
{
    ticket_id: 123,
    ticket_subject: "Do you offer volume discounts?",
    ticket_group_id: 2,
    ticket_group_name: "Support",
    ticket_bucket_id: 0,
    ticket_bucket_name: "Inbox",
    ticket_latest_message_id: 2,
    ticket_latest_message_content: "...",
    ticket_latest_message_sender_id: 5,
    ticket_latest_message_sender_name: "William Portcullis",
    ticket_latest_message_sender_email: "customer@example.com",
    ticket_latest_message_sender_org_id: 6,
    ticket_latest_message_sender_org_name: "Macrotough",
    ticket_owner_id: 3,
    ticket_owner_name: "Steven Métier",
    ticket_owner_email: "worker@example.com"
}</code>
</pre>

All of the keys and values can now be iterated with a simple loop.  Keys have globally unique names.  Any key can be retrieved directly in a consistent way without recursion.  And we still have the ability to model hierarchal relationships at any depth.

# Contexts and key expansion

Now that we've demonstrated how Cerb's object dictionaries reduce complexity, let's look at how they improve performance.

The example above was simplified to demonstrate the basic concept of dictionaries.  In practice, there are many more records and keys involved, and it would be inefficient to always load that data if most of the time it doesn't end up being used.  In other words, if you just need the mask and subject from a ticket record, Cerb shouldn't waste time loading data for the associated group, bucket, latest message, sender, organization, owner, custom fields, etc.

In the response to our original `GET` request for ticket #123, you may have noticed the many keys like this:

<pre>
<code class="language-json">
{
    bucket__context: "cerberusweb.contexts.bucket",
    bucket_id: 6,

    group__context: "cerberusweb.contexts.group",
    group_id: 6,

    initial_message__context: "cerberusweb.contexts.message",
    initial_message_id: 1195,
    
    initial_message_sender__context: "cerberusweb.contexts.address",
    
    initial_message_sender_org__context: "cerberusweb.contexts.org",

    latest_message__context: "cerberusweb.contexts.message",
    latest_message_id: 1195,
    
    latest_message_sender__context: "cerberusweb.contexts.address",
    
    latest_message_sender_org__context: "cerberusweb.contexts.org",

    org__context: "cerberusweb.contexts.org",
    org_id: 51,

    owner__context: "cerberusweb.contexts.worker",
    owner_id: 0,
    
    owner_address__context: "cerberusweb.contexts.address",
}</code>
</pre>

These keys are placeholders for linked records that are not loaded by default.

When you request a key that needs those records, Cerb will automatically _lazy load_[^lazy-loading] them.  We call this process **key expansion**.  Even if you request a single key from one of these records, the dictionary will expand all of the related keys and values.

For instance, let's assume you wanted the name of the group that the ticket is assigned to.  Here's the placeholder for that record:

<pre>
<code class="language-json">
group__context: "cerberusweb.contexts.group",
group_id: 6,
</code>
</pre>

When you request a key that doesn't exist in the dictionary, like `group_name`, Cerb builds a list of all the `*__context` keys it does know about.  It then attempts to match those patterns against the requested key, using the longest patterns first.

In this case, the following key pattern would match:

<pre>
<code class="language-json">
group__context: "cerberusweb.contexts.group"
</code>
</pre>

Once a context is found for a key, Cerb looks for an associated `*_id` in the dictionary with the same prefix.  In this example, it looks for `group_id`, which does exist in the dictionary with a value of `6`.  Cerb would then *expand* (load) the keys and values from group #6:

<pre>
<code class="language-json">
group_name: "Billing"
</code>
</pre>

You may notice that some deeply nested contexts don't have corresponding IDs in the dictionary.  For instance:

<pre>
<code class="language-json">
latest_message_sender_org__context: "cerberusweb.contexts.org"
</code>
</pre>

To find a key like `latest_message_sender_org_name`, Cerb would build the following list of contexts using the dictionary:

<pre>
<code class="language-text">
latest_message_sender_org__context
latest_message_sender__context
latest_message__context
__context
</code>
</pre>

There aren't keys for `latest_message_sender_org_id` or `latest_message_sender_id` because their parent records haven't been expanded yet.  However, the following key does exist:

<pre>
<code class="language-json">
latest_message_id: 1195
</code>
</pre>

At this point, Cerb will expand the keys for message #1195, which provides the `latest_message_sender_id` key, and once that record's keys are expanded then the key for `latest_message_sender_org_id` is also available.  The value of `latest_message_sender_org_name` would then be returned.

## Expanding keys in API requests

Up to this point, we've treated the process of *key expansion* as an abstract concept.  You may have realized that the initial `GET` request would have already returned the JSON from the API, so accessing undefined keys from the dictionary would just return `null` values in an external program.

Without an introduction to key expansion, many programmers assume that the `__context` and `_id` keys are used for subsequent API requests to load additional information.  That would work, but it would be very inefficient to issue a dozen HTTP requests just to construct the full dictionary of a single ticket.  When performing a search that returns 100 tickets at a time, all those incremental round-trips to load additional data would create a lot of unnecessary overhead.

Instead, you can request that multiple keys be expanded when you make the original request.

Let's take another look at our original `GET` request:

<pre>
<code class="language-http">
GET /rest/tickets/123.json
</code>
</pre>

If we wanted the `group_name` and `latest_message_sender_org_name` keys to be available in the response, we'd add the following option to the request:

<pre>
<code class="language-http">
GET /rest/tickets/123.json?expand=group_name,latest_message_sender_org_name
</code>
</pre>

Remember, this would also load any other related key/value pairs from the group and organization records.  In fact, the following shortcut also works:

<pre>
<code class="language-http">
GET /rest/tickets/123.json?expand=group_,latest_message_sender_org_
</code>
</pre>

In the above request, we're requesting the expansion of the keys for the ticket's group and the latest message sender's organization by specifying only their key prefix.  This will also load the latest message and the latest message's sender, because they're both hierarchal parents of the organization's record.

# Meta data

Now that you understand how key expansion works, you may be wondering how to figure out what keys are available for a given request.

By default, most responses include special **meta data** keys, which provide a list of the labels and data types for all of the available keys in the dictionary.  You'll find these in the `_labels` and `_types` keys of a typical single dictionary response, and in the `results_meta` section of a multiple-dictionary response like search results.

The `show_meta` option in a request URL determines whether this information is provided or not.  The option is disabled by default to save bandwidth and CPU cycles for subsequent requests. You can enable it by setting it to `1`.

The labels meta data is also useful for understanding what is stored in a particular key.  In most cases the key names are intuitive (e.g. `ticket_latest_message_sender_first_name`), but custom fields are particularly cryptic.  For example, the meta data could tell you that the key `custom_123` is a *date* custom field, with the label "Due date".  With this information, you could use the key's value appropriately.

# Data types

See: [Custom field types](/docs/api/topics/requests/#data-types)

{% include api_toc.html %}

# References

[^lazy-loading]: <http://en.wikipedia.org/wiki/Lazy_loading>
[^recursion]: <http://en.wikipedia.org/wiki/Recursion_(computer_science)>