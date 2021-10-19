# Get Project Item Id

Get node ID of Project Item.

# Usage

## Specify parameters without id

```yaml
- uses: monry/actions-get-project-item-id@v1
  with:
    # Personal Access Token that with `repo` and `org:read` are granted.
    github-token: ${{ secrets.PAT_PROJECT_NEXT }}
    project-owner: 'monry'
    project-owner-type: 'user'
    project-number: 1
    issue-repository: 'monry/awesome-repository'
    issue-number: 100
```

## Specify parameters with id

```yaml
- uses: monry/actions-get-project-item-id@v1
  with:
    # Personal Access Token that with `repo` and `org:read` are granted.
    github-token: ${{ secrets.PAT_PROJECT_NEXT }}
    project-id: 'PN_xxxxxxxxxxxxxx'
    issue-id: ${{ github.event.issue.node_id }}
```

# Inputs

## `github-token`

This action requires Personal Access Token that `repo` and `org:read` are granted.

For security purposes, it is recommended to register Personal Access Token as Secrets.

## `project-id`

Node ID of project.

This value can obtain from [monry/actions-get-project-id@v1](https://github.com/marketplace/actions/get-project-id).<br />
See also: [monry/actions-get-project-id](https://github.com/monry/actions-get-project-id) repos.

## `project-owner`

Owner name of project.

Owner name refers to the user name or the organization name.

**NOTICE** This value is required if `project-id` is not specified.

## `project-owner-type`

Type of owner of project.

The value should be one of the following values.

- `user`
- `organization` (default)

**NOTICE** This value is required if `project-id` is not specified.

## `project-number`

Project number.

The project number is the number shown in the URL or list of projects.

**NOTICE** This value is required if `project-id` is not specified.

## `issue-id`

Node ID of issue.

This value can obtain from `github.event.issue.node_id` if triggered by `on: issues`.

## `issue-repository`

Repository name of issue with owner name.

**NOTICE** This value is required if `issue-id` is not specified.

## `issue-number`

Number of issue.

**NOTICE** This value is required if `issue-id` is not specified.

# Outputs

## `project-item-id`

Obtained value stores into output variable named `project-item-id`.

```yaml
- uses: monry/actions-get-project-item-id@v1
  id: get-project-item-id # requires `id` to refer output values with after steps
  with:
    github-token: ${{ secrets.PAT_PROJECT_NEXT }}
    project-owner: 'monry'
    project-owner-type: 'user'
    project-number: 1
    issue-repository: 'monry/awesome-repository'
    issue-number: 100
- run: |
    echo '${{ steps.get-project-item-id.outputs.project-item-id }}'
```
