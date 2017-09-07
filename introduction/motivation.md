# Motivation

At CareerBuilder, we have a presence in almost every major country, each with immense content needs. We want to build rich, informative experiences for both job seekers and employers, recommend relevant content, and report on it so we can better serve our users and author more successful content in the future. In the past, we've typically used either WordPress or Drupal to build these experiences.

The management overhead of WordPress is minimal, but lacks distribution flexibility - we can't author content in one central location and distribute it to multiple location-specific websites. Instead, we have to have 20 different IT teams manage 20 different installations and accounts, or email 20 different people just to push out content from the top of the organization - for example, a company-wide sale, a new product initiative, and so on.

Drupal, on the other hand, has more advanced distribution tools - you can build a 'multitenant' site for many locales. Speed, relevancy, extensibility, and advanced distribution are major issues, however. Out of the box, Drupal lacks a search database like ElasticSearch or Solr, which limits both speed and relevancy, especially in more advanced use cases. Drupal's plugin and frontend/templating architecture tends to be very complicated, and PHP is no longer as commonplace among engineers - especially at CareerBuilder. Additionally, Drupal is not headless, which makes consuming content in non-traditional media, such as an ad network, a 3rd party property, a car, etc much more difficult - or impossible!

We love the concepts of various API-centric [Custom Content CMSs](/glossary.md#custom-content-cms), which solve many of the aforementioned issues, but we have been hard-pressed to find one that's open source, is Ruby-based, and supports all the various features we found necessary, such as:

* Content from the top-down
* Content from the bottom-up
* Responsive, bespoke content creation interfaces \([Wizards](/basics/designing-wizards.md)\)
* Search database backend, which provides:
  * Advanced relevancy
  * Speed



