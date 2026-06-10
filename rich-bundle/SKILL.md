---
name: rich
description: Manages RICH modules in modern Symfony applications. Use when asked to understand the RICH architecture, create a RICH module, or to create the RICH Input, Command, and Handler classes.
---

# RICH Architecture

The core architectural pattern is **RICH** (Request, Input, Command, Handler), provided by the [`1tomany/rich-bundle`](https://github.com/1tomany/rich-bundle) library. It is designed for modern Symfony installations (v7.2+), and works for both web and console applications.

First, read the [RICH Bundle documentation](https://raw.githubusercontent.com/1tomany/rich-bundle/refs/heads/master/README.md) to better understand the overall design pattern. Below is a brief summary of the request flow:

1. A **Controller** or **Console Command** receives a request (HTTP or command line arguments) and resolves an **Input** object. The **Input** object is a DTO that implements `OneToMany\RichBundle\Input\InputInterface` and is validated with the Symfony Validator component.
2. The **Input** object converts to an immutable **Command** object with the `toCommand()` method as defined in `OneToMany\RichBundle\Input\InputInterface`. The **Command** object is an instance of `OneToMany\RichBundle\Command\CommandInterface`.
3. A **Handler** executes business logic on the **Command** and returns a **Result** object. The **Handler** object is an instance of `OneToMany\RichBundle\Handler\HandlerInterface` and the **Result** object is an instance of `OneToMany\RichBundle\Result\ResultInterface`. Though it's not required, the **Result** object often wraps a Doctrine entity or a collection of entities.
4. The **Controller** generally serializes the data wrapped by the **Result** object using the Symfony Serializer component, whereas a **Console Command** generally outputs a nicely formatted table.

## Module structure

Code is organized by domain module rather than by layer. Each module lives in the `src/Module/` directory. Repository implementations live in `src/Repository/` and implement the contract interfaces. Doctrine entities live in `src/Entity/`. You do not need to attempt to generate the Doctrine entity or repository as Symfony provides a `make:entity` console command to do so. The developer will be responsible for running the `make:entity` console command. You can, however, add methods to the repository interface if a new method is needed to find a Doctrine entity.
