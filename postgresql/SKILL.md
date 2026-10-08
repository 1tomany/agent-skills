---
name: postgresql
description: Use when an application uses PostgreSQL
license: MIT
---

# PostgreSQL Skill

## Overview

This skill outlines how to use PostgreSQL, table structure, and how to write migrations. It is important that a database is well designed, structured, and maintained. After a certain size, it is much easier to change code than it is to change a database.

## Table Structure

Tables should almost always use the following structure unless sufficient reason not to is provided:

- Identity primary key with type `bigint` and named `id`
- Metadata timestamps with types `timestamptz`
  - Non-null columns `created_at` and `updated_at` are required
  - Do not set default values for any timestamps
  - Any other metadata timestamp columns
- Foreign keys, roughly ordered by importance
- Entity date and timestamp columns
- Non-required entity metadata columns
- Required entity columns
- Error and metrics columns

### Metadata Timestamps

The columns `created_at` and `updated_at` must be placed immediately after the `id` column. These should be `NOT NULL` and should not have a default value.

### Foreign Keys

Foreign keys must be placed immediately after all metadata timestamp columns. They should be ordered by "importance" where importance is defined by how required the column is for a row in the table to exist. For example, in a multi-tenant application, the column that represents the tenant would come before a column that represents the user that created the record. Knowing what tenant the record belongs to is necessary for the row to exist, but knowing who created it isn't.

The `CASCADE` operation should be set for all foreign keys. If a foreign key is `NOT NULL`, the `CASCADE` operation should be `DELETE`.

### Entity Date and Timestamp Columns

### Non-required Entity Metadata Columns

### Required Entity Columns

### Error and Metrics Columns

## Examples
