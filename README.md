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
mops:1:start first test
mops:1:end first test
mops:1:start second test
mops:1:end second test
mops:1:skip third test
```

formatted result
```
✓ first test
✓ second test
− third test
```
