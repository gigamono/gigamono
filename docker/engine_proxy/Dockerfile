######################################
## Builder
######################################

# Start from a Rust image.
FROM rust:latest as builder

# Enter working directory.
WORKDIR /apps

# Copy files over to working dir.
COPY ./utilities ./utilities
COPY ./engine_proxy ./engine_proxy

# Enter `engine_proxy`.
WORKDIR /apps/engine_proxy

ENV RUSTFLAGS="-C target-feature=+crt-static"

# Build project.
RUN cargo build --target x86_64-unknown-linux-gnu --release

# Strip symbols.
RUN strip ./target/x86_64-unknown-linux-gnu/release/proxy_server

######################################
## Final Image
######################################

# Start with base alpine.
FROM alpine:latest

# Enter working directory.
WORKDIR /apps

# Copy just the app executable into workdir.
COPY --from=builder \
    /apps/engine_proxy/target/x86_64-unknown-linux-gnu/release/proxy_server \
    ./

# Run binary
CMD [ "./proxy_server" ]

