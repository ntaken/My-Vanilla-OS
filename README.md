# My-Vanilla-OS

Base is vanilla-os/desktop:main

My daily driver. I know nothing. Inspiration https://github.com/justsaft/Vanilla-Cherry

## Added

- Wireshark and allowing ordinary user to do packet capture.


## Use this custom image

- Edit the configuration file with the command: `abroot config-editor`.
- Change the "name" entry from something like `vanilla-os/desktop` to `ntaken/my-vanilla-os`
- Now, Run `abroot upgrade` to switch to your custom image. (Warning: If you are not allowed to run `abroot upgrade` because of previous operation. You should change back to your standard name and reboot your computer and try the steps again. If you reboot without successfully running `abroot upgrade` you will break booting of Vanilla OS and need to use a live cd to mount root-b or root-a and change back to previous name in `/usr/share/abroot/abroot.json`.)

## Explore

Now, that you are aware of the basics, let's explore the files and directories present in this repository:

- `.github/workflows/vib-build.yml`: This file contains the GitHub Actions workflow to check for updates to the base image and build the Vib image on push and pull requests.
  - It uses the [`vib-gh-action`](https://github.com/Vanilla-OS/vib-gh-action) to build the recipe and upload it as an artifact. The generated artifact is then built using Docker's actions and pushed to GHCR (**Note**: The image with the respective branch tags is published to GHCR only on push actions to the branches in your repository or on tags and not on pull requests).
  - The action runs automatically on a schedule checking updates to the base image using [Differ](https://github.com/Vanilla-OS/Differ).
- `.github/workflows/release.yml`: This file contains the GitHub Actions workflow to automatically create a GitHub release when a tag is created and it uploads the generated Containerfile to the release for future reference.
- `.github/dependabot.yml`: This file contains the configuration for GitHub's Dependabot to check for updates to the GitHub actions used in the workflow files monthly and when it finds a new version it creates a PR in your repository.
- `includes.container`: The files included in this directory are added by default to your image to the specified location (**Note**: It also contains ABRoot's configuration file).
- `modules`: This directory contains the modules that are used to customize the image. You can add your modules to this directory.
- `recipe.yml`: This file contains the recipe for the image. It specifies the base image, modules and other fields to be present in the custom image.
