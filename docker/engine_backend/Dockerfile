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

ENV RUSTFLAGS="-C target-feature=+crt-static"

# Build project.
RUN cargo build --target x86_64-unknown-linux-gnu --release

# Strip symbols.
RUN strip ./target/x86_64-unknown-linux-gnu/release/backend_server

######################################
## Final Image
######################################

# Start with base alpine.
FROM alpine:latest

# Enter working directory.
WORKDIR /apps

# Copy just the app executable into workdir.
COPY --from=builder \
    /apps/engine_backend/target/x86_64-unknown-linux-gnu/release/backend_server \
    ./

# Run binary
CMD [ "./backend_server" ]

