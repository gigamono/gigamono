# Start from a slim Rust image.
FROM rust:latest

# Enter working directory.
WORKDIR /app

# Copy files over to working dir.
COPY ./utilities ./utilities
COPY ./engine_proxy ./engine_proxy

# Enter `engine_proxy`.
WORKDIR /app/engine_proxy

# Copy config file.
COPY ./sample.gigamono.yaml ./

# Build project.
RUN cargo install --path .

# Run binary
ENTRYPOINT [ "RUST_LOG=debug target/release/proxy_server" ]
