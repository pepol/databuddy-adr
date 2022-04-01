---
created: 2022-04-01T23:13:31+02:00
modified: 2022-04-01T23:25:06+02:00
---

# ADR-0003 DataBuddy Key-Value Operations

DataBuddy exposes redis-compatible API over the RESP.

Following commands are available:

`CREATE <bucket>`
- create bucket with given name
  - default ACLs for new buckets are specified in system configuration as either `private` (only creator has access) or `public` (everybody has all access)
- return OK, with optional note if bucket exists
- return ERR if creation failed for reason other than "already exists"

`USE <bucket>`
- use given bucket for further commands
- return OK
- return ERR if bucket doesn't exist

`GET <key>`
- return value stored at given key
- return ERR if key doesn't exist

`SET <key> <value>`
- store value at given key
- return OK
- return ERR if error occured

`DEL <key1> [<key2> ...]`
- delete values stored at given key(s)
- return count of deleted items

`KEYS [<pattern1> ...]`
- list keys matching given pattern(s), or all if no pattern is provided
- return array of found keys (array of strings)
