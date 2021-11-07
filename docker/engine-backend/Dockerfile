# Start from a slim Rust image.
FROM rust:latest

# Enter working directory.
WORKDIR /app

# Copy files over to working dir.
COPY ./deno ./deno
COPY ./utilities ./utilities
COPY ./secure-runtime ./secure-runtime
COPY ./engine-backend ./engine-backend

# Enter `engine-backend`.
WORKDIR /app/engine-backend

# Build project.
RUN cargo install --path .

# Run binary
ENTRYPOINT [ "./target/release/server" ]
