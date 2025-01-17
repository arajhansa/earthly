# Earthly Cloud

Earthly Cloud is a collection of features that enrich the Earthly experience via cloud-based services. These include:

* [Earthly Cloud Secrets](./cloud-secrets.md): A secret management system that allows you to store secrets in a cloud-based service and use them across builds.
* [Earthly Satellites](./satellites.md): Cloud-based Buildkit instances managed by the Earthly team.
* [Earthly CI](./earthly-ci.md): A cloud-based CI/CD system that allows you to continuously build your code in the cloud.

## Getting started

### Creating an account

To get started with Earthly Cloud, you'll need to register an Earthly account. You can do so by visiting [Earthly CI](https://ci.earthly.dev), or by using the CLI as described below.

```bash
earthly account register --email <email>
```

An email will be sent to you containing a verification token. Next run:

```bash
earthly account register --email <email> --token <token>
```

This command will prompt you to set a password, and to optionally register a public-key for password-less authentication.

### Creating or joining an Earthly org

An Earthly org allows you to share projects, secrets, satellites and pipelines with colleagues. To view the orgs you belong to, run:

```bash
earthly org ls
```

To create an Earthly org you can run:

```bash
earthly org create <org-name>
```

To invite another user to join your org, run:

```bash
earthly --org <org-name> org invite <email>
```

You can join an Earthly org by following the steps outlined in the invitation email sent to you by an Earthly admin.

### Creating a project

To use certain features, such as Earthly CI, or Earthly Cloud Secrets, you will aditionally need to create an Earthly Project. You can create a project by running:

```bash
earthly project --org <org-name> create <project-name>
```

## Logging in from a CI

To be able to use certain Earthly features, such as Cloud Secrets, or Satellites from a CI other than Earthly CI, you will need to log into Earthly. The easiest way to do that is to create an Earthly authentication token by running

```bash
earthly account create-token [--write] <token-name>
```

This token can then be exported as an environment variable in the CI of choice.

```bash
EARTHLY_TOKEN=...
```

Which will then force Earthly to use that token when accessing secrets or satellites.
