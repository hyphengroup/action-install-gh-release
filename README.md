# `install-gh-release` GitHub Action

This repository contains an action for use with GitHub Actions, which will install any GitHub release into your action environment:

This is especially useful when installing arbitrary Go binaries. It can lookup the latest version, or download a specific tag.

only assets with `tar.gz` or `zip` extension are downloaded and `extractTar` is called on either.

For sops, use `mdgreenwald/mozilla-sops-action@v1.1.0`

## Usage

```yaml
- name: Install go-task
  uses: hyphengroup/action-install-gh-release@v1.3.0
  with: # Grab the latest version
    repo: go-task/task
- name: Install tf2pulumi
  uses: hyphengroup/action-install-gh-release@v1.3.0
  with: # Grab a specific tag
    repo: pulumi/tf2pulumi
    tag: v0.7.0
- name: Install private-binary
  uses: hyphengroup/action-install-gh-release@v1.3.0
  with: # Grab a specific tag
    repo: hyphengroup/private-repo
    tag: v0.1.0
    token: ${{ secret.OTHER_GITHUB_TOKEN }}
- name: Install private-binary
  uses: hyphengroup/action-install-gh-release@v1.3.0
  with: # Grab a specific tag
    repo: hyphengroup/private-repo
    tag: v0.1.0
    extractArgs: |
      xz
      --strip-components
      1
    token: ${{ secret.OTHER_GITHUB_TOKEN }}
```
