# Bootstrapping Guide

Open this workspace in vscode desktop (DevSpaces) and follow the next set of instructions if you've just initialized the workspace.

![Open in vscode desktop](https://tiui-image-assets.s3.amazonaws.com/images/open-vscode-desktop.png)

## Updating your workspace

As new features get released in tiui-app, you can update your workspace with the following command.
After bootstrapping, run this at least once so that your CICD actions are in place.

```bash
bit update-wkspc
```

This will create github workflow files which DevSpaces may not allow you to directly commit because it uses a generated token. You can manually add these files using the GitHub UI directly. Files created include:

- Tags components, deploys app, exports to bit server
```
.github/workflows/bit-publish.yml
```

- Checks the status of bit, build, lint, format, and test
```
.github/workflows/health-check.yml
```

- Health check status for newly raised PRs
```
.github/workflows/pr-status.yml
```

## Adding the app runner

To add the app runner to your workspace, run the following command:

```bash
bit create tiui-app apps/<app-name>
```

Example:

```bash
bit create tiui-app apps/gfi
```

You need to compile your app before you can run it. Run install as well in case your dependencies haven't been installed.

```bash
bit install && bit compile
```

## Using the app runner

Before you run the app, you must allow bit to use it:

```bash
bit use apps/<app-name>
```

Example:

```bash
bit use apps/gfi
```

Check if your app is listed:

```bash
bit app list
```

To run the app,

```bash
bit run <app-name>
```

Example:

```bash
bit run gfi-app
```

You can now open your app in the browser at [http://localhost:3000](http://localhost:3000)

You can now see your app which contains two routes:

- Home Page
  ![Home Page](https://tiui-image-assets.s3.amazonaws.com/images/home.png)

- Login Page
  ![Login Page](https://tiui-image-assets.s3.amazonaws.com/images/login.png)

## Soft Tagging

In order to publish your app, you must tag it. The CICD will take care of all of this for you. Tagging your app, deploying it to S3 and exporting components to bit server.

As a developer you are required to soft tag your component to indicate to CICD that it is ready to be published.

You can see which components are pending to be tagged using the command:
```shell
bit status
```

Example:

```shell
bit tag --all --soft -m "feature: initial app deployment"
```

Commit your changes to git and wait for some CICD magic.

You should see that CICD would have updated the bitmap on your behalf.

![Bitmap Update](https://tiui-image-assets.s3.amazonaws.com/images/bitmap-update.png)

It has also synced your distribution files to S3.

![S3 Console](https://tiui-image-assets.s3.amazonaws.com/images/s3-console.png)

The S3 bucket is also configured for public static hosting.

![Static Hosting](https://tiui-image-assets.s3.amazonaws.com/images/static-hosting.png)
