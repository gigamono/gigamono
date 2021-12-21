# ======= BUILDING WEB APP ======= #
FROM node:latest as web_builder

# Enter working directory.
WORKDIR /app

# Copy files over to working dir.
COPY ./web_ui ./web_ui

# Enter `web_ui`.
WORKDIR /app/web_ui

# Install dependencies.
RUN npm install

# Build app
RUN npm run build

# ======= RUNNING RUST APP ======= #
FROM rust:latest

# Enter working directory.
WORKDIR /app

# Copy files over to working dir.
COPY ./utilities ./utilities
COPY ./engine_workspace ./engine_workspace
COPY --from=web_builder /app/web_ui ./web_ui

# Enter `engine_workspace`.
WORKDIR /app/engine_workspace

# Copy config file.
COPY ./sample.gigamono.yaml ./

# Build project.
RUN cargo install --path .

# Run binary
ENTRYPOINT [ "RUST_LOG=debug target/release/workspace_server" ]
