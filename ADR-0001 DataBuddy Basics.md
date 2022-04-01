---
created: 2022-04-01T22:54:25+02:00
modified: 2022-04-01T22:57:40+02:00
---

# ADR-0001 DataBuddy Basics

DataBuddy is a distributed key-value store.

DataBuddy is written in Go, due to the simplicity of the language and availability of libraries implementing various structures and algorithms necessary.

DataBuddy uses Log-Structured Merge Trees to store both data and metadata.

DataBuddy uses BadgerDB as LSM tree implementation.
