# Names and addresses

## Kujira address lookups
### Description
Use this query instead of the more generic name lookup if you know you're resolving a Kujira address.

### Response
This query will fail if no reverse record exists for the address.

```json
{"name": "mintthemoon.kuji"}
```

### Examples: CLI
```bash
kujirad query wasm state smart <registry_addr> \
    '{"kujira_addr": {"addr": "kujira..."}'
```

## Name lookups
### Description
Use a name lookup to get the name associated with an address. In addition to a Kujira
address, you can use any interchain address with a [compatible derivation path](https://medium.com/chainapsis/keplr-explained-coin-type-118-9781d26b2c4e)
and it will resolve if a reverse record exists for the equivalent Kujira address.

### Response
The query will fail if no reverse record exists for the address.

```json
{"name": "mintthemoon.kuji"}
```

### Examples: CLI
```bash
kujirad query wasm state smart <registry_addr> \
    '{"name": {"addr": "kujira..."}'
```

```bash
kujirad query wasm state smart <registry_addr> \
    '{"name": {"addr": "osmo..."}'
```

## Address lookups
### Description
Use an address lookup to get the address associated with a domain. By default
this will return a Kujira address, but you can pass the `prefix` parameter to
resolve any interchain address with a [compatible derivation path](https://medium.com/chainapsis/keplr-explained-coin-type-118-9781d26b2c4e).

### Response
The query will fail if no record exists for the domain or if the record kind is not `KujiraAddr`.

```json
{"addr": "kujira..."}
```

```json
{"addr": "osmo..."}
```

### Examples: CLI
```bash
kujirad query wasm state smart <registry_addr> \
    '{"addr": {"addr": "kujira..."}'
```

```bash
kujirad query wasm state smart <registry_addr> \
    '{"addr": {"addr": "kujira...", "prefix": "osmo"}'
```