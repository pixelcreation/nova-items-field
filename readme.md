## Nova Items Field

Laravel Nova array items field with sorting, validation & many [display options](#additional-options)

![nova-array-input-field](https://user-images.githubusercontent.com/29180903/51337942-7d1be300-1a56-11e9-84fa-66f5b285c279.png)

### Installation

```
composer require blendbyte/nova-items-field
```

### Usage

```php
use NovaItemsField\Items;
```

```php
function fields() {
    return [
        Items::make('Emails'),
    ]
}
```

and be sure to [cast](https://laravel.com/docs/5.7/eloquent-mutators#array-and-json-casting) the property as an array on your eloquent model

```php
public $casts = [
    'emails' => 'array'
];
```

### Validation

Use Laravel's built-in [array validation](https://laravel.com/docs/5.7/validation#validating-arrays)

```php
Items::make('Emails')->rules([
    'emails.*' => 'email|min:10',
]),
```

Manually setting the attribute may be needed in some cases.

```php
Items::make('Long Text', 'attribute')->rules([
    'attribute.*' => 'email|min:10',
]),
```

### Array processing

Use the array to perform other actions by making an [observer](https://nova.laravel.com/docs/1.0/resources/#resource-events)

```php
function saving($user)
{
    foreach($user->emails as $email)
    {
        //
    }
}
```

### Replace item vue component

Here's a brief walkthrough to customize the vue item - [view](https://github.com/dillingham/nova-items-field/issues/10#issuecomment-527315057)

### Additional options

| Function                      | Description                      | Default           |
|-------------------------------|----------------------------------|-------------------|
| `->max(number)`               | limit number of items allowed    | false             |
| `->draggable()`               | turn on drag/drop sorting        | false             |
| `->fullWidth()`               | increase the width of field area | false             |
| `->maxHeight(pixel)`          | limit the height of the list     | false             |
| `->listFirst()`               | move add new to the bottom       | false             |
| `->inputType(text)`           | text, date, etc                  | "text"            |
| `->placeholder($value)`       | the new item input text          | "Add a new item"  |
| `->deleteButtonValue($value)` | value for delete button          | `null` (‘x’ icon) |
| `->createButtonValue($value)` | value for create button          | "Add"             |
| `->hideCreateButton()`        | hide the "add" button            | false             |
