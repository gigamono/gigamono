# Copyright 2022 the Gigamono authors. All rights reserved. GPL-3.0 License.

######################################
## Builder
######################################

# Start from a Rust image.
FROM rust:latest as builder

# Enter working directory.
WORKDIR /apps

# Copy files over to working dir.
COPY ./utilities ./utilities
COPY ./tera ./tera
COPY ./engine_backend ./engine_backend

# Enter `engine_backend`.
WORKDIR /apps/engine_backend

# Build project.
RUN cargo build --target x86_64-unknown-linux-gnu --release

# Strip symbols.
RUN strip ./target/x86_64-unknown-linux-gnu/release/backend_server

# Copy deno_core scripts to /keep folder.
RUN mkdir --parents /keep && \
    find /usr/local/cargo/registry/src/ -maxdepth 4 -iname "*.js" -exec cp --parents "{}" /keep \;

######################################
## Final Image
######################################

# Start with base debian.
FROM debian:stable-slim

# Enter working directory.
WORKDIR /apps

# Copy deno_core scripts.
COPY --from=builder /keep/usr/local/ /usr/local

# Copy the tera postscripts.
COPY --from=builder \
    /apps/tera/lib/postscripts \
    ./tera/lib/postscripts

# Copy the tera core extensions.
COPY --from=builder \
    /apps/tera/lib/extensions \
    ./tera/lib/extensions

# Update working directory
WORKDIR /apps/engine_backend

# Copy the app executable into workdir.
COPY --from=builder \
    /apps/engine_backend/target/x86_64-unknown-linux-gnu/release/backend_server \
    ./

# Run binary
CMD [ "./backend_server" ]

