---
created: 2022-04-01T22:57:43+02:00
modified: 2022-04-01T23:13:28+02:00
---

# ADR-0002 DataBuddy Storage Concepts

DataBuddy uses several independent LSM trees for storage of data and metadata.

A bucket is a single independent BadherDB instance. It serves the same purpose as a table/schema in SQL databases.

Each database contains 1 user-accessible bucket upon creation named `default`.

Information pertaining to buckets is stored in a system bucket. Information stored includes the bucket name (part of key within system bucket), path to storage directory, ACLs, etc.

Each bucket can have an Access Control List defined. The ACL is a list of access grants. If none of the grants provides access to user in question, they are denied access.

Access grant is a pairing between a group of 1 or more users and an action allowed.

Actions allowed can be a combination of:
- read keys matching pattern
- read all keys (pattern `*`)
- write keys matching pattern
- write all keys (pattern `*`)
- delete keys matching pattern
- delete all keys (pattern `*`)

Only a single pattern per grant is allowed (either all, or limit), with all actions in the grant taking it into account. Thateans that to allow a user to read all and write only to a subset of keys, 2 grants need to be created.

User list in access grant can be defined either explicitly by listing all user, and/or implicitly by specifying a user group definition. User group membership is resolved at the time of rule validation, not creation.

User group information is stored in user information bucket for each user (to get all users of a group, mapreduce/filter over all users has to be performed). This is done as the group membership is used primarily for ACLs, so checks need to be fast for specific user's access to resource.
