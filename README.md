<div align="center">
    <a href="#" target="_blank">
        <img src="https://raw.githubusercontent.com/appcypher/gigamono-assets/main/avatar-gigamono-boxed.png" alt="Gigamono Logo" width="140" height="140"></img>
    </a>
</div>

<h1 align="center">Gigamono</h1>

`Gigamono` is a secure multi-tenant serverless framework for building workspaces that can host any number of web apps. Although Gigamono comes bundled with some development and productivity apps, the framework itself is unopinionated on what kind of functionality you want out of your workspace.

Workspaces are great for isolation but they are not enough to deal with privilege escalation issues that come from running third-party modules. The capability-based security system built into the framework means that each running module would require the permission of an admin to access sensitive system resources, and the nice thing is that this applies to frontend apps and extensions running in your UI as well.

##

### Content

1. [Getting Started](#getting-started)

##

### Getting Started <a name="getting-started" />

- Clone repository with recursive flag to grab submodules

    ```
    git clone https://github.com/gigamono/gigamono --recursive
    ```

- Start docker compose

    ```bash
    docker-compose --env-file ./sample.env -f docker/compose/compose.yaml up
    ```
