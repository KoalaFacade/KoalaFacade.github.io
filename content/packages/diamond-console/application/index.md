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

### Data Transfer Object

Command for generate a Data Transfer Object with plain PHP to your application directory.

For advance usage you can go [here](#data-transfer-object-1)
#### Command

```bash
php artisan application:make:data-transfer-object RoleData User
```

#### Arguments

|  Name  |           Description           |
|:------:|:-------------------------------:|
|  Name  | Data Transfer Object class name |
| Domain |           Domain Name           |

#### Options

|   Name    |                 Description                 |
|:---------:|:-------------------------------------------:|
| `--force` | Force create the Data Transfer Object class |

---

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

## Advance Usage

Some files have advance usage to make your development experience be better.

### Data Transfer Object

For you information our DTO would automatically assign the data according the property type you define, let's say you
have property that had type enum type, if the given data match with case name or value within the enum class, we will assign with that enum, This also applies to other data types. 
what if no one's match? We will return exception for you.

#### 1. Define DTO
```php
use KoalaFacade\DiamondConsole\Foundation\DataTransferObject;

class ExampleData extends DataTransferObject
{
    public function __construct(
        public string | null $firstName,
        public AnotherDTO | null $roles,
        public Enum | null $lastName
        //......another properties
    ) {}
}
```
#### 2. Input array data to DTO

Let's say I'd DTO like below
```php
use KoalaFacade\DiamondConsole\Foundation\DataTransferObject;

class ExampleData extends DataTransferObject
{
    public function __construct(
        public string | null $firstName,
        public string | null $lastName
    ) {}
}
```
you can automatically assign the constructor like below. with notes the array key shall match with the 
construsctor naming style. 

```php
$data = [
    'firstName' => 'Stiven',
    'lastName' => 'Katuuk'
];

$resolvedData = ExampleData::resolve(data: $data);

echo $resolvedData->firstName;
```

you probably have an array where the key is using snake_case style and you constructor using camelCase you can
override the parent method to make the input array keys match with you constructor naming style.

```php
use KoalaFacade\DiamondConsole\Foundation\DataTransferObject;
use Illuminate\Support\Str;

class ExampleData extends DataTransferObject
{
    public function __construct(
        public string | null $firstName,
        public string | null $lastName
    ) {}
    
    /**
     * Resolve the input of array key to constructor naming
     *
     * @param  string  $key
     * @return string
     */
    protected static function resolveArrayKeyOfInput(string $key): string
    {
        //$key is first_name it will convert to firstName
        return Str::camel(value: $key); // you can utilise the array key of input here
    }
}

$data = [
    'first_name' => 'Stiven',
    'last_name' => 'Katuuk'
];

$resolvedData = ExampleData::resolve(data: $data);

echo $resolvedData->firstName;
```
#### 3. Wrap array values into particular DTO
Let say in the future you're going to have array that contains value as array as well, and you want to wrap it into particular
DTO you can take advantage from php stan to do it, and we will automatically map the value for you.

```php
use KoalaFacade\DiamondConsole\Foundation\DataTransferObject;

class ExampleData extends DataTransferObject
{
    public function __construct(
        public string | null $firstName,
        /** @var array<int, RoleData> $roles */
        public array $roles = []
    ) {}
}

$data = [
    'first_name' => 'Stiven',
    'roles' => [
        ['name' => 'Administrator'],
        ['name' => 'Moderator']
    ]
];

$resolvedData = ExampleData::resolve(data: $data);

// will return array that already mapped RoleData 
var_dump($data->roles); 
```

To better understanding how our DTO works may you can take a look to the external package that we would mention, under the hood we're using
[cuyz/valinor](https://valinor.cuyz.io/latest/getting-started/) to help us automatically map the input data to our DTO.

#### 4. Dump and die the current data
Sometimes we want to debug the incoming data

```php
use KoalaFacade\DiamondConsole\Foundation\DataTransferObject;

class ExampleData extends DataTransferObject
{
    public function __construct(
        public string | null $firstName,
        public string | null $lastName = null
    ) {}
}

$data = ['first_name' => 'Kevin'];

ExampleData::resolve($data)->dd(); 
```

#### 5. Keep the code clean by avoid the defining variable
Sometimes we want to avoid defining the variable by implicit
```php
use KoalaFacade\DiamondConsole\Foundation\DataTransferObject;

class ExampleData extends DataTransferObject
{
    public function __construct(
        public string | null $firstName,
        public string | null $lastName = null
    ) {}
}

// Approach 1
(new ExampleData(firstName: 'Kevin'))
    ->tap(callable: function (ExampleData $data): void {
        // Business Logic
    });

// Approach 2
$data = ['first_name' => 'Kevin'];

ExampleData::resolve($data)
    ->tap(callable: function (ExampleData $data): void {
        // Business Logic
    });
```

#### 6. Clone the existing DTO into new DTO
Sometimes we want to duplicate the existing DTO but won't to redefined again and again, to solve this we gonna use
**Prototype Pattern**
```php
use KoalaFacade\DiamondConsole\Foundation\DataTransferObject;

class ExampleData extends DataTransferObject
{
    public function __construct(
        public string | null $firstName,
        public string | null $lastName = null
    ) {}
}

$data = new ExampleData(firstName: 'Kevin'); // fistName: 'Kevin'
$newData = $data->with(lastName: 'Khansa'); // fistName: 'Kevin', lastName: 'Khansa'
```
