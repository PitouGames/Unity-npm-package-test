# Test

This is a test of GitHub packages

## Installation

Use Unity 2021.3.4f1 or greater.

 - Make sure you have a GitHub account. GitHub requiers you to authenticate to download a public package.
 - Create a new personal access token : https://github.com/settings/tokens/new. Check only the scope `read:packages (Download packages from GitHub Package Registry)`
 [screenshot]
 - Find or create the `.upmconfig.toml` file (see https://docs.unity3d.com/Manual/upm-config-scoped.html#upmconfigUser). On Windows, it is in `%USERPROFILE%\.upmconfig.toml`.
 - Add the property in it
 ```
[npmAuth."https://npm.pkg.github.com/@pitougames"]
token = "<the new token>"
```
 - Close all Unity instance.
 - Configure the scope registry in your Unity project manifest (`Packages/package.json`) and add package name:

```json
{
    "dependencies": {
        "com.pitou.test": "0.1.0",
        ...
    },
    "scopedRegistries": [
        {
            "name": "Pitou packages",
            "url": "https://npm.pkg.github.com/@pitougames",
            "scopes": [
                "com.pitou"
            ]
        }
    ]
}
```

 - Add auth https://docs.unity3d.com/Manual/upm-config-scoped.html

 - Open your Unity project

Note: when browsing unity package manager, you will have an error:
```
[Package Manager Window] Cannot perform upm operation: Unable to perform online search:
  Request [GET https://npm.pkg.github.com/@pitougames/-/v1/search?text=com.pitou&from=0&size=250] failed with status code [405] [NotFound].
```
This is because GitHub doesn't have an API to get package list. You should ignore this error.
