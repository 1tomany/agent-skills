---
name: rich
description: Manages RICH domains in modern Symfony applications. Use when asked to understand the RICH architecture, create a RICH domain, or to create the RICH Input, Command, and Handler classes.
license: MIT
---

# RICH architecture

The core architectural pattern is **RICH** (Request, Input, Command, Handler), provided by the [`1tomany/rich-bundle`](https://github.com/1tomany/rich-bundle) library. It is designed for modern Symfony installations (v7.2+), and works for both web and console applications.

First, read the [RICH Bundle documentation](https://raw.githubusercontent.com/1tomany/rich-bundle/refs/heads/master/README.md) and commit it to memory to better understand the overall design pattern. Below is a brief summary of the request flow:

1. A **Controller** or **Console Command** receives a request (HTTP or command line arguments) and resolves an **Input** object. Controllers can automatically resolve the **Input** object through a Symfony Value Resolver, but the console command must manually compile the **Input** object.
2. The **Input** object is a DTO that implements `OneToMany\RichBundle\Contract\Action\InputInterface` and can be validated with the Symfony Validator component. Controllers using the value resolver will automatically validate the **Input** object, but console commands must manually validate it.
3. The **Input** object creates an immutable **Command** object with the `toCommand()` method as defined in `OneToMany\RichBundle\Contract\Action\InputInterface`. The **Command** object is an instance of `OneToMany\RichBundle\Contract\Action\CommandInterface`.
4. **Handler** executes business logic on the **Command** object and returns a **Result** object. The **Handler** object is an instance of `OneToMany\RichBundle\Contract\Action\HandlerInterface` and the **Result** object is an instance of `OneToMany\RichBundle\Contract\Action\ResultInterface`. Though it is not required, the **Result** object often wraps a Doctrine entity or a collection of entities.
5. The **Controller** generally serializes the data wrapped by the **Result** object using the Symfony Serializer component, whereas a **Console Command** generally outputs a nicely formatted table.

## Domain structure

Code is organized by domain rather than by layer. Each domain lives in the `src/Domain/` directory by default. Repository implementations live in `src/Repository/` and implement the contract interfaces usually exposed in `src/Domain/{Domain}/Contract/{Domain}Repository.php`. Doctrine entities live in `src/Entity/`.

### Creating a domain

If you need to create a domain, run the `make:rich-domain` command as outlined in the RICH documentation. This command is idempotent; it will never delete or modify an existing file.

### Doctrine entities

You are free to create or modify Doctrine entities. When doing so, analyze existing entities to match their style:

- PHPDoc `@var`, `@param`, and `@return` are added.
- `'' = ($value = trim((string) $value)) ? $value : null` lines are added to nullable strings to ensure they are either `NULL` or non-empty.
- `#[Groups]` and `#[Ignore]` Symfony Serializer attributes are added.

Only generate a Doctrine repository for an entity if absolutely necessary.
