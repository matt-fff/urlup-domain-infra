# urlup-domain-infra

## Installation

Optionally use your preferred method of creating and activating a virtual environment. For example:

```bash
virtualenv --py 3.10 .venv
source .venv/bin/activate
```

Install local requirements:

```bash
pip install -r requirements.txt
```

## Configuration

The existing `Pulumi.dev.yaml` uses a [Pulumi ESC environment](https://www.pulumi.com/product/esc/), which you won't have access to.

You can either:

1. create your own Pulumi ESC environment with the config values.
2. create a local pulumi config file `Pulumi.your-env.yaml` with your config values.

For reference, here's how urlup.org's domains would look as a local config:

```yaml
config:
  api_domain:
    zone_domain: urlup.org
    cert_domain: api.urlup.org
  redirect_domain:
    zone_domain: uu1.ink
    cert_domain: uu1.ink
  frontend_prod_domain:
    zone_domain: urlup.org
    cert_domain: urlup.org
  frontend_staging_domain:
    zone_domain: codefold.net
    cert_domain: "*.urlup.codefold.net"
  tags:
    app: urlup
```

Here are those same values formatted for Pulumi ESC:

```yaml
values:
  pulumiConfig:
    api_domain:
      zone_domain: urlup.org
      cert_domain: api.urlup.org
    redirect_domain:
      zone_domain: uu1.ink
      cert_domain: uu1.ink
    frontend_prod_domain:
      zone_domain: urlup.org
      cert_domain: urlup.org
    frontend_staging_domain:
      zone_domain: codefold.net
      cert_domain: "*.urlup.codefold.net"
    tags:
      app: urlup
```

## Prerequisites

You'll need to install/configure [Pulumi](https://www.pulumi.com/docs/install/) and probably the [AWS CLI](https://aws.amazon.com/cli/).

## Running

Select your stack with `pulumi stack select` - you'll be given the option to create a new stack.
Your stack name should match with your local config;
if you name your stack "staging", you'll want to have a config file named `Pulumi.staging.yaml`.

Run `pulumi preview` to preview your stack.
Run `pulumi up` to deploy or update your stack.
Run `pulumi destroy` to destroy the stack.
