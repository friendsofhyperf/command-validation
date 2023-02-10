# Command Validation

[![Latest Stable Version](https://poser.pugx.org/friendsofhyperf/command-validation/version.png)](https://packagist.org/packages/friendsofhyperf/command-validation)
[![Total Downloads](https://poser.pugx.org/friendsofhyperf/command-validation/d/total.png)](https://packagist.org/packages/friendsofhyperf/command-validation)
[![GitHub license](https://img.shields.io/github/license/friendsofhyperf/command-validation)](https://github.com/friendsofhyperf/command-validation)

The command validation component for Hyperf.

## Installation

```base
composer require friendsofhyperf/command-validation:^3.0
```

## Usage

```php
<?php

declare(strict_types=1);

namespace App\Command;

use FriendsOfHyperf\CommandValidation\Concerns\ValidatesInput;
use Hyperf\Command\Command as HyperfCommand;
use Hyperf\Command\Annotation\Command;

#[Command]
class FooCommand extends HyperfCommand
{
    use ValidatesInput;

    /**
     * 执行的命令行
     */
    protected string $name = 'foo:hello {?name : The name of the person to greet.}';

    public function handle()
    {
        $this->info(sprintf('Hello %s.', $this->input->getArgument('name')));
    }

    public function rules(): array
    {
        return [
            'name' => 'required',
        ];
    }

    protected function messages(): array
    {
        return [
            'name.required' => 'The name is required.',
        ];
    }
}
```

## Sponsor

If you like this project, Buy me a cup of coffee. [ [Alipay](https://hdj.me/images/alipay.jpg) | [WePay](https://hdj.me/images/wechat-pay.jpg) ]
