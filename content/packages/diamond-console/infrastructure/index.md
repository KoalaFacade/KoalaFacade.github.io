---
title: "Infrastructure"
date: 2023-02-01T16:47:03+07:00
draft: false
summary: "List of infrastructure commands from KoalaFacade  Diamond Console"
keywords: ["ddd", "infrastructure"]
---

> List of `infrastructure` Commands

## `infrastructure:make:event PostEvent Post`

> Command for generate an Event class to your project.

### Arguments

|  Name  |   Description    |
|:------:|:----------------:|
|  Name  | Event name class |
| Domain |   Domain Name    |

### Options

|   Name    |         Description          |
|:---------:|:----------------------------:|
| `--force` | Force create the Event class |

---

## `infrastructure:make:factory RoleFactory User`

> Command for generate a Factory class

This command would generate two files :

1. Factory Concrete at Infrastructure/{DomainName}/Database/Factories
2. Factory Contract at Domain/Shared/Contracts/Database/Factories

The bottom of reason why we did this, cause Factories is an Infrastructure component then Domain can't consume any stuff inside Infrastructure, so you can do Dependency Injection at Service Provider for resolve this one.

### Arguments

|  Name  | Description  |
|:------:|:------------:|
|  Name  | Factory Name |
| Domain | Domain Name  |

### Options

|   Name    |          Description           |
|:---------:|:------------------------------:|
| `--force` | Force create the Factory class |

---

## `infrastructure:make:listener PostListener Post`

> Command for generate a Listener class to your project.

### Arguments

|  Name  |     Description     |
|:------:|:-------------------:|
|  Name  | Listener name class |
| Domain |     Domain Name     |

### Options

|        Name     `    |                      Description                      |
|:-------------------:|:-----------------------------------------------------:|
| `--event=NameEvent` | For create Event class and use it into Listener class |
|      `--force`      |            Force create the Listener class            |

---

## `infrastructure:make:mail ApprovedUser User`

> Command for generate a Mail class.

This command will generate Mail class into Infrastructure side because this class purpose is store to external.

### Arguments

|  Name  |   Description   |
|:------:|:---------------:|
|  Name  | Mail name class |
| Domain |   Domain Name   |

### Options

|   Name    |         Description         |
|:---------:|:---------------------------:|
| `--force` | Force create the Mail class |

---

## `infrastructure:make:observer UserObserver User`

> Command for generate an Observer class to your project.

### Arguments

|  Name  |     Description     |
|:------:|:-------------------:|
|  Name  | Observer name class |
| Domain |     Domain Name     |

### Options

|   Name    |           Description           |
|:---------:|:-------------------------------:|
| `--force` | Force create the Observer class |

---

## `infrastructure:make:seeder UserSeeder User`

> Command for generate a Seeder class.

This command will generate Seeder class into Infrastructure because this class purpose is to insert a test data into table.

### Arguments

|  Name  |         Description         |
|:------:|:---------------------------:|
|  Name  |      Seeder name class      |
| Domain |         Domain Name         |

### Options

|   Name    |               Description               |
|:---------:|:---------------------------------------:|
| `--force` |      Force create the Seeder class      |

---

## `infrastructure:make:provider FactoryServiceProvider User`

> Command for generate a Service Provider class.

This command will generate Service Provider class into Infrastructure to binds between Domain and Infrastructure.

### Arguments

|  Name  |         Description         |
|:------:|:---------------------------:|
|  Name  | Service Provider name class |
| Domain |         Domain Name         |

### Options

|   Name    |               Description               |
|:---------:|:---------------------------------------:|
| `--force` | Force create the Service Provider class |

---
