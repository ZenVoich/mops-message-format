# Mops Message Format
Message format recognized by [Mops](https://github.com/ZenVoich/mops) when running tests with `mops test`

## v1.0
Stdout line must begin with one of the following labels:

`mops:1:start <name>` - test start

`mops:1:end <name>` - test end (test is considered passed)

`mops:1:skip <name>` - test skip

If the Motoko compiler fails, the last `mops:1:start` test is considered failed.

### Example
stdout
```
mops:1:start get file meta
mops:1:end get file meta
mops:1:start try to get file meta of unknown file
mops:1:end try to get file meta of unknown file
mops:1:skip upgrade storage canister
```

formatted result
```
✓ get file meta
✓ try to get file meta of unknown file
− upgrade storage canister
```

## V1.1
`mops:1:expected <text>` - expected value (line feed must be replaced with `\n`)

`mops:1:received <text>` - received value (line feed must be replaced with `\n`)