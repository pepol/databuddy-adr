---
created: 2022-04-04T09:53:23+02:00
modified: 2022-04-04T09:58:22+02:00
---

# ADR-0004 DataBuddy default bucket

DataBuddy default bucket name is stored in system bucket configuration (`_system` bucket, `defaults:bucket` key).

The default bucket name is settable on database initialization and is not modifiable afterwards.

Default bucket is accessible to all users and not deletable.
