---
title: "Domain"
date: 2023-02-01T16:47:20+07:00
draft: false
summary: "Documentation commands for Domain Layer"
keywords: ["ddd", "diamond console", "domain"]
---

> List of `domain` Commands

## `domain:make:action GenerateProfileAction User`

> Command for generate an Action inside your Domain directory.

### Arguments

|  Name  |    Description    |
|:------:|:-----------------:|
|  Name  | Action class name |
| Domain |    Domain Name    |

### Options

|         Name         |            Description             |
|:--------------------:|:----------------------------------:|
|      `--force`       |   Force create the Action class    |

---

## `domain:make:builder UserBuilder User`

> Command for generate a Query Builder inside your Domain directory.

### Arguments

|  Name  |    Description     |
|:------:|:------------------:|
|  Name  | Builder class name |
| Domain |    Domain Name     |

### Options

|        Name         |             Description              |
|:-------------------:|:------------------------------------:|
| `--model=ModelName` | To hint Model class on Query Builder |
|      `--force`      |    Force create the Builder class    |

### Usage

In your model you can use the builder like the example below.

`src/Domain/Shared/User/Models/User.php`

```php
<?php

namespace Domain\Shared\User\Models;

use Domain\Shared\User\Models\Builders\UserBuilder;
use Illuminate\Database\Eloquent\Factories\HasFactory;
use Illuminate\Database\Eloquent\Model;

/**
 * @mixin  UserBuilder
 */
class User extends Model
{
    use HasFactory;

    /**
     * @param  $query
     *
     * @return UserBuilder<User>
     */
    public function newEloquentBuilder($query): UserBuilder
    {
        return new UserBuilder(query: $query);
    }
}
```

---

## `domain:make:data-transfer-object RoleData User`

> Command for generate a Data Transfer Object with plain PHP to your domain directory.

### Arguments

|  Name  |           Description           |
|:------:|:-------------------------------:|
|  Name  | Data Transfer Object class name |
| Domain |           Domain Name           |

### Options

|   Name    |                 Description                 |
|:---------:|:-------------------------------------------:|
| `--force` | Force create the Data Transfer Object class |

---

## `domain:make:enum Role User`

> Command for generate an Enum to your Domain directory.

### Arguments

|  Name  |   Description   |
|:------:|:---------------:|
|  Name  | Enum class name |
| Domain |   Domain Name   |

### Options

|   Name    |         Description         |
|:---------:|:---------------------------:|
| `--force` | Force create the Enum class |

---

## `domain:make:model User User`

> Command for generate a Model inside Shared in Domain directory, all Model will store shared folder since another Domain probably consume the Model at the same time.

### Arguments

|  Name  |   Description    |
|:------:|:----------------:|
|  Name  | Model class name |
| Domain |   Domain Name    |

### Options

|         Name          |                                                       Description                                                        |
|:---------------------:|:------------------------------------------------------------------------------------------------------------------------:|
| `-m` or `--migration` |                                         Create Migration file when model created                                         |
|  `-f` or `--factory`  | Create Factory class when Model created this option will generate two files, Factory contract and Factory concrete |
|      `--force`      |                                               Force create the Model class                                               |

---

## `domain:make:value-object ReferralCode User`

> Command for generate a Value Object class. This command will generate Value Object class into Domain.

### Arguments

|  Name  |         Description         |
|:------:|:---------------------------:|
|  Name  |   Value Object name class   |
| Domain |         Domain Name         |

### Options

|   Name    |               Description               |
|:---------:|:---------------------------------------:|
| `--force` |   Force create the Value Object class   |
