# Start from a slim Rust image.
FROM rust:latest

# Enter working directory.
WORKDIR /app

# Copy files over to working dir.
COPY ./deno ./deno
COPY ./utilities ./utilities
COPY ./engine-api ./engine-api

# Enter `engine-api`.
WORKDIR /app/engine-api

# Build project.
RUN cargo install --path .

# Run binary
ENTRYPOINT [ "./target/release/server" ]
