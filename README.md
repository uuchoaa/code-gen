## Endpoint Configuration YAML Specification

### Purpose

This YAML specification defines a structured format to describe API endpoints, including their paths, request examples, and response examples. It's intended to be a simple way to document APIs for developers and users.

### Structure

The main structure of the configuration consists of a list of `endpoints`.

### Fields

#### endpoints

A list of endpoint objects.

##### path

A dictionary where the key is an HTTP method (`get`, `post`, etc.) and the value is the corresponding URI path.

- Example: `post /user_sessions`

##### request_example (optional)

A dictionary or a list of dictionaries providing sample request payloads for the given endpoint.

- Example: `email: 'user@email.com'`

##### response_example

A dictionary or a list of dictionaries providing sample response payloads for the given endpoint. The keys can be HTTP status codes (e.g., `200`, `404`) or any other relevant designation.

- Example:
  ```yaml
  201:
    name: 'Mailing teste'
    file_url: 'https://path.to/spreadsheet'
  ```

### Examples

1. A `post` endpoint with request and response examples:

   ```yaml
   - path:
       post /user_sessions
     request_example:
       email: 'user@email.com'
     response_example:
       - id: '123123'
         email: 'user@email.com'
         auth_strategies: ['password']
   ```

2. A `get` endpoint with only a response example:

   ```yaml
   - path:
       get /videobots 
     response_example:
       - name: 'Porto Oferta'
         description: 'Video oferta da Porto RH'
         thumbnail_url: 'https://path.to/image'
   ```

3. An endpoint where the response examples include HTTP status codes:

   ```yaml
   - path:
       post /discovery/slug 
     request_example: 
       slug: 'xptoz'
     response_example: 
       - 200:
           manifest: {}
           ovmConfig: {}
       - 404:
           error: 'not found'
   ```

### Conventions

1. For clarity and consistency, each `path` should specify only one HTTP method and corresponding URI.
2. If an endpoint can return multiple types of responses, use a list of dictionaries for the `response_example`, with potential HTTP status codes as the keys.
3. Always use the full HTTP method names in lowercase (e.g., `get`, `post`, `put`, `delete`).

---

This is a general overview of the structure. Depending on the specific use case or platform, additional details might be required. Always tailor specifications to the requirements and preferences of your audience.
