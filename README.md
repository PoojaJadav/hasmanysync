# HasMany Sync

## Introduction

This package adds has-many sync relationships to Eloquent in Laravel. It's same like sync relationship.

## Installation

You can install the package via composer

````
composer require poojajadav/hasmanysync
````

## Usage

#### Hasmany sync

Hasmany-sync relation is almost identical to standard Syncing Associations except. It'll add, update and remove data from hasmany relationship.
Example:

```php
<?php

namespace App\Models;

use Illuminate\Database\Eloquent\Factories\HasFactory;
use Illuminate\Database\Eloquent\Model;
use Poojajadav\Hasmanysync\Traits\HasManySync;

class Post extends Model
{
    use HasFactory;
    use HasManySync;

    protected $guarded = [];

    public function comments()
    {
        return $this->hasMany(Comment::class);
    }
}
```

Now you can action on relationship like:
```php
<?php

$post = Post::first();
$comments = [
  [
       "id" => 2,
       "post_id" => 1,
       "name" => "This comment will be update"
     ],
  ['name' => 'This comment will attach'],
];

$post->comments()->sync($comments);
```

### Contributors
- [Dipak Gavali](https://github.com/dipak-pinetco)
- [Pinal Patel](https://github.com/PinalPatel160)
- [Pooja Jadav](https://github.com/poojajadav)
