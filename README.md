# [TI UI App Template](https://github.com/trilogy-group/tiui-app)

Generated from [TI UI Workspace Generator](https://github.com/trilogy-group/tiui-workspace-generator)

### If you've just created this repo for the first time, you need to follow all the instructions in the [Bootstrapping Guide](./BOOTSTRAP.md)

This guide will help you setup your app and deployment.

Check out this [Video for Bootstrapping Guide](https://drive.google.com/file/d/1cSFtYUblQcHo_ScFEkPbYqqj7-F5MO4_/view?usp=sharing) (7 mins)

## Reference

You can find a sample app created here for reference:
https://github.com/trilogy-group/gfi-admin-console

## Linting and Formatting

The newly created bit workspace comes with a linter and formatter.

You can run lint in two modes - lint and lint:quiet (disable reporting on warnings)

```shell
pnpm lint
```

```shell
pnpm lint:quiet
```

You can run format in two modes - format and format:check

```shell
pnpm format
```

```shell
pnpm format:check
```

The linter and formatter are versioned and is pointing to latest. So, any time there is a central update to these versions, bit install should automatically update the linter and formatter.
