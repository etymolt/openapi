# Etymolt OpenAPI

> The OpenAPI 3.1 specification for `api.etymolt.com`. The source of truth that drives every official Etymolt SDK.

[![License: CC-BY-4.0](https://img.shields.io/badge/license-CC--BY--4.0-blue.svg)](./LICENSE)

## What this repo is

The single, versioned source of truth for the Etymolt HTTP API. Every official SDK (`etymolt-node`, `etymolt-python`, `etymolt-go`) is generated from `openapi.yaml` in this repo. Implementers building custom clients against `api.etymolt.com` should target the schema published here.

This repo follows the [Stripe pattern](https://github.com/stripe/openapi) of separating the API contract from the implementation. The implementation is private; the contract is public.

## Layout

```
.
├── latest/
│   ├── openapi.yaml          # Current production API spec
│   └── openapi.json          # JSON form of the same spec
├── preview/
│   └── openapi.yaml          # Next-version preview spec (subject to change)
├── archive/
│   └── 2026-Q2/openapi.yaml  # Historical snapshots by quarter
└── README.md
```

## Versioning

The API itself follows date-based versioning at the endpoint level (`POST /v1/verify`). Spec updates that don't change the endpoint contract land in `latest/`; spec updates that propose breaking changes land in `preview/` for at least 4 weeks before promotion.

## Generating an SDK

Examples (TypeScript using `@hey-api/openapi-ts`, Python using `openapi-python-client`):

```bash
# TypeScript
npx @hey-api/openapi-ts \
  -i https://raw.githubusercontent.com/etymolt/openapi/main/latest/openapi.yaml \
  -o ./generated -c @hey-api/client-fetch

# Python
openapi-python-client generate \
  --url https://raw.githubusercontent.com/etymolt/openapi/main/latest/openapi.yaml
```

## EVP/1 connection

The response shape of `POST /v1/verify` is a conformant [EVP/1](https://github.com/etymolt/evp-spec) verdict. The OpenAPI spec here references the EVP/1 JSON Schema by URL.

## Contact

- General: `hello@etymolt.com`
- Security: `security@etymolt.com`

## License

[CC-BY-4.0](./LICENSE). The "Etymolt" name and logo are trademarks of Etymolt Inc. and are not licensed under CC-BY-4.0.

## Naming, attested.
