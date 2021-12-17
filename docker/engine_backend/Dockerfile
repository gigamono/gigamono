# Start from a slim Rust image.
FROM rust:latest

# Enter working directory.
WORKDIR /app

# Copy files over to working dir.
COPY ./utilities ./utilities
COPY ./tera ./tera
COPY ./engine_backend ./engine_backend

# Enter `engine_backend`.
WORKDIR /app/engine_backend

# Copy config file.
COPY ./sample.gigamono.yaml ./

# Build project.
RUN cargo install --path .

# Run binary
ENTRYPOINT [ "./target/release/server" ]
