# Next.js on AWS with Terraform Example Project

This example project demonstrates how to deploy Next.js to AWS using serverless technologies. For more information, please see the blog post: [Deploy Serverless Next.js to AWS with Terraform 1.1](https://maxrohde.com/2022/01/22/deploy-serverless-next-js-to-aws-with-terraform-1-1/).

In order to adapt this project to your own needs, clone it and modify the file [packages/app-nextjs-bootstrap/goldstack.json](https://github.com/mxro/nextjs_aws_terraform/blob/master/packages/app-nextjs-bootstrap/goldstack.json). Replace the all configuration items under `deployments` with values specific to your project.

```json
{
  "$schema": "./schemas/package.schema.json",
  "name": "app-nextjs-bootstrap",
  "template": "app-nextjs-bootstrap",
  "templateVersion": "0.1.32",
  "configuration": {},
  "deployments": [
    {
      "name": "prod",
      "configuration": {
        "defaultCacheDuration": 10,
        "hostedZoneDomain": "dev.goldstack.party",
        "websiteDomain": "nextjs-aws-terraform11.dev.goldstack.party",
        "websiteDomainRedirect": "www.nextjs-aws-terraform11.dev.goldstack.party"
      },
      "awsUser": "awsUser",
      "awsRegion": "us-west-2"
    }
  ]
}
```

For more information on the configuration options, see [Next.js Bootstrap Configuration](https://docs.dev.goldstack.party/docs/modules/app-nextjs-bootstrap#configure).

You also will need to configure access to your AWS account. For more information on this, please see [Goldstack Documentation - AWS Configuration](https://docs.dev.goldstack.party/docs/goldstack/configuration#aws-configuration).

Once you have updated the configuration, you can get your project deployed with:

```sh
yarn
yarn build
cd packages/app-nextjs-bootstrap
yarn infra up prod
yarn deploy prod
```

Or run `yarn watch` in the `app-nextjs-bootstrap` directory to test your project locally.

