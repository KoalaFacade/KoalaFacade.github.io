---
title: "Infrastructure"
date: 2023-02-01T16:47:03+07:00
draft: false
summary: "Documentation commands for Infrastructure Layer"
keywords: ["ddd", "diamond console", "infrastructure"]
---

## Introduction

Infrastructure Layer in Domain Driven Design is a layer that contains
external services such as Database, Messaging System, and Email Services etc.
So mainly this layer contains the whole external services logic.

## Commands

The list of commands that can you use for structuring your Domain Driven Design project.

### Event

Command for generate an Event class to your project.

#### Command

```bash
php artisan infrastructure:make:event PostEvent Post
```

#### Arguments

|  Name  |   Description    |
|:------:|:----------------:|
|  Name  | Event name class |
| Domain |   Domain Name    |

#### Options

|   Name    |         Description          |
|:---------:|:----------------------------:|
| `--force` | Force create the Event class |

---

### Factory

Command for generate a Factory class.

This command would generate two files :

1. Factory Concrete at Infrastructure/{DomainName}/Database/Factories
2. Factory Contract at Domain/Shared/Contracts/Database/Factories

The bottom of reason why we did this, cause Factories is an Infrastructure component then
Domain can't consume any stuff inside Infrastructure, so you can do Dependency Injection
at Service Provider for resolve this one.

#### Command

```bash
php artisan infrastructure:make:factory RoleFactory User
```

#### Arguments

|  Name  | Description  |
|:------:|:------------:|
|  Name  | Factory Name |
| Domain | Domain Name  |

#### Options

|   Name    |          Description           |
|:---------:|:------------------------------:|
| `--force` | Force create the Factory class |

---

### Listener

Command for generate a Listener class to your project.

#### Command

```bash
php artisan infrastructure:make:listener PostListener Post
```

#### Arguments

|  Name  |     Description     |
|:------:|:-------------------:|
|  Name  | Listener name class |
| Domain |     Domain Name     |

#### Options

|        Name     `    |                      Description                      |
|:-------------------:|:-----------------------------------------------------:|
| `--event=NameEvent` | For create Event class and use it into Listener class |
|      `--force`      |            Force create the Listener class            |

---

### Mail

Command for generate a Mail class.
This command will generate Mail class into Infrastructure side because this class
purpose is store to external.

#### Command

```bash
php artisan infrastructure:make:mail ApprovedUser User
```

#### Arguments

|  Name  |   Description   |
|:------:|:---------------:|
|  Name  | Mail name class |
| Domain |   Domain Name   |

#### Options

|   Name    |         Description         |
|:---------:|:---------------------------:|
| `--force` | Force create the Mail class |

---

### Observer

Command for generate an Observer class to your project.

#### Command

```bash
php artisan infrastructure:make:observer UserObserver User
```

#### Arguments

|  Name  |     Description     |
|:------:|:-------------------:|
|  Name  | Observer name class |
| Domain |     Domain Name     |

#### Options

|   Name    |           Description           |
|:---------:|:-------------------------------:|
| `--force` | Force create the Observer class |

---

### Seeder

Command for generate a Seeder class.
This command will generate Seeder class into Infrastructure because this class
purpose is to insert a test data into table.

#### Commadn

```bash
php artisan infrastructure:make:seeder UserSeeder User
```

#### Arguments

|  Name  |         Description         |
|:------:|:---------------------------:|
|  Name  |      Seeder name class      |
| Domain |         Domain Name         |

#### Options

|   Name    |               Description               |
|:---------:|:---------------------------------------:|
| `--force` |      Force create the Seeder class      |

---

### Provider

Command for generate a Service Provider class.
This command will generate Service Provider class into Infrastructure to binds
between Domain and Infrastructure.

#### Command

```bash
php artisan infrastructure:make:provider FactoryServiceProvider User
```

#### Arguments

|  Name  |         Description         |
|:------:|:---------------------------:|
|  Name  | Service Provider name class |
| Domain |         Domain Name         |

#### Options

|   Name    |               Description               |
|:---------:|:---------------------------------------:|
| `--force` | Force create the Service Provider class |

---
