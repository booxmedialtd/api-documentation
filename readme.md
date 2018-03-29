# api-documentation

## Directory structure of this project

Files in "endpoints" contain fully functional Swagger markup that can be displayed to show endpoint documentation.

Files in "snippets" refer to Entities and must contain JUST the attributes of the entity so that they can be included in the endpoint files like so:

```yaml
    responses:
      200:
        description: "Successful response"
        schema:
          type: "object"
          required:
          - data
          properties:
            data:
              type: array
              items:
                type: object
                required:
                - type
                - id
                properties:
                  type:
                    type: string
                    example: Episode
                  id:
                    type: string
                    description: "The id of the entity being referenced"
                    example: "3173335a-810b-4b53-b009-122a169f9920"
                  attributes:
                    $ref: "https://raw.githubusercontent.com/booxmedialtd/api-documentation/master/snippets/EnrichedMetadata/EpisodeEntity.yml#EpisodeEntity"
```
