# Update deployment_caller.yml workflow file

## 📄 Overview

The ./.github/workflows/deployment_caller.yml file contains the GitHub action to deploy code changes when [a new commit is pushed to the remote ‘dev’ and 'uat' branches on GitHub](https://docs.github.com/en/get-started/using-git/pushing-commits-to-a-remote-repository), and also when a release is published on GitHub.

For more info, please reference [the Github documentation](https://docs.github.com/en/actions/use-cases-and-examples/deploying/deploying-with-github-actions#triggering-your-deployment) and the [FTP-Deploy-Action docs](https://github.com/SamKirkland/FTP-Deploy-Action) to understand more about the process involved in deploying changes to dev.

## ✔️ Actions for You

1. Create a new branch from the `main` branch called `deployment-workflows`

2. Update the `./.github/workflows/deployment_caller.yml` file to include your site's `dev` server and server directory eg

```yml
dev_server: DEV1
dev_server_dir: /boilerplate_dev_cogplatform_co_uk/
```

3. Update the `./.github/workflows/deployment_caller.yml` file to include your site's `uat` server and server directory eg


```yml
uat_server: WEB1
uat_server_dir: /COGBoilerplate_uat/
```

4. ⚠️ Make sure the 'on release trigger', and live server details, remain set to the default boilerplate values.  **This is important as we don't want to accidentally deploy changes to the live server when we are in the process of building a new site.** These values can be changed over later as the first of the post-live tasks.

**Example 'on release trigger' commented out by default (leave like this)**

```yml
# release:
#   types:
#     - published
```

**Example 'on release trigger' commented out by default (leave like this)**

```yml
live_server: WEB1
live_server_dir: /TOSET/
```

5. commit your changes, and create a pull request to merge those changes back into main branch.


### 📋 Notes

- When setting the server directory, ensure that the directory name is correct. You should be able to find the correct directory by checking bluebook.

- Ensure that all letter characters in the server value are uppercase.

#### ❌ Bad

```yml
uat_server: web1
```


#### ✅ Good

```yml
uat_server: WEB1
```

- Ensure that the server directory is enclosed in forward slashes `/` and does not contain any trailing slashes.

#### ❌ Bad

```yml
uat_server_dir: COGBoilerplate_uat
```


#### ✅ Good

```yml
uat_server_dir: /OGBoilerplate_uat/
```
