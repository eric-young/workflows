# workflows

Set of re-usable github workflows, intended for use with the Dell Technologies CSI/CSM Projects

Workflows can be found in the /workflows directory

Reusable workflows require a `workflow_call` trigger, and can optionally accept inputs and secrets

Example of a reusable workflow:
```
name: Reusable Workflow
on:
  workflow_call:
    inputs:
      input1:
        description: 'Input 1'
        required: true
        type: string
    secrets:
      secret1:
        description: 'Secret 1'
        required: true
jobs:
  job1:
    runs-on: ubuntu-latest
    steps:
      - name: Step 1
        run: echo "This is a reusable workflow"
```


Example of calling a reusable workflow:
```
name: Caller Workflow
on: [push]
jobs:
  job1:
    uses: eric-young/workflows/workflows/reusable-workflow.yml@main
    with:
      input1: 'Hello, World!'
    secrets:
      secret1: ${{ secrets.SECRET1 }}

```
