# The CIO CI / CD Runbook

A runbook for the platform team to use when recovering from errors/outages.

## Table of Contents

- [The CIO CI / CD Runbook](#the-cio-ci--cd-runbook)
  - [Table of Contents](#table-of-contents)
  - [Getting Started](#getting-started)
  - [Local Development](#local-development)
  - [Deploying Updates](#deploying-updates)

## Getting Started

This repository uses `mkdocs` to generate a static website from GitHub flavored markdown. `mkdocs` is a Python-based tool and can be installed along with other dependencies using [Poetry](https://python-poetry.org).

Install Poetry on your system by following the instructions at https://python-poetry.org/docs/#installation. Currently, micropipenv is not compatible with versions of poetry at 1.5.0 or higher. Therefore, I recommend installing via `curl -sSL https://install.python-poetry.org | python3 - --version 1.4.2`. See: https://github.com/thoth-station/micropipenv/issues/280.

Next, run the following commands to install `mkdocs` and other dependencies

```bash
poetry install
```

The above command installs dependencies in an isolated environment for this project

## Local Development

When creating or updating the content of the site, `poetry run serve` can be used to serve the site from the local filesystem. `poetry run package` will produce a static html copy of the site and is used by the pipeline.

```bash
poetry run serve
```

`mkdocs` will automatically rebuild the site as changes are made.

## Deploying Updates

This repository uses the `python-v39-poetry-ui-container-image` pipeline to deploy the documentation to Cirrus. It will build and deploy pushed branches to a test application with a custom route, and the `main` branch to the production route.


## Adding or changing the pfe password section
`htpasswd -c .htpasswd username`  
- It will ask you for a password after  
	- Then just git add/commit/push the site/.htpasswd-pfe file  
