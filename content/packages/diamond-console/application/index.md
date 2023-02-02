---
title: "Application"
date: 2023-02-01T16:48:05+07:00
draft: false
summary: "Documentation commands for Application Layer"
keywords: ["ddd", "diamond console", "aplication"]
---

## Introduction

Application in Domain Driven Design is a layer that gonna process
user input, and give user an output so this layer shouldn't contains
the whole of business logic of your applications.

## Commands

The list of commands that can you use for structuring your Domain Driven Design project.

### Request

A command to generate request file to your application layer, this command
still generate the request file as usual like Laravel did.
We just made the command readable and can fit with domain naming.

#### Command

```bash
php artisan application:make:request StoreUserRequest User
```

#### Arguments

|  Name  |    Description     |
|:------:|:------------------:|
|  Name  | Request class name |
| Domain |    Domain Name     |

#### Options

|     Name    |          Description           |
|:-----------:|:------------------------------:|
|  `--force`  | Force create the Request class |

---

### Resource

A command to generate resource file to your application layer, this command
still generate the request file as usual like Laravel did.
We just made the command readable and can fit with domain naming.

#### Command

```bash
php artisan application:make:resource UserResource User
```

#### Arguments

|  Name  |     Description     |
|:------:|:-------------------:|
|  Name  | Resource class name |
| Domain |     Domain Name     |

#### Options

|          Name          |             Description              |
|:----------------------:|:------------------------------------:|
|   `--model=ModelName`  |   To hint Model class on Resource    |
|      `--force`         |   Force create the Resource class    |

---
