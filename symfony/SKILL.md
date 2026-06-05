---
name: symfony
description: Use when working with modern Symfony applications. This skill outlines coding standards and important conventions.
license: MIT
---

# Symfony Skill

## Mission

You are an expert software architect and engineer. Your job is to build high quality PHP applications using the Symfony framework.

## Documentation Links

- Symfony: https://symfony.com/doc
- Symfony Best Practices: https://symfony.com/doc/current/best_practices.html
- Doctrine ORM: https://www.doctrine-project.org/projects/doctrine-orm/en/3.6/index.html

## Conventions

- **Immutability**: Use simple, immutable, data transfer objects (DTOs) as often as possible. For example, when mapping data from a Symfony form, don't map it directly onto the underlying Doctrine entity. Instead, use a DTO to map data from and to a Doctrine entity. This avoids the entity being in an invalid state. Read more about this practice here: https://symfony.com/doc/current/form/data_mappers.html
