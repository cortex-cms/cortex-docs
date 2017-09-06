# Core Concepts

### Content Types

In Cortex CMS, a `ContentType` allows a [superadministrator](/glossary.md#superadministrator) to model what kind of content gets delivered to the consuming application - your corporate or personal blog, resource center, marketplace, website and so on.

Unlike systems that hardcode your basic content types out of the box - Blogposts, Media, etc. - and require you to create tightly coupled plugins to mix in additional functionality, Cortex CMS allows you to compose your content types from the ground up, specific to each business case. To accomplish this, you combine the necessary `FieldTypes` that make up your content. Every `FieldType`available for use is provided as part of a plugin, allowing you to extend the system without directly modifying the 'core' platform.

Once a [content creator](/glossary.md#content-creator) has created actual content based on a `ContentType`, it is saved as a `ContentItem`.

### Field Types

When modeling `ContentTypes`, [superadministrators](/glossary.md#superadministrator) make use of individual `FieldTypes`, which can provide anything from input fields with types such as Text, Boolean, User, Media to static text, informative widgets, video & data previews, and much more.

Once a [content creator](/glossary.md#content-creator) has created content based on a `ContentType`, a `FieldItem` is created for each of the `FieldTypes` that make up the `ContentType`.

### Decorators

[Content creators](/glossary.md#content-creator) expect a creation experience that properly utilizes screen real estate, is informative, and can be reconfigured based on new business needs and challenges. Unlike systems such as Drupal, which simply stack each `FieldType` added to a `ContentType` one after the other in a giant, vertical view, Cortex CMS allows [superadministrators](/glossary.md#superadministrator) to design the create/edit/index experience by way of `Decorators`. These are simple JSON objects that, based on their `Decorator` type, adhere to a documented schema.

There are currently two primary `Decorator` types \(though more can be added via plugins\): `Wizard` and `Index`. By setting the type to `Wizard` and adhering to its documented schema, a [superadministrator](/glossary.md#superadministrator) can set up a CRUD interface that that can drop `Fields` into a flexible, responsive grid, configure individual `FieldTypes` for display to the [content creator](/glossary.md#content-creator), toggle a WYSIWYG editor, apply CSS classes directly to the rendered `Field`, utilize the data from one `Field` in another `Field`, and so on.

### State, Workflow & Scheduling

TBD

### Headless

TBD

### Search

TBD

