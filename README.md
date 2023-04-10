# RFC 7807 Error Response Example

This repository contains example files for an error response object that aligns with [RFC 7807](https://www.rfc-editor.org/rfc/rfc7807), also known as "Problem Details for HTTP APIs."

Ensure that API error responses follow this format to provide consistent and informative error messages to clients.

The error object may be extended with custom properties as needed, as long as they do not conflict with the properties defined in RFC 7807.

## Files

- [error_response_example.json](error_response_example.json): An example error message (JSON) aligned to the RFC 7807 error response object
- [error_response_schema.json](error_response_schema.json): A JSON schema defining the structure of the RFC 7807 error response object.
- [error_response_openapi.yaml](error_response_openapi.yaml): An OpenAPI schema definition for the RFC 7807 error response object, which can be used within the `components` section of an OpenAPI specification.

## Usage

### OpenAPI Schema Definition

The `error_response_openapi.yaml` file contains an OpenAPI schema definition that can be integrated into an existing OpenAPI specification. Include the `ErrorResponse` schema under the `components` section of your OpenAPI document to reference it in your API responses.

For example, you can reference the `ErrorResponse` schema in an API endpoint like this:

```yaml
paths:
  /example:
    get:
      responses:
        '200':
          description: Successful operation
        '400':
          description: Bad Request
          content:
            application/problem+json:
              schema:
                $ref: '#/components/schemas/ErrorResponse'
```
