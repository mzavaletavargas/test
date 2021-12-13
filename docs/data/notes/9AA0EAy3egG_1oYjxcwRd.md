
# AWS Codebuild

Getting version number from file:

```bash
 - NPM_VERSION=v-$(cat package.json | grep version | head -1 | awk -F":" '{print $2}' | sed 's/[\ ",]//g')
```

## Related

![Node Pipeline Architecture](/assets/images/2021-07-09-21-05-11.png)

[Build specification reference for CodeBuild - AWS CodeBuild](https://docs.aws.amazon.com/codebuild/latest/userguide/build-spec-ref.html)
[Available runtimes - AWS CodeBuild](https://docs.aws.amazon.com/codebuild/latest/userguide/available-runtimes.html)

## Terraform

https://registry.terraform.io/providers/hashicorp/aws/latest/docs/resources/codedeploy_app

## Github webhooks

https://docs.aws.amazon.com/codebuild/latest/userguide/github-webhook.html

## docs

https://docs.aws.amazon.com/codebuild/latest/userguide/codebuild-user.pdf
