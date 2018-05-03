# Data Validation

> Note: These are very old instructions, and need to be updated with clearer language, recent changes, and more detail

Each FieldType defines the validations that can be run on a FieldItem's data. It should have a hash where the keys are the different types of validations that can be run, and the values are method names that will be called to determine if the requested Field validation is legitimate:

```text
VALIDATION_TYPES = {
  length: :valid_length_validation?,
  presence: :valid_presence_validation?
}.freeze
```

In order to define the validations that can be run, we use the [validators defined by Rails](https://github.com/rails/rails/tree/master/activemodel/lib/active_model/validations). You can also write [custom validators](http://guides.rubyonrails.org/active_record_validations.html#custom-validators) that would be used in the same way. This makes it easy to adhere to the same syntax used with ActiveRecord validations. When creating a Field, first it checks to ensure that the requested validations are consistent with the validations its FieldType provides, e.g. if a TextFieldType supports presence and length validations, you will not be able to add a numericality validation. Then the FieldType tests to see that any requested Field validations are allowed by instantiating the associated Validator and catching any ArgumentError or NoMethodError that gets thrown. If an error is thrown, then the syntax or content of the Field validation is incorrect somehow. If there is no error, then the Field validation is allowed.

The Field validations themselves are run when creating a ContentItem and its associated FieldItems. A ContentItem is only considered valid if all of its FieldItems are valid. To determine validity, the FieldItem instantiates the FieldType, passes in its data, and tells the FieldType to run the validations hash specified by the Field.

```text
class TextFieldType
  def text_length
    validator = LengthValidator.new(validations[:length].merge(attributes: [:text]))
    validator.validate_each(self, :text, text)
  end
end
```

