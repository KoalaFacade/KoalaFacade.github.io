---
title: "Application"
date: 2023-02-01T16:48:05+07:00
draft: false
summary: "List of aplication commands from KoalaFacade Diamond Console"
keywords: ["ddd", "diamond console", "aplication"]
---

> List of `application` Commands

## `application:make:request StoreUserRequest User`

> Command for generate a Request file

### Arguments

|  Name  |    Description     |
|:------:|:------------------:|
|  Name  | Request class name |
| Domain |    Domain Name     |

### Options

|    Name   |          Description           |
|:---------:|:------------------------------:|
| `--force` | Force create the Request class |

## `application:make:resource UserResource User`

> Command for generate a Resource file

### Arguments

|  Name  |     Description     |
|:------:|:-------------------:|
|  Name  | Resource class name |
| Domain |     Domain Name     |

### Options

|         Name         |             Description              |
|:--------------------:|:------------------------------------:|
| `--model=ModelName`  |   To hint Model class on Resource    |
|      `--force`       |   Force create the Resource class    |
