# Unity-Template
A template repo for Unity projects. 
Uses GitHub actions to automatically build, (test) and deploy the project to [itch.io](https://itch.io/).
More details can be found on the [Game CI website](https://game.ci/docs/github/getting-started).

The workflows will build the project for:
* Windows
* MacOS
* HTML5 (WebGL)

## Setup Secrets
Go to `Github` > `<Your repository>` > `Settings` > `Secrets` > `Actions` and add the following **repository secrets**:
* `UNITY_EMAIL`: The email address of your unity account 
* `UNITY_PASSWORD`: The password of your unity account
* `UNITY_LICENSE`: The content of the Unity license file (`*.ulf`), see below 
* `ITCH_USERNAME`: The username of your [itch.io](https://itch.io/) account
* `PROJECT_NAME`: The name of the [itch.io](https://itch.io/) project page 
* `BUTLER_CREDENTIALS`: The [itch.io API key](https://itch.io/user/settings/api-keys) for the "Butler" CLI

## Unity License
The `UNITY_LICENSE` secret requires the content of a Unity license file.
1. [Manually run](https://docs.github.com/en/actions/managing-workflow-runs/manually-running-a-workflow) the `Acquire activation file` workflow in the GitHub Actions
1. Download the manual activation file that now appeared as an artifact and extract the `Unity_v20XX.X.XXXX.alf` file from the zip.
1. Visit [license.unity3d.com](https://license.unity3d.com/manual) and upload the Unity_v20XX.X.XXXX.alf file. You should now receive your license file (Unity_v20XX.x.ulf) as a download. It's ok if the numbers don't match your Unity version exactly
1. Open `Github` > `<Your repository>` > `Settings` > `Secrets` > `Actions` 
1. Add the full content of the license file as `UNITY_LICENSE` secret

## Versioning
<<<<<<< HEAD
* Every change on the master branch will trigger the workflows. 
* Each build will receive its unique semantic version, 1.2.3.
* The patch version (3rd digit) is increased automatically.
* Use a Git tag (attached to the commit) to change the major or minor version.
* The itch.io CLI "Butler" will automatically update the corresponding versions on the website.

## Troubleshooting

#### WebGL start fails
Your WebGL version fails in the browser (e.g. on itch.io) during start-up, with an error message similar to this:

```
Unable to parse Build/<project-name>.framework.js.br! This can happen if build compression was enabled but web server hosting the content was misconfigured to not serve the file with HTTP Response Header "Content-Encoding: br" present. Check browser Console and Devtools Network tab to debug.
```

* Open your game in Unity
* Edit > Project Settings... > Player
* Select the WebGL tab on the right
* Go to Publish Settings
* Compression Format: Disabled

=======
* Every change on the master branch will trigger the workflows 
* Each build will receive its unique semantic version, 1.2.3
* The patch version (3rd digit) is increased automatically
* Use a Git tag (attached to the commit) to change the major or minor version
* The itch.io CLI "Butler" will automatically update the corresponding versions on the website
>>>>>>> bf3b61d3fbfedadd2c8a911e4651e0a0211372b7
