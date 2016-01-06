Wercker step ghr [![MIT License](http://img.shields.io/badge/license-MIT-blue.svg?style=flat-square)](https://github.com/tcnksm/wercker-step-ghr/blob/master/LICENCE)
====

[![wercker status](https://app.wercker.com/status/764d2e0c53428ce47dcb3e9f3a2a0f22/s/master "wercker status")](https://app.wercker.com/project/bykey/764d2e0c53428ce47dcb3e9f3a2a0f22)

This is [wercker](http://wercker.com/) deploy step for [tcnksm/ghr](https://github.com/tcnksm/ghr), create [Github Release](https://help.github.com/articles/creating-releases/) and uploading artifacts there. 

## Usage

In the `wercker.yml` of your application use the following step definition:

```yaml
steps:
   - tcnksm/ghr:
       token: $GITHUB_TOKEN
       input: dist
```

To use this step, you need to set `$GITHUB_TOKEN` and `input` directory. About `$GITHUB_TOKEN` see at [Github Token](https://github.com/tcnksm/wercker-step-ghr#github-token) section. `input` directory is where your artifacts you want to upload are in and it would be in `${WERCKER_OUTPUT_DIR}` passed from build step.

## Options

You can control build with some option from `wercker.yml`:

```yaml
steps:
   - tcnksm/ghr:
       token: $GITHUB_TOKEN
       input: dist
       version: v0.1.0         # Relase tag default is `pre-release`
       pre_release: true       # Relase as pre-release default is false
       replace: true           # Replace release if it exists
```

## Example

See [tcnksm-sample/wercker-golang](https://github.com/tcnksm-sample/wercker-golang). This simple golang repository is continuously cross-compiled and relase as `pre-prerelease`, you can always provide new builds to user. 

## GitHub token

To be able to use this step, you will first need to create a GitHub token with an account which has enough permissions to be able to create releases. First goto `Account settings`, then goto `Applications` for the user. Here you can create a token in the `Personal access tokens` section. For a private repository you will need the `repo` scope and for a public repository you will need the `public_repo` scope. Then it is recommended to save this token on wercker as a protected environment variable.


## Author

[tcnksm](https://github.com/tcnksm)
