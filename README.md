# ossr-new-deposit

GitHub action to upload a new record into the ESCAPE Open-source Software and Service Repository

To use, add the following to your github action file (e.g. `.github/workflows/ossr.yml`):

```

on:
  push:
    tags:
      - '*'

jobs:
  ossr_new_entry:
    runs-on: ubuntu-latest
    name: A job to upload a new record in the OSSR
    steps:
      - uses: escape2020/ossr-new-deposit@main
        with:
          repository_url: $GITHUB_SERVER_URL/$GITHUB_REPOSITORY
          token: ${{ secrets.ZENODO_TOKEN }}
```

## Arguments:
- `repository_url`: string
  - URL of the repository to upload
  - if the action is used in the repository to upload, `$GITHUB_SERVER_URL/$GITHUB_REPOSITORY` can be used
  
- `token`: `${{ secrets.ZENODO_TOKEN }}` or `${{ secrets.SANDBOX_ZENODO_TOKEN }}` (if you want to use `sandbox: True` option)
  - [get a TOKEN from Zenodo](https://zenodo.org/account/settings/applications/tokens/new/) and add it to your [GitHub Secrets](https://docs.github.com/en/actions/reference/encrypted-secrets) under the name `ZENODO_TOKEN`

### Optional
- `sandbox`: `True` or `False` (default)
  - to use the Zenodo sandbox (for tests purposes)

- `release`: string
  - tag to use for the upload (optional)
  - by default, the latest release will be used. If there are no release yet, the main branch will be used.
