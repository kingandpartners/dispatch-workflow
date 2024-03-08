# Dispatch Workflow
Used for dispatching workflows across repositories

## Inputs

| Input        | Description                                                                                             | Required                     |
|--------------|---------------------------------------------------------------------------------------------------------|------------------------------|
| token        | GitHub token that will be used for remote repository                                                    | Yes                          |
| repo         | Path to your satis configuration file                                                                   | Yes                          |
| workflow_id  | Path to your satis configuration file                                                                   | Yes                          |
| ref          | Branch of repository to dispatch workflow on                                                            | No<br/>Default = 'main'      |
| inputs       | Path to your satis configuration file                                                                   | No<br/>Default = '{}'        |

## Outputs
None

## Usage
Example `.github/workflow/release.yaml`
```yaml
name: Trigger Satis Build

on:
  - release
  - push

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: kingandpartners/dispatch-workflow@main
        with:
          token: ${{ secrets.APP_TOKEN }}
          repo: owner/repo
          workflow_id: partial-build.yml
          inputs: '{"package_name": "some-composer/repo"}'
```
