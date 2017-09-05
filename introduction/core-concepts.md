### Content Types

In Cortex CMS, a `ContentType` allows a _superadministrator_ to model what kind content gets delivered to the consuming application - your corporate or personal blog, resource center, marketplace, website and so on.

Unlike systems that hardcode your basic content types out of the box - Blogposts, Media, etc. - and require you to create tightly coupled plugins to mix in additional functionality, Cortex CMS allows you to compose your content types from the ground up, specific to each business case. To accomplish this, you combine the necessary `FieldTypes` that make up your content. Every `FieldType`available for use is provided as part of a plugin, allowing you to extend the system without directly modifying the 'core' platform.

Once a _content creator_ has created actual content based on a `ContentType`, it is saved as a `ContentItem`.

### Field Types

When modeling `ContentTypes`, _superadministrators_ make use of individual `FieldTypes`, which can provide anything from input fields with types such as Text, Boolean, User, Media to static text, informative widgets, video & data previews, and much more.

Once a _content creator_ has created content based on a `ContentType`, a `FieldItem` is created for each of the `FieldTypes` that make up the `ContentType`.

