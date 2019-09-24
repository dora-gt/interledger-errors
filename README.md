# Interledger Errors

HTTP APIs return errors as the [RFC7807](https://tools.ietf.org/html/rfc7807) format.

## Type Structure
- The scheme and host
    - https://errors.interledger.org
- The top level path and meaning
    1. `ilp` (https://errors.interledger.org/ilp)
        - Refers to the Interledger Protocol layer errors.
        - e.g.
            - https://errors.interledger.org/ilp/F00
            - https://errors.interledger.org/ilp/T01
    1. `http-api` (https://errors.interledger.org/http-api)
        - Refers to the HTTP API layer errors.
        - e.g.
            - https://errors.interledger.org/http-api/json-syntax#trailing-comma
            - https://errors.interledger.org/http-api/spsp/invalid-receiver
### `ilp`
Not currently used, just reserved for the future. To be written.

### `http-api`

Note that we don't add `error` word because it is already underneath the `errors` subdomain. We use `-` instead of `_` for the word separator.

Paths are:
- `https://errors.interledger.org/http-api/{not API specific error identifier}#{sub-type identifier}`
    - e.g.
        - `https://errors.interledger.org/http-api/json-syntax#trailing-comma`
        - `https://errors.interledger.org/http-api/json-data#required-fields-not-provided`
- `https://errors.interledger.org/http-api/{RFC name or service name}/{error identifier}#{sub-type identifier}`
    - e.g.
        - `https://errors.interledger.org/http-api/spsp/invalid-receiver#xxx`
        - `https://errors.interledger.org/http-api/settlement-api/account-not-found`

#### Definitions
- `/http-api/unauthorized`
    - status: 401
    - title: xxx
- `/http-api/json-syntax`
    - status: 400
    - title: xxx
- `/http-api/json-data`
    - status: 400
    - title: xxx
    - sub-types
        - `#required-fields-not-provided`
- `/http-api/spsp/xxx`
