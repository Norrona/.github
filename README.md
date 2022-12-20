# Norrona Workflows

## Description

This is a repository for callable workflows to be used in Github actions.

## Workflows

### build.yaml

This workflow builds an application from a dockerfile and publishes it to GCP Artifact Registry.

It requires two inputs in order to function:
- `APP_NAME` - This will be the artifact name in Artifact Registry
- `DOCKERFILE_PATH` - The relative path to a Dockerfile within a repository

The main jobs of the workflow:
- `test` - Builds the application from a dockerfile, tags it with short sha and pushes it to an Artifact Registry repository
- `prod` - Triggered from a semver tag, fetches the latest artifact and tags it with semver

The workflow also calls upon the present slack workflows in order to post build messages.

