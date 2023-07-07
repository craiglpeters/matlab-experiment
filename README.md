# matlab-experiment
Try using the MATLAB docker image in a Codespace by clicking [![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/craiglpeters/matlab-experiment?quickstart=1)

Key attributes of this repo:
1. The [Dev container](https://containers.dev) config defines how the Codespaces environment works in [.devcontainer](https://github.com/craiglpeters/matlab-experiment/tree/main/.devcontainer)
   1. uses the default [universal](https://github.com/devcontainers/images/tree/main/src/universal) image which has LOTS of tools preinstalled so that many things should just work out of the box
   2. specifies a minimum 4 cpu machine since I assume MATLAB requires some horsepower
   3. includes the [`docker-in-docker` feature](https://github.com/devcontainers/features/tree/main/src/docker-in-docker) to ensure that you can run the MATLAB docker container within the containerized dev environment
     (Note: this is not strictly neccessary as the univeral image includes docker-in-docker, but other base images do not, so I included it here to put emphasis on the capability of [dev container features](https://containers.dev/features))
   4. does the docker pull in the [`updateContentCommand`](https://containers.dev/implementors/json_reference/#lifecycle-scripts) so that the container is pulled during the [Codespaces Prebuild](https://docs.github.com/en/codespaces/prebuilding-your-codespaces/about-github-codespaces-prebuilds)
   5. executes `docker run` in the `postAttachCommand` to put the process into a foreground terminal session
   6. loads the [MathWorks MATLAB language VS Code extension from the VS Code Marketplace](https://marketplace.visualstudio.com/items?itemName=MathWorks.language-matlab) so users have the best experience coding MATLAB without having to install the extension manually
2. The repository is configured as a [Codespaces Template Repository](https://docs.github.com/en/codespaces/setting-up-your-project-for-codespaces/setting-up-your-repository/setting-up-a-template-repository-for-github-codespaces) which makes it easy for users to start a codespace from it
3. I created the badge by [creating a deep link to the repository](https://docs.github.com/en/codespaces/setting-up-your-project-for-codespaces/setting-up-your-repository/facilitating-quick-creation-and-resumption-of-codespaces#configuring-more-options) and chose the 'Quick Start' option
