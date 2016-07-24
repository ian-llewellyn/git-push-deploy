# git-push-deploy

Based on [How To Use Git to Manage your User Configuration Files on a Linux VPS: DigitalOcean](https://www.digitalocean.com/community/tutorials/how-to-use-git-hooks-to-automate-development-and-deployment-tasks) - thanks Justin! This script requires bash v4 on the deployment server.

## Instructions for use
* Create a `git init --bare` repo somewhere on your web server.
* Add `post-receive` and `post-receive.conf` to the hooks directory.
* Modify the `DOC_ROOT` variable in the `.conf` file to suit your needs.
* Push the `master` branch of a project to the bare git repo on your server.
* Hey presto, the site is updated!

## Post-deploy commands
If you have some post deployment commands to run, add them to the `POST_CMD`
variable separated by a newline and/or a semi-colons ';', for example:
```bash
POST_CMD="echo Touching last-mod; touch last-mod'
```

## Multi-branch deployment
You can set a range of locations to be updated by different branches in your
project. Simply add `BRANCH[<name>]=<sub_dir>` to the `.conf` file for each
branch you want to trigger a deploy. **Note:** `sub_dir` is appended to
`DOC_ROOT` when deploying.
