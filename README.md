# Transformer Template Project

## About

This is a template project for creating data transformers that can be registered with the [Data Registry](https://github.com/covid-open-data/data-registry).
The workflow for transformation is managed via [GitHub Actions](https://github.com/features/actions).

## Usage

1. Copy or fork this repo.
2. Search the repo for `TODO` and make the appropriate changes for your transformer.

## Development

There are three primary files that can be changed for your specific needs:

1. [xform.sh](src/xform.sh)
   - This script handles installing dependencies and executing your transformer. 
2. [install.sh](src/install.sh) 
   - This script can be used to install additional dependencies that your transformer requires.
   - This file can be deleted if it's not needed.
3. [xform.R](src/xform.R)
   - This is the default transformer file.
   - This file can be deleted or replaced with code for any other programming language. You will need to update [xform.sh](src/xform.sh) to call your new code if not using R. 

To schedule your transformer in GitHub Actions you will need to uncomment the scheduling section in [.github/workflows/main.yml](.github/workflows/main.yml).

Search the codebase for `TODO` to find additional items that may need to be configured for your instance.

## Testing

Each action runs in its own Docker container in GitHub Actions and locally for testing.
Each action has its own Makefile with common commands to run and test each step of the workflow.
The main [Makefile](Makefile) has commands for executing each action.

Primary Commands:
- `make run-workflow`
  - Runs the xform and git-push. 
  - Running locally via docker-compose does not commit and push. Edit [.github/actions/git-push/docker-compose.yml](.github/actions/git-push/docker-compose.yml) to modify this behaviour if needed.
- `make run-xform`
  - Run the xform.
- `make run-git-push`
  - Run git push.

See [Makefile](Makefile) for all commands and each individual Makefile in the [actions](.github/actions) folders.
