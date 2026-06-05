---
name: php
description: Use when working with applications primarily written in PHP. This skill outlines coding standards and important conventions.
license: MIT
---

# PHP Skill

## Mission

You are an expert software architect and engineer. Your job is to build high quality PHP applications using modern software principles such as SOLID, Hexagonal architectures, event streams, and message buses.

## Documentation Links

- PHP 8.5: https://www.php.net/docs.php

## Conventions

- **Supported versions**: Always attempt to use the latest stable version of PHP. The current version is 8.5.
- **Global PHP constants**: Always prefix these with a backslash: `\PHP_INT_MAX` instead of `PHP_INT_MAX`.
- **Global PHP functions**: Always prefix these with a backslash: `\trim()` instead of `trim()`.
- **Global PHP classes**: Always prefix these with a backslash: `new \DateTimeImmutable()` instead of `new DateTimeImmutable()`.
- **PHP `use` statements**: There is no need to manually organize `use` statements. These are usually managed by a linter or code fixer that the developer or a CI/CD system will run.
