# Tagging and Releases

## GIt

To create a tag on the current branch:

`git tag v1.2.0`

And for a tag with annotations:

`git tag v1.2.0 -a`

To push a tag to a remote repository:

`git push origin --tags`

This can then be used to create **releases** on Github.

## CI / CD (GH Actions)

Can use: https://github.com/actions/create-release

Based on the example from the above link...

```YAML
on:
  push:
    tags:
      - 'v*'

name: Create Release After Deployment

jobs:
  post-deploy:
    name: Create Release
    runs-on: ubuntu-latest
    steps:
		# Download Artifact or Checkout
      - name: Create Release
        uses: actions/create-release@v1
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}
        with:
          tag_name: ${{ github.ref }}
          release_name: ${{ github.ref }}
          body: |
            Changes in this Release
            - First Change
            - Second Change
          draft: false
          prerelease: false
```
