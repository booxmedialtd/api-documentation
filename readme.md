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

Note that value objects (which can be inserted into entities) are explicitly named in the file, for example consider how Image and Content Rating is included
in the Program Entity:

```yaml
    ProgramEntity:
      type: object
      required:
      - id
      - program_type
      - long_title
      - grid_title
      - duration_seconds
      - release_year
      - spoken_iso2_language
      - subtitle_iso2_language
      - created_at
      - modified_at
      properties:
        id:
          type: string
          example: "d0de0088-3141-439e-8455-839bdb8f6cec"
        program_type:
          type: string
          example: "trailer"
          description: "One of trailer|movie|progam|episode"
        duration_seconds:
          type: integer
          example: 5400
        release_year:
          type: integer
          example: 1984
        images:
          type: array
          items:
            $ref: "https://raw.githubusercontent.com/booxmedialtd/api-documentation/master/snippets/EnrichedMetadata/ImageValueObject.yml#ImageValueObject"
        content_flags:
          type: array
          items:
            $ref: "https://raw.githubusercontent.com/booxmedialtd/api-documentation/master/snippets/EnrichedMetadata/ContentFlagValueObject.yml#ContentFlagValueObject"
``` 
