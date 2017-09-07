# Building Content Types

> Note: These are very old instructions, and need to be updated with clearer language, recent changes, and more detail

Say you want to create a ContentType called AwesomeBlogPost that has 4 fields: a Title \(TextFieldType\), a Body \(TextFieldType\), a Video \(YoutubeFieldType\), and an Image \(ImageFileFieldType\).

Each FieldType has a number of validations that can potentially be run. You choose which validations to use when creating a Field using that FieldType. The Field will store the name you specify, the validations you choose to run, and the position of that Field relative to other Fields in the same ContentType.

So, in AwesomeBlogPost you would specify that the Field named "Title" is a TextFieldType which comes first, its presence is required, and it should be a maximum of 50 characters; the Field named "Body" is a TextFieldType which comes second and should have a maximum of 1000 characters; the Field named "Video" is a YoutubeFieldType which comes third; and the Field named "Image" is an ImageFileFieldType which comes last and must be a jpg under 1MB.

```
ct = ContentType.new(name: "AwesomeBlogPost", description: "The kind of blog post that goes on my Awesome Site", creator_id: 1)

ct.fields.new(name: "Title", field_type: "text_field_type", validations: { presence: true, length: { maximum: 50 } }, metadata: { placeholder: "This is the title" })
ct.fields.new(name: "Body", field_type: "text_field_type", validations: { length: {maximum: 1000 } })
ct.fields.new(name: "Video", field_type: "youtube_field_type" })
ct.fields.new(name: "Image", field_type: "image_file_field_type", validations: content_type: { content_type: "image/jpeg" }, size: { less_than: 1.megabyte })

ct.save
```



