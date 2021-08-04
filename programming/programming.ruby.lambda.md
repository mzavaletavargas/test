---
id: RrrexBaG2ydBnKa9
title: Lambda
desc: ""
updated: 1628091510972
created: 1627923171051
---

## Deploy ruby AWS Lambda

## Steps

Check this guide: https://docs.aws.amazon.com/lambda/latest/dg/ruby-package.html

```bash
# set path for fetching dependenciess
bundle config set --local path 'vendor/bundle'

# zip the following files/folders
# my_function.rb is in the zip folder root

.
├── lib
│   ├── some_service.rb
│   ├── ohter_file.rb
│   └── ...
├── vendor
│   └── bundle
│       ├── ruby
│       └── other_dependency...
└── my_function.rb
```

`my_function.rb`

https://docs.aws.amazon.com/lambda/latest/dg/ruby-handler.html

```ruby
require './lib/some_service'

def handler(event:, context:)
  puts Service.sayHi
  {
    'statusCode' => '200',
    'body' => 'OK'
  }
end
```

When setting up your lambda use `my_function.hanlder`
Choose the right [ruby version](https://docs.aws.amazon.com/lambda/latest/dg/lambda-ruby.html)

## AWS SDK to connect to vault using IAM role

Using vault-ruby : https://github.com/hashicorp/vault-ruby

```ruby
  provider_chain = Aws::CredentialProviderChain.new
  credentials = provider_chain.resolve
  secret_auth = Vault.auth.aws_iam(
    "my-role",
    credentials
  )
```
