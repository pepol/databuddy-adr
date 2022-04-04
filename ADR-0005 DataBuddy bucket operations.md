---
created: 2022-04-04T09:59:29+02:00
modified: 2022-04-04T10:05:12+02:00
amends: ADR-0003
---

# ADR-0005 DataBuddy bucket operations

Following commands are used for bucket management:

`BUCKET`
- return currently used bucket name

`BUCKET COUNT`
- return count of all available buckets

`BUCKET LIST`
- return list of all available buckets (names only)
- replaces `BUCKETS [<pattern>]`

`BUCKET CREATE <bucket>`
- create bucket with given name
- replaces `CREATE <bucket>`

`BUCKET USE <bucket>`
- use given bucket for further commands
- replaces `USE <bucket>`
