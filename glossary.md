# Glossary

## CMS

At its core, a Content Management System allows for the creation & distribution of content across media devices. With more advanced tools, such as Cortex CMS, a CMS can also provide dynamic content recommendations to end-users, an API for [integration engineers](glossary.md#integration-engineer) to work with when consuming content, reporting, localizations, advanced distribution rules and much more.

## Custom Content CMS

'Custom Content' implies a more flexible CMS architecture. Rather than hardcoding available 'content types' \(such as a Blogpost, Webpage, Landing Page, Media, etc\), Cortex CMS and others of its ilk allow [superadministrators](glossary.md#superadministrator) to easily spin up new content types \(and modify them\) on a whim, as new business cases arise or change. This allows companies to meet the evolving needs of their users, while still providing rich, relevant & tracked experiences.

## Content Creator

The primary customer a CMS serves is the content creator, who authors the rich content experiences necessary for end-users to be delighted by the product, whether it be a blog, a website, or something more - a smartphone app, an advertising platform, or even a car's dashboard.

## Superadministrator

The glue putting together all the pieces across the CMS - this user creates or manages the various `ContentTypes`, plugins, tenants and users available to every other role.

## Integration Engineer

This developer creates and configures the connection between Cortex CMS and the desired frontend application. They can do this via the Cortex CMS API \(recommended\) or RSS feed by following the consuming [content instructions](basics/consuming-content.md) & utilizing the [Cortex Client](basics/consuming-content.md#api-client-libraries). A frontend application may be a simple blog, resource center, phone app, embeded device, appliance, and so much more!

## ContentType

A collection of `Fields` which represents a category of content that you want on your site

## Field

The association between a `ContentType` and a `FieldType`. When saving as a `FieldItem`, it informs the `ContentType` which `FieldType` to use, the validations to run on the content, and provides any relevant metadata to plugins, widgets, decorators, etc.

## FieldType

Describes the characteristics of some piece of data that can be used to compose a `ContentType`. For example, if a `ContentType` needs a string of text, you might utilize a `TextFieldType`, while a PDF might require a `FileFieldType`, and so on.

## ContentItem

An instance of a `ContentType`, a `ConteItem` is a grouping of `FieldItems` with [content creator](glossary.md#content-creator)-provided data that is then persisted to the database and search engine.

## FieldItem

Each `FieldItem` represents a component of the `ContentItem` to which it belongs. So if the `ContentItem` is a blog post, there would be a `FieldItem` for the title, another for the body, another for an associated image, etc. Each of these `FieldItems` has a single corresponding `FieldType` that describes what kind of content it represents, such as a `TextFieldType`, `BooleanFieldType`, etc

## Decorator

## Multitenancy

## Content Library

## Role

## Permission

## WYSIWYG

## WYSIWYG Widget

## Service Layer

## Elasticsearch

## Drafts

## Docker

## Automated Testing

