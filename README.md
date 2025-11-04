# Technical Writer Assessment: Using a docs-as-code approach to submit your writing sample

## Overview

We use a docs-as-code approach to manage our documentation. The project relies on Git, Markdown and Docusaurus to create and maintain the site.

This repository contains a sample site built with these tools. You can view the built site at https://philstollery.github.io/github-usaurus.

Please can you do the following:

1. Clone this repository to your machine, then push it to a private repository under your GitHub account.
2. Complete the setup to deploy the website to GitHub Pages.
3. Write a how-to tutorial using our template that:
    - Explains how to deploy a Docusaurus website to GitHub Pages.
    - Uses step-by-step instructions and screenshots so a non-technical user can follow along. You may use content from this `README.md` as a reference.
    - Follows the structure in our tutorial template: https://philstollery.github.io/github-usaurus/docs/templates/template-tutorial
    - Follows the style guide: https://philstollery.github.io/github-usaurus/docs/templates/style-guide
    - Please don't spend more than 45 minutes on the writing task.
4. Publish your changes to your personal repository, and give **PhilStollery** access to your hosted GitHub Pages site and the updated repo.

Below are the steps to set up the project locally and deploy it to GitHub Pages.

## Prerequisites

Before you begin, ensure you have the following:

- Node.js (version 14 or higher)
- The Yarn package manager
- A free GitHub account
- Git configured locally, so you can pull and push to GitHub

## Installation

After you clone this repository, navigate to the project directory and install dependencies:

```bash
yarn
```

## Local development

Start the local development server:

```bash
yarn start
```

This opens a browser window and serves the site locally. Most changes appear live, so you can preview your edits before building and deploying.

## Deployment

You need a GitHub personal access token. See GitHub's guide for creating one: https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/managing-your-personal-access-tokens#creating-a-personal-access-token-classic

Grant the token `write:packages` and `read:packages` scopes.

1. Set the `NPM_GITHUB_AUTH_TOKEN` environment variable to your personal access token (example in zsh/bash):

    ```bash
    export NPM_GITHUB_AUTH_TOKEN="YOUR_PERSONAL_ACCESS_TOKEN"
    ```

2. Set the `GIT_USER` environment variable to your GitHub username:

    ```bash
    export GIT_USER="your-github-username"
    ```

3. If a `gh-pages` branch does not already exist, create it and push it to GitHub:

    ```bash
    git checkout -b gh-pages
    git add .
    git commit -m "Create gh-pages branch"
    git push -u origin gh-pages
    ```

4. Edit the `docusaurus.config.ts` file to set `url` and `baseUrl` for your GitHub Pages site. For a repository named `github-usaurus` under the user `philstollery`, the relevant settings are:

    ```ts
    // Set the production url of your site here
    url: 'https://philstollery.github.io',
    // Set the /<baseUrl>/ pathname under which your site is served
    // For GitHub Pages deployment, it is often '/<projectName>/'
    baseUrl: '/github-usaurus/',

    // GitHub Pages deployment config. If you aren't using GitHub Pages, you don't need these.
    organizationName: 'philstollery', // your GitHub org/user name
    projectName: 'github-usaurus', // your repo name
    ```

Change `url`, `baseUrl`, `organizationName` and `projectName` to match your GitHub username and repository name.

5. Run the deployment command:

    ```bash
    yarn deploy
    ```

    `yarn deploy` builds the site and (when configured) pushes the built site to the `gh-pages` branch for GitHub Pages hosting.

6. View your deployed site at: https://your-github-username.github.io/your-repository-name/