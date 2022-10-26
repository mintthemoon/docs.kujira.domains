# Resolving addresses

## Forward lookups
### Description
Use a forward lookup to get the Kujira address associated with a domain.

### Response
The query will fail if no record exists for the name. Not all records are Kujira addresses
so you should validate the response `kind` is `KujiraAddr` before using it as an address.

```json
{"name": "mintthemoon.kuji", "kind": "KujiraAddr", "data": "kujira..."}
```

### Example: CLI
Replace `<registry_addr>` with the KNS Registry contract address and `mintthemoon.kuji`
with the Kujira address you want to resolve.

```bash
kujirad query wasm state smart <registry_addr> \
    '{"record": {"name": "mintthemoon.kuji"}'
```

## Reverse lookups
### Description
Use a reverse lookup to get the domain associated with a Kujira address.

### Response
The query will fail if no reverse record exists for the domain.

```json
{"name": "mintthemoon.kuji"}
```

### Example: CLI
Replace `<registry_addr>` with the KNS Registry contract address and `kujira...`
with the Kujira address you want to resolve.

```bash
kujirad query wasm state smart <registry_addr> \
    '{"kujira_addr": {"addr": "kujira..."}'
```