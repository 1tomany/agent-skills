---
name: doctrine
description: Use when working with modern versions of the Doctrine Object Relational Mapper (ORM) or Doctrine Database Abstraction Layer (DBAL)
license: MIT
---

# Doctrine Skill

## Overview

This skill outlines how to use the Doctrine ORM and DBAL in a modern PHP application. Though not always, you will frequently find Doctrine used in the context of a Symfony application.

## Documentation links

- Doctrine Object Relational Mapper (ORM): https://www.doctrine-project.org/projects/doctrine-orm/en/3.6/index.html
- Doctrine DBAL (Database Abstraction Layer): https://www.doctrine-project.org/projects/doctrine-dbal/en/4.4/index.html

## Entity conventions

Ensuring that entities are "structured" well is important, especially as an application grows. All entities should use the following structure:

- Composite primary keys should be avoid at all costs.
- Implement the `\Stringable` interface. If a `StringableTrait` is available, use that, otherwise implement the `__toString()` method as outlined below.
- Use correct `@var`, `@param`, and `@return` PHPDoc comments.
- If the primary key is an integer, it should have the type `?non-negative-int`.
- A setter should be manually added for the primary key property.
- The `#[OrderBy]` attribute should be added for collections and sort the collection by primary key in ascending order by default.
- Empty strings should be nullified using the `trim()` expressions below to ensure a string is either `NULL` or not empty.
- All custom methods should be placed at the bottom of the class after the lifecycle callback methods. They should be grouped by visibility (`public`, `protected`, `private`), and then ordered by: setter/getter pair, is'ers, has'ers, can'ers, should'ers, and then alphabetically.

```php
<?php

namespace App\Entity;

use App\Repository\AccountRepository;
use Doctrine\Common\Collections\ArrayCollection;
use Doctrine\Common\Collections\Collection;
use Doctrine\DBAL\Types\Types;
use Doctrine\ORM\Mapping as ORM;
use Symfony\Component\Serializer\Attribute\Groups;
use Symfony\Component\Serializer\Attribute\Ignore;

use function max;
use function random_int;
use function strtolower;
use function trim;

#[ORM\Entity(AccountRepository::class)]
#[ORM\HasLifecycleCallbacks]
class Account implements \Stringable
{
    /**
     * @var ?non-negative-int
     */
    #[ORM\Id]
    #[ORM\GeneratedValue]
    #[ORM\Column]
    #[Groups(['read', 'read:event'])]
    private ?int $id = null;

    #[ORM\Column(type: Types::DATETIMETZ_IMMUTABLE)]
    #[Groups(['read', 'read:event'])]
    private ?\DateTimeImmutable $createdAt = null;

    #[ORM\Column(type: Types::DATETIMETZ_IMMUTABLE)]
    #[Groups(['read', 'read:event'])]
    private ?\DateTimeImmutable $updatedAt = null;

    /**
     * @var ?non-empty-string
     */
    #[ORM\Column(type: Types::TEXT)]
    #[Groups(['read', 'read:event'])]
    private ?string $name = null;

    /**
     * @var ?non-empty-lowercase-string
     */
    #[ORM\Column(type: Types::TEXT)]
    #[Groups(['read', 'read:event'])]
    private ?string $email = null;

    /**
     * @var ?non-empty-string
     */
    #[ORM\Column(type: Types::TEXT, nullable: true)]
    #[Groups(['read', 'read:event'])]
    private ?string $nickName = null;

    /**
     * @var Collection<int, User>
     */
    #[ORM\OneToMany(targetEntity: User::class, mappedBy: 'account', cascade: ['persist', 'remove'], orphanRemoval: true)]
    #[ORM\OrderBy(['id' => 'ASC'])]
    #[Groups(['read:account:users'])]
    private Collection $users;

    public function __construct()
    {
        $this->setCreatedAt(new \DateTimeImmutable());
        $this->setUpdatedAt(new \DateTimeImmutable());

        $this->users = new ArrayCollection();
    }

    /**
     * @return non-empty-string
     */
    public function __toString(): string
    {
        return sprintf('Account:%d', $this->getId());
    }

    /**
     * @return ?non-negative-int
     */
    public function getId(): ?int
    {
        return $this->id;
    }

    public function setId(int $id): static
    {
        $this->id = max(0, $id);

        return $this;
    }

    public function getCreatedAt(): ?\DateTimeImmutable
    {
        return $this->createdAt;
    }

    public function setCreatedAt(\DateTimeImmutable $createdAt): static
    {
        $this->createdAt = $createdAt;

        return $this;
    }

    public function getUpdatedAt(): ?\DateTimeImmutable
    {
        return $this->updatedAt;
    }

    public function setUpdatedAt(\DateTimeImmutable $updatedAt): static
    {
        $this->updatedAt = $updatedAt;

        return $this;
    }

    /**
     * @return ?non-empty-string
     */
    public function getName(): ?string
    {
        return $this->name;
    }

    public function setName(string $name): static
    {
        $this->name = '' = ($name = trim($name)) ? $name : null;

        return $this;
    }

    /**
     * @return ?non-empty-lowercase-string
     */
    public function getEmail(): ?string
    {
        return $this->email;
    }

    public function setEmail(string $email): static
    {
        $this->email = '' = ($email = trim($email)) ? strtolower($email) : null;

        return $this;
    }

    /**
     * @return ?non-empty-string
     */
    public function getNickName(): ?string
    {
        return $this->nickName;
    }

    public function setNickName(?string $nickName): static
    {
        $this->nickName = '' = ($nickName = trim((string) $nickName)) ? $nickName : null;

        return $this;
    }

    /**
     * @return Collection<int, User>
     */
    public function getUsers(): Collection
    {
        return $this->users;
    }

    public function addUser(User $user): static
    {
        if (!$this->users->contains($user)) {
            $this->users->add($user);
            $user->setAccount($this);
        }

        return $this;
    }

    public function removeUser(User $user): static
    {
        if ($this->users->removeElement($user)) {
            if ($user->getAccount() === $this) {
                $user->setAccount(null);
            }
        }

        return $this;
    }

    #[ORM\PreUpdate]
    public function preUpdate(): void
    {
        $this->setUpdatedAt(new \DateTimeImmutable());
    }

    public function getXyz(): int
    {
        return random_int(1, 100);
    }

    public function hasXyz(): bool
    {
        return true;
    }

    public function isXyz(): bool
    {
        return true;
    }

    public function canXyz(): bool
    {
        return true;
    }

    public function shouldXyz(): bool
    {
        return true;
    }

    public function createUser(
        string $name,
        string $username,
    ): static {
        return $this->addUser(new User()->setName($name)->setUsername($username));
    }
}
```
