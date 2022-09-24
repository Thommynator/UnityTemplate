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
  * `BUTLER_CREDENTIALS`: The API key of the [itch.io](https://itch.io/) CLI "Butler"
  * `PROJECT_NAME`: The name of the itch.io project page 

## Unity License
The `UNITY_LICENSE` secret requires the content of a Unity license file.
1. [Manually run](https://docs.github.com/en/actions/managing-workflow-runs/manually-running-a-workflow) the `Acquire activation file` workflow in the GitHub Actions
1. Download the manual activation file that now appeared as an artifact and extract the `Unity_v20XX.X.XXXX.alf` file from the zip.
1. Visit [license.unity3d.com](https://license.unity3d.com/manual) and upload the Unity_v20XX.X.XXXX.alf file. You should now receive your license file (Unity_v20XX.x.ulf) as a download. It's ok if the numbers don't match your Unity version exactly
1. Open `Github` > `<Your repository>` > `Settings` > `Secrets` > `Actions` 
1. Add the full content of the license file as `UNITY_LICENSE` secret

## Versioning
Every change on the master branch will trigger the workflows. 
Each build will receive its unique semantic version, 1.2.3.
The patch version (3rd digit) is increased automatically.
Use a Git tag (attached to the commit) to change the major or minor version.
The itch.io CLI "Butler" will automatically update the corresponding versions on the website.
