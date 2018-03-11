---
title: Workspaces
permalink: /docs/workspaces/
jumbotron:
  title: Workspaces
  tagline: Stay on the same page while collaborating from anywhere
---

A **workspace** is a page designed to optimize a particular workflow.  Workspaces can be shared by everyone, shared within a [group](/docs/groups/) or role, or private to a specific [worker](/docs/workers/).

You can add any number of workspace pages to your [navigation bar](/docs/navigation/#pages) and personalize Cerb into your own mission control.

Workspaces use **tabs** to organize their content into sections; much like dividers are used to partition pages in a large binder. There are many kinds of tabs, but the two most common are worklists and dashboards.

* TOC
{:toc}

# Worklists

A **worklist** is a filterable, pageable, sortable, and customizable set of records displayed using rows and columns.  Each row of a worklist is a matching record and each column is a particular field from each record. The displayed columns can be customized on a worklist based on your particular need.

<div class="cerb-screenshot">
<img src="/assets/images/docs/using-cerb/workspaces/worklist.png" class="screenshot">
</div>

By saving a worklist in a workspace, you'll always have an up-to-date view of matching records without wasting any time searching.  For instance, a worklist can display new customer messages that need a response, client organizations in a specific industry, tasks that are overdue, etc.

### Filters

The most useful feature of worklists is their ability to pull out interesting sets of records from your data using **filters**.  A filter is simply some criterion that a record must satisfy in order to be included in the list.  Filters target a specific field, and often provide both an **operator** and **value**.  For text, common operators are "starts with" and "contains this phrase".  For numbers, you may want fields that are equal to a value, not equal, greater/less than, between, etc.

### Required Filters

The owner of a workspace can also add special **required filters** to a worklist that cannot be changed by other users of the worklist.  For instance, if a worklist is meant to only show open conversations from clients with a service level agreement, then no additional filtering can change that constraint.  Every other filter will act only against those matching records.

### Deep searching

Cerb also allows for **deep searching**, which means that you can filter a worklist based on the fields of records related to those that you're currently looking at, and then filter again based on fields related to those deeper records, and so on.

<div class="cerb-screenshot">
<img src="/assets/images/docs/using-cerb/workspaces/deep_search.png" class="screenshot">
</div>

For instance, you can build a worklist of email messages sent by organizations in the health care industry who have an enterprise SLA and also have at least one female contact whose name starts with the letter 'M'.  This is one of Cerb's distinguishing features.

### Sorting

In conjunction with filtering, **sorting** highlights the records of most interest by ordering a worklist by a particular field.  For example, you may be interested in the oldest messages in a list, or the opportunities with the highest potential value.

<div class="cerb-screenshot">
<img src="/assets/images/docs/using-cerb/workspaces/sorting.png" class="screenshot">
</div>

### Peek

When records are displayed in a worklist, you can open any of their cards for a quick **peek** without leaving the list.  Cards also summarize helpful information about a record, allow you to make modifications, etc.  In Cerb, you can accomplish a lot without ever leaving a worklist.

<div class="cerb-screenshot">
<img src="/assets/images/docs/using-cerb/workspaces/peek.png" class="screenshot">
</div>

### Pagination

When a worklist has many results, it's automatically divided into smaller chunks called **pages**. You can navigate through the pages using *next* and *previous* links.  You can also quickly jump to the first or last page.

<div class="cerb-screenshot">
<img src="/assets/images/docs/using-cerb/workspaces/paging.png" class="screenshot">
</div>

### Subtotals

Another useful feature in Cerb is the ability to **subtotal** worklists by grouping records with similar values for a given field.  Perhaps you want to subtotal organizations by country, email conversations by group, tasks by owner, etc.

<div class="cerb-screenshot">
<img src="/assets/images/docs/using-cerb/workspaces/subtotals.png" class="screenshot">
</div>

Once you've subtotaled a list, you can click on a particular category to automatically add a new filter to the worklist.

### Import/Export

Once you have a worklist filtered the way you want it, you can **export** data in CSV (comma-separated), JSON, or XML formats.  You also aren't limited to the fields displayed by the worklist; you can choose any fields, including those from related records.

Similarly, you can also **import** records on most worklists in CSV format.  You'll be given the opportunity to map columns in your import file to record fields.

### Bulk update

You can also perform actions on an entire worklist, on selected records, or on a random sample of matching records of any size.

For instance, when looking at a long list of indistinguishable leads that need a followup, you can bulk assign a random set of 25 records to yourself.  You can also use random samples to run A/B tests.

### Explore

When you need to view the profile page of each matching record in sequence, click the **explore** button below a worklist.  This will create a consistent snapshot of the worklist at the current point-in-time and allow you to navigate through it.  You can even send an explore set to another worker using its permalink.

You can use the `[` and `]` keyboard shortcuts to navigate backward and forward through the list, respectively.
