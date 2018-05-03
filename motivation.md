# Motivation

At CareerBuilder, we have a presence in almost every major country, each with immense content needs. We want to build rich, informative experiences for both job seekers and employers, recommend relevant content, and report on it so we can better serve our users and author more successful content in the future. We're also constantly adapting to changing business needs, spinning up new test vehicles for content as these use cases arise. In the past, we've typically used either WordPress or Drupal to build these experiences, but have found that the lack of a unified content strategy and platform has held us back.

## Why not the tried-and-true WordPress?

The management overhead of WordPress is minimal, but lacks distribution flexibility - we can't author content in one central location and distribute it to multiple location-specific websites. Instead, we have to have 20 different IT teams manage 20 different installations and accounts, or email 20 different people just to push out content from the top of the organization - for example, a company-wide sale, a new product initiative, and so on.

## Alright, but isn't Drupal really flexible?

Drupal has more advanced distribution tools - you can build a 'multitenant' site for many locales. Speed, relevancy, extensibility, and advanced distribution are major issues, however. Out of the box, Drupal lacks a search database like ElasticSearch or Solr, which limits both speed and relevancy, especially in more advanced use cases. Drupal's plugin and frontend/templating architecture tends to be very complicated, and PHP is no longer as commonplace among engineers - especially at CareerBuilder. Additionally, Drupal is not headless, which makes consuming content in non-traditional media, such as an ad network, a 3rd party property, a car, etc much more difficult - or impossible!

## Fine, you got me - but didn't you forget all the Custom Content CMSs?

We love the concepts of various API-centric [Custom Content CMSs](glossary.md#custom-content-cms), which solve many of the aforementioned issues, but we have been hard-pressed to find one that's open source, is Ruby-based, and supports all the various features we found necessary, such as:

* Content from the top-down. We want to push down content from the lead content/marketing teams down to our field offices.
* Content from the bottom-up. If a field office creates a great piece of content, it should be shareable across tenants and up the chain to any tenant that would like to consume or localize it. This is similar to how public radio \(and radio in general\) [syndicates](https://en.wikipedia.org/wiki/Broadcast_syndication#Radio_syndication) and shares content.
* Responsive, bespoke content creation interfaces \([Wizards](basics/designing-wizards.md)\). Custom Content CMSs typically don't have great [content creator](glossary.md#content-creator) experiences, as they've sacrificed good UI/UX for a better engineer/superadministrator experience.
* A search engine, which provides:
  * Advanced relevancy. CareerBuilder provides content recommendations based on Job Title/Occupancy codes, which tie in with internal data science APIs that further enrich these recommendations. Integrating all these needs with other CMSs would prove difficult. Cortex CMS allows engineers to to arbitrarily [extend the search engine](advanced/developing-plugins/extending-search.md) via plugins.
  * Speed! For advanced queries, which are very common, normal databases just can't stack up to Lucene-based search engines.
* `FieldTypes` built as React components
* Drag-and-drop website/landing page builder and manager
* Lots more!

_**Thus, Cortex CMS is born!**_

