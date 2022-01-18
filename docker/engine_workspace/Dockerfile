# Copyright 2022 the Gigamono authors. All rights reserved. Apache 2.0 license.

######################################
## Server Builder
######################################

# Start from a Rust image.
FROM rust:latest as server_builder

# Enter working directory.
WORKDIR /apps

# Copy files over to working dir.
COPY ./utilities ./utilities
COPY ./engine_workspace ./engine_workspace

# Enter `engine_workspace`.
WORKDIR /apps/engine_workspace

# Build project.
RUN cargo build --target x86_64-unknown-linux-gnu --release

# Strip symbols.
RUN strip ./target/x86_64-unknown-linux-gnu/release/workspace_server

######################################
## UI Build
######################################

FROM node:latest as ui_builder

# Enter working directory.
WORKDIR /apps/web_ui

# Copy files over to working dir.
COPY ./web_ui ./

# Install dependencies.
RUN npm install

# Build app
RUN npm run build

######################################
## Final Image
######################################

# Start with base debian.
FROM debian:buster-slim

# Enter working directory.
WORKDIR /apps

# Copy just the app executable into workdir.
COPY --from=ui_builder /apps/web_ui/build ./web_ui/build

WORKDIR /apps/engine_workspace

# Copy the app executable into workdir.
COPY --from=server_builder \
    /apps/engine_workspace/target/x86_64-unknown-linux-gnu/release/workspace_server \
    ./

# Run binary
CMD [ "./workspace_server" ]

