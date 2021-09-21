# ossr-new-deposit

GitHub action to upload a new record into the ESCAPE Open-source Software and Service Repository

To use, add the following to your github action file (e.g. `.github/workflows/ossr.yml`):

```

on:
  push:
    tags:
      *

jobs:
  ossr_new_entry:
    runs-on: ubuntu-latest
    name: A job to upload a new record in the OSSR
    steps:
      - uses: escape2020/ossr-new-depositn@main
        with:
          repository_url: $GITHUB_SERVER_URL/$GITHUB_REPOSITORY
          token: ${{ secrets.SANDBOX_ZENODO_TOKEN }}
```

options:
- `sandbox`: `True` or `False` (default)
  - to use the Zenodo sandbox (for tests purposes)

- `release`: string
  - tag to use for the upload (optional)
  - by default, the latest release will be used. If there are no release yet, the main branch will be used.
