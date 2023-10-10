```json
{
    "$schema": "http://json-schema.org/draft-07/schema#",
    "type": "object",
    "properties": {
        "endpoints": {
            "type": "array",
            "items": {
                "type": "object",
                "properties": {
                    "path": {
                        "type": "object",
                        "propertyNames": {
                            "enum": ["get", "post", "put", "delete", "patch"]
                        },
                        "minProperties": 1,
                        "maxProperties": 1,
                        "additionalProperties": {
                            "type": "string"
                        }
                    },
                    "request_example": {
                        "oneOf": [
                            {
                                "type": "object",
                                "additionalProperties": true
                            },
                            {
                                "type": "array",
                                "items": {
                                    "type": "object",
                                    "additionalProperties": true
                                }
                            }
                        ]
                    },
                    "response_example": {
                        "oneOf": [
                            {
                                "type": "object",
                                "patternProperties": {
                                    "^[0-9]{3}$": {
                                        "type": "object",
                                        "additionalProperties": true
                                    }
                                },
                                "additionalProperties": false
                            },
                            {
                                "type": "array",
                                "items": {
                                    "type": "object",
                                    "patternProperties": {
                                        "^[0-9]{3}$": {
                                            "type": "object",
                                            "additionalProperties": true
                                        }
                                    },
                                    "additionalProperties": false
                                }
                            }
                        ]
                    }
                },
                "required": ["path", "response_example"],
                "additionalProperties": false
            }
        }
    },
    "required": ["endpoints"],
    "additionalProperties": false
}
```

Here's a brief rundown of this schema:

- It expects an object with an `endpoints` property.
- `endpoints` is an array where each item has `path` and `response_example`.
- `path` should be an object with one property (HTTP verb like `get`, `post`, etc.) and a string value representing the endpoint path.
- `request_example` can be an object or an array of objects.
- `response_example` can be an object with HTTP status codes (like `200`, `404`) as keys, or an array of such objects.

You can use this schema with JSON Schema validators to ensure that given YAML (converted to JSON) follows the described structure. Remember, this is a basic schema and can be further enhanced or refined as needed.
