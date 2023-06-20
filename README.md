# Using `auth.json` for Private Themes and Plugins on GitHub with Composer

This guide will walk you through the process of setting up an `auth.json` file to install private themes and plugins hosted on GitHub using Composer. This method is applicable when you want to use commercial or proprietary themes and plugins that are not publicly available.

## Prerequisites

Before you begin, ensure that you have the following:

- A GitHub account
- Composer installed on your system ([Composer Installation Guide](https://getcomposer.org/doc/00-intro.md#installation-linux-unix-macos))
- Access to the private repository containing the theme or plugin

## Steps

Follow the steps below to set up your `auth.json` file and install the private theme or plugin using Composer:

### 1. Generate a Personal Access Token on GitHub

- Visit the [GitHub Personal Access Tokens](https://github.com/settings/tokens) page while logged into your GitHub account.
- Click on "Generate new token."
- Provide a suitable token description.
- Under "scopes," make sure the "repo" scope is selected.
- Click "Generate token" at the bottom of the page.
- GitHub will generate a personal access token. Keep this token handy as you'll need it in the next step.

> If you use the new Fine-grained personal access tokens, use Repository access, and and choose Contents: read only for Permissions

### 2. Create or Update the `auth.json` File

- In your project's root directory, create a new file named `auth.json`.
- If you already have an existing `auth.json` file, you can update it with the following configuration:

  ```json
  {
    "github-oauth": {
      "github.com": "<YOUR_PERSONAL_ACCESS_TOKEN>"
    }
  }
  ```

  Replace `<YOUR_PERSONAL_ACCESS_TOKEN>` with the personal access token you generated in the previous step.

### 3. Update Your `composer.json` File

- Open your project's `composer.json` file.
- Add or update the `"repositories"` section to include the private repository. Here's an example:

  ```json
  "repositories": [
    {
      "type": "composer",
      "url": "https://wpackagist.org"
    },
    {
      "type": "vcs",
      "url": "https://github.com/<GITHUB_USERNAME>/<REPO_NAME>"
    }
  ]
  ```

  Replace `<GITHUB_USERNAME>` with the GitHub username of the repository owner, and `<REPO_NAME>` with the name of the private repository.

- Under the `"require"` section, add the package entry for the private theme or plugin you want to install. For example:

  ```json
  "require": {
    "wpackagist-plugin/woocommerce": "^5.5",
    "wpackagist-theme/twentytwenty": "^1.9",
    "<GITHUB_USERNAME>/<REPO_NAME>": "^1.0"
  }
  ```

  Replace `<GITHUB_USERNAME>` with the GitHub username of the repository owner, and `<REPO_NAME>` with the name of the private repository.

### 4. Install the Theme or Plugin via Composer

- Open your terminal or command prompt.
- Navigate to your project's root directory.
- Run the following Composer command:

  ```bash
  composer install
  ```

  Composer will read the `auth.json` file, authenticate with GitHub using your personal access token, and install the packages defined in the `composer.json` file, including the private theme or plugin.

### 5. Use the Installed Theme or Plugin

- Once the installation is complete, you can start using the installed theme or plugin within your project.
- Make sure to follow any additional instructions provided by the theme or plugin's documentation or the repository owner.

## Conclusion

By following these

 steps, you should now have successfully set up the `auth.json` file and installed private themes and plugins hosted on GitHub using Composer. You can leverage this method to integrate proprietary or commercial themes and plugins into your projects seamlessly. Remember to keep your `auth.json` file secure and not share it with anyone, as it contains your personal access token.
