<div align="center">
    <a href="#" target="_blank">
        <img src="https://raw.githubusercontent.com/appcypher/gigamono-assets/main/avatar-gigamono-boxed.png" alt="Gigamono Logo" width="140" height="140"></img>
    </a>
</div>

<h1 align="center">Gigamono</h1>

`Gigamono` is a secure multi-tenant serverless framework for building workspaces that can host any number of web apps. Although Gigamono comes bundled with some development and productivity apps, the framework itself is unopinionated on what kind of functionality you want out of your workspace.

Workspaces are great for isolation but they are not enough to deal with privilege escalation issues that come from running third-party modules. The capability-based security system built into the framework means that each running module would require the permission of an admin to access sensitive system resources, and the nice thing is that this applies to frontend apps and extensions running in your UI as well.

##

<div align="center">
  :warning: Not ready for production use :warning:
</div>

### Content

1. [Getting Started](#getting-started)
2. [Headless Gigamono](#headless-gigamono)

##

### Getting Started <a name="getting-started" />

- Clone repository with recursive flag to grab submodules

  ```bash
  git clone https://github.com/gigamono/gigamono --recursive
  ```

  ```bash
  cd gigamono
  ```

  ```bash
  docker-compose --env-file ./sample.env -f docker/compose/compose.dev.yaml up
  ```

- Test the apis.

  ```bash
  curl "localhost:5050/api/v1/system/apps"
  ```

- Setting up the UI

  ```bash
  cd web_ui
  ```

  ```bash
  npm install && npm run build
  ```

- Visit the page

  ```bash
  open http://127.0.0.1:5050/dashboard
  ```

##

### Headless Gigamono <a name="headless-gigamono" />
