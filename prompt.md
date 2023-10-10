You are a software development code assitant. You answer only code.
Based on my input yaml, create a OpenAPI yaml. Infer as many open api attributes as possible based on my input. My input will be the necessary to you infer the other things missing. Please fill it. Don't forget "tags" attribute. Don't forget to define the schemas.

I'll provide an example to help you:

Input example 1:
```yaml
endpoints:
  - path:
      post /user_sessions
    request_example:
      email: 'user@email.com'
    response_example:
      - id: '123123'
        email: 'user@email.com'
        auth_strategies: ['password']
      - id: '123123'
        email: 'user@email.com'
        auth_strategies: ['password', 'two_factor']
    description: Creates a user session and returns the user authentication strategies available

```

Output example 1:
```yaml
openapi: '3.0.0'
info:
  version: '1.0.0'
  title: 'User Sessions API'
servers:
  - url: 'http://api.example.com' # Replace with your actual server URL
paths:
  /user_sessions:
    post:
      tags:
        - 'User Sessions'
      summary: 'Create a user session'
      description: 'Creates a user session and returns the user authentication strategies available'
      requestBody:
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/UserSessionRequest'
      responses:
        '200':
          description: 'Successfully created user session'
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/UserSessionResponse'
components:
  schemas:
    UserSessionRequest:
      type: 'object'
      properties:
        email:
          type: 'string'
          format: 'email'
    UserSessionResponse:
      type: 'object'
      properties:
        id:
          type: 'string'
        email:
          type: 'string'
          format: 'email'
        auth_strategies:
          type: 'array'
          items:
            type: 'string'
tags:
  - name: 'User Sessions'
    description: 'Operations related to user sessions'

```
Input example 2:
```yaml
  - path:
      get /posts
    response_example:
      title: 'hello world'
      content: 'hi there, welcome to my blog. this is my first post!'
```

Output example 2:
```yaml
openapi: '3.0.0'
info:
  version: '1.0.0'
  title: 'User Sessions API'
servers:
  - url: 'http://api.example.com' # Replace with your actual server URL
paths:
  /user_sessions:
    post:
      tags:
        - 'User Sessions'
      summary: 'Create a user session'
      description: 'Creates a user session and returns the user authentication strategies available'
      requestBody:
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/UserSessionRequest'
      responses:
        '200':
          description: 'Successfully created user session'
          content:
            application/json:
              schema:
                $ref: '#/components/schemas/UserSessionResponse'
components:
  schemas:
    UserSessionRequest:
      type: 'object'
      properties:
        email:
          type: 'string'
          format: 'email'
    UserSessionResponse:
      type: 'object'
      properties:
        id:
          type: 'string'
        email:
          type: 'string'
          format: 'email'
        auth_strategies:
          type: 'array'
          items:
            type: 'string'
tags:
  - name: 'User Sessions'
    description: 'Operations related to user sessions'

```

Don't explain your answers, just give me the OpenAPI yaml. Don't confirm the operation, just give me the OpenAPI yaml.

My input is:
```yaml
endpoints:
  - path:
      get /videobots/{id}/mailings
    response_example:
      - name: 'Mailing teste'
        file_url: 'https://path.to/spreadsheet'

  - path:
      post /videobots/{id}/mailings
    request_example:
      name: 'Mailing teste'
      file_url: 'https://path.to/spreadsheet'
    response_example: 
      201:
        name: 'Mailing teste'
        file_url: 'https://path.to/spreadsheet'

```
