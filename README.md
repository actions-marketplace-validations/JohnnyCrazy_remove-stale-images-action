# Remove Stale Images

Small action which keeps your image count at a fixed number, removing all old ones. This allows for some space saving if you don't depend on old image tags.

# Example Usage

```yaml
name: 'testing'
on:
  registry_package:
    types: [published, updated]

jobs:
  remove-stale-images: # make sure the action works on a clean machine without building
    runs-on: ubuntu-latest
    steps:
      - uses: johnnycrazy/remove-stale-images-action@v1
        with:
          token: ${{ secrets.GITHUB_TOKEN }}
          packages: test # comma seperated list of your projects/image names
          keep: 5 # Keep the latest 5 tags
```