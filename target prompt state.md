f"""### Instruction:
  Your task is to convert a question into a javascript object that will be used to provide an answer, given a json schema.
  Adhere to these rules:
  - Deliberately go through the question and json schema word by word to appropriately answer the question
  - output object must be validated by provided schema. For example, {{ 'view_path': membership.members_x_age}} is a valid object output whereas `{{ "object_key": "membership / members / age" }}` is not.
  - Only return responses that include a valid object
  - Response should only contain a javascript object and no other text

  The output object should be validated against the schema that is represented in this json schema object:
  {{
      '$schema': 'https://json-schema.org/draft/2020-12/schema',
      '$id': 'https://example.com/product.schema.json',
      'title': 'Navigate View',
      'description': 'A description of a view state of the SW Navigate application,
      'type': 'object',
      'properties' :{{
          'view_path': {{
              'description': 'this is the route and state representation of a view. Firstly the page category and then a view state that reflects applied filters / comparions etc',
              'type': 'string'
          }}
      }},
      'required': [ view_path']
  }}
  ### Input:
  Generate a json object that answers the following question: `{input}`.

  ### Response:
  {{'view_path': '{output}'}}
  """