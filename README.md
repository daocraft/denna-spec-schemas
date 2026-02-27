# Denna Spec Schemas

Official schema library for the [Denna Specification](https://spec.denna.io), maintained by [Denna Labs](https://denna.io).

These schemas are building blocks. Use them as-is for standard use cases, extend them for protocol-specific needs, or use them as reference when writing your own schemas from scratch.

All schemas are hosted at `https://schemas.denna.io/` and use the `io.denna.*` kind namespace.

## Available Schemas

### DeFi (`io.denna.defi.*`)

| Schema | Kind | Path |
|--------|------|------|
| Star Configuration | `io.denna.defi.star-config` | `schemas/v1/defi/star-config.schema.json` |
| Rates & Parameters | `io.denna.defi.rates` | `schemas/v1/defi/rates.schema.json` |
| Address Registry | `io.denna.defi.address-registry` | `schemas/v1/defi/address-registry.schema.json` |

### Governance (`io.denna.governance.*`)

| Schema | Kind | Path |
|--------|------|------|
| Governance Document | `io.denna.governance.document` | `schemas/v1/governance/document.schema.json` |

## Usage

Reference schemas in your `.denna-spec.json` files:

```json
{
  "$schema": "https://schemas.denna.io/v1/defi/star-config.schema.json",
  "metadata": {
    "id": "my-protocol-config",
    "name": "My Protocol",
    "kind": "io.denna.defi.star-config"
  },
  "chains": [...]
}
```

Or reference them locally (copy to your `schemas/` directory):

```json
{
  "$schema": "../schemas/star-config.schema.json"
}
```

## Extending Official Schemas

You can extend any official schema by creating your own JSON Schema that adds additional `properties` or `required` fields:

```json
{
  "$schema": "https://json-schema.org/draft/2020-12/schema",
  "$id": "io.sky.star.config",
  "allOf": [
    { "$ref": "https://schemas.denna.io/v1/defi/star-config.schema.json" }
  ],
  "properties": {
    "parameters": {
      "properties": {
        "borrowRateSubsidyEligible": { "type": "boolean" }
      }
    }
  }
}
```

## Type Definitions

All schemas import shared type definitions from the Denna Spec core:

```
https://spec.denna.io/schemas/v1/denna-types.schema.json
```

Available types: `address`, `rate`, `amount`, `duration`, `date`, `chain`, `metadata`.

## Versioning

Schemas are versioned at stable paths (`schemas/v1/`, `schemas/v2/`). A MAJOR version increment indicates breaking changes. Older versions remain available.

## Contributing

This is an open-source repository. To propose a new schema or changes to an existing one, open a pull request with:
1. The schema file
2. At least one example `.denna-spec.json` file that validates against it
3. A description of the use case

## License

Creative Commons — CC BY 4.0
