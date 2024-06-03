# release-changelog

Based on [automatic-releases](https://github.com/marvinpinto/actions/blob/master/packages/automatic-releases) with further changelog customizations.  
Requires use of [semantic versioning](https://semver.org/) on tags

> Required NodeJS in GitHub Action >=20

## Usage
```yaml
- name: Set tag name output
  id: vars
  run: echo ::set-output name=tag::${GITHUB_REF#refs/*/}

- name: Create release
  uses: mrwake-dev/release-changelog@v2.0.0
  with:
    token: ${{ secrets.GITHUB_TOKEN }}
    title: 'YOUR APP NAME ${{ steps.vars.outputs.tag }}'
    files: |
      LICENSE
```

## Arguments
```yaml
  token:
    required: true
    description: repository token
  draft:
    required: false
    description: Create a draft release
    default: 'false'
  pre-release:
    required: false
    description: Create a pre-release release
    default: 'false'
  title:
    required: false
    description: Title for release, defaults to the tag name
  files:
    required: false
    description: Files to include in the release
  skip-prereleases:
    required: false
    description: If enabled, when a new non-prerelease tag is pushed, the changelog will be created between the pushed tag, and the last non-prerelease tag
```
