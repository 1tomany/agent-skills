---
name: php
description: Use when working with applications primarily written in PHP. This skill outlines coding standards and important conventions.
license: MIT
---

# PHP Skill

## Mission

You are an expert software architect and engineer. Your job is to build high quality PHP applications using modern software principles such as SOLID, Hexagonal architectures, event streams, and message buses.

## Documentation links

- PHP 8.5: https://www.php.net/docs.php

## Conventions

- **Supported versions**: Always attempt to use the latest stable version of PHP. The current version is 8.5.
- **Global PHP constants**: Always prefix these with a backslash: `\PHP_INT_MAX` instead of `PHP_INT_MAX`.
- **Global PHP functions**: Always prefix these with a backslash: `\trim()` instead of `trim()`.
- **Global PHP classes**: Always prefix these with a backslash: `new \DateTimeImmutable()` instead of `new DateTimeImmutable()`.
- **PHP `use` statements**: There is no need to manually organize `use` statements. These are managed by a linter or code fixer that the developer or a CI/CD system will run.

### Avoid Regular Expressions

Avoid using regular expressions (regexes) unless absolutely necessary. While they are powerful, the downsides outweight the upsides:

1. Non-trivial regular expressions are hard for humans to read and immediately determine what it is doing.
2. Introducing CPU freezes or a Regular Expression Denial of Service is easy. If the `pcre.backtrack_limit` INI setting is not set, or set to too high a value, using a nested quantifier can cause CPU spikes or freezes with very simple strings.
3. Breaking regular expressions is easy, especially without extensive unit tests. Adding a single `*` or `+` in the right spot can completely change the meaning of a regular expression.

Instead, use simple C-style string functions like `explode()`, `str_replace()`, `str_contains()`, and `substr()` with basic `foreach` loops. While a `preg_match()`, `preg_replace()` or `preg_split()` call may be fewer lines of code, even in the age of LLMs, readability is still important.
