---
name: phinx
description: Use when writing database migrations with Phinx
license: MIT
---

# Database Migrations Skill

## Overview

This skill outlines how to write database migrations with a developer tool like Phinx or the Doctrine Migrations library.

## Documentation

- **Phinx Documentation:** https://phinx.org/docs/
- **Writing Migrations:** https://phinx.org/docs/migrations.html

## Creating a Migration

Use the CLI tool provided by the library to create a new migration to ensure it follows the format outlined by any configuration files.

```shell
php vendor/bin/phinx create CreateTableAccount
```

## Naming a Migration

Attempt to name the migration so that it mirrors the SQL it contains:

- `CreateTableAccount` instead of `CreateAccountTable`
- `AlterTableAccountAddColumnEmailAddress` instead of `AlterAccountTableAddEmailAddressColumn`
- `AlterTableUsersAddColumnsFirstNameAndLastName` instead of `AlterTableUsersAddFirstNameAndLastNameColumns`
- `DropTableLegacyAccount` instead of `DropLegacyAccountTable`
