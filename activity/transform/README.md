# Transform
This activity provides your Flogo application the ability to run transformation on Json input strings using Kazaam transformations.

## Installation

```
flogo install github.com/mmussett/flogo-components/activity/transform
```

Link for flogo web:

```
https://github.com/mmussett/flogo-components/activity/transform
```


## Schema
Inputs and Outputs:

```json
{
  "inputs": [
    {
      "name": "input",
      "type": "any",
      "required": true
    },
    {
      "name": "spec",
      "type": "any",
      "required": true
    }
  ],
  "outputs": [
    {
      "name": "output",
      "type": "any"
    }
  ]
}

```

## Inputs
| Setting     | Required | Description    |
|:------------|:---------|:---------------|
| content     | True | Input JSON string to transform |
| spec | True | Kazaam transformation specification   |

## Outputs
| Setting     | Description    |
|:------------|:---------------|
| result | Transformed JSON string

## Configuration Example
```json
{
    "id": "transform_1",
    "name": "Transform",
    "description": "JSON transformation activity using Kazaam library.",
    "activity": {
        "ref": "github.com/mmussett/flogo-components/activity/transform",
        "input": {
            "content": null,
            "spec": "[{\"operation\": \"shift\", \"spec\": {\"Rating\": \"rating.primary.value\", \"example.old\": \"rating.example\"}}]"
        },
        "mappings": {
            "input": [
              {
                "type": "assign",
                "value": "$flow.input",
                "mapTo": "content"
              }
            ]
        }
    }
}
```

## About Kazaam transformation library

Kazaam library is used for the underlying transformation of arbitrary JSON. Similar to BazaarVoice JOLT, Kazaam uses a JSON specification to define the transformation.

Please refer to github documentation on supported specification:

https://github.com/qntfy/kazaam
