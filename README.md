# Using `auth.json` for Private Repository on GitHub to Install Theme via Composer

This guide will walk you through the process of setting up an `auth.json` file to install a private theme repository hosted on GitHub using Composer. This is a common scenario when you want to use a commercial or proprietary theme that is not publicly available.

## Prerequisites

Before you begin, ensure that you have the following:

- A GitHub account
- Composer installed on your system ([Composer Installation Guide](https://getcomposer.org/doc/00-intro.md#installation-linux-unix-macos))
- Access to the private repository containing the theme

## Steps

Follow the steps below to set up your `auth.json` file and install the theme using Composer:

### 1. Generate a Personal Access Token on GitHub

- Visit the [GitHub Personal Access Tokens](https://github.com/settings/tokens) page while logged into your GitHub account.
- Click on "Generate new token."
- Provide a suitable token description.
- Under "scopes," make sure the "repo" scope is selected.
- Click "Generate token" at the bottom of the page.
- GitHub will generate a personal access token. Keep this token handy as you'll need it in the next step.

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

### 3. Install the Theme via Composer

- Open your terminal or command prompt.
- Navigate to your project's root directory.
- Run the following Composer command:

  ```bash
  composer require <GITHUB_USERNAME>/<REPO_NAME>:<TAG_OR_BRANCH>
  ```

  Replace `<GITHUB_USERNAME>` with the GitHub username of the repository owner, `<REPO_NAME>` with the repository name, and `<TAG_OR_BRANCH>` with the desired tag or branch of the theme to install.

- Composer will use the `auth.json` file to authenticate and download the theme package from the private repository.

### 4. Use the Installed Theme

- Once the installation is complete, you can start using the installed theme within your project.
- Make sure to follow any additional instructions provided by the theme's documentation or the repository owner.

## Conclusion

By following these steps, you should now have successfully set up the `auth.json` file and installed a private theme repository hosted on GitHub using Composer. You can leverage this method to integrate proprietary or commercial themes into your projects easily. Remember to keep your `auth.json` file secure and not share it with anyone, as it contains your personal access token.
