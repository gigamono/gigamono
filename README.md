<div align="center">
    <a href="#" target="_blank">
        <img src="https://raw.githubusercontent.com/appcypher/gigamono-assets/main/avatar-gigamono-boxed.png" alt="Gigamono Logo" width="140" height="140"></img>
    </a>
</div>

<h1 align="center">Gigamono</h1>

`Gigamono` is a secure multi-tenant serverless framework for building workspaces that can host any number of web apps. Although Gigamono comes with productivity and development "subapps", the framework itself is unopinionated on what kind of functionality you want out of your workspace.

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
