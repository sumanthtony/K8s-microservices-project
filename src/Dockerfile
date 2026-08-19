# Stage 1: Build using Debian-based SDK (glibc required by protoc)
FROM mcr.microsoft.com/dotnet/sdk:8.0 AS builder
WORKDIR /app

# Copy project file & restore
COPY src/cartservice.csproj ./src/
RUN dotnet restore ./src/cartservice.csproj -r linux-musl-x64

# Copy source and publish self-contained musl binary
COPY src/ ./src/
WORKDIR /app/src
RUN dotnet publish cartservice.csproj \
    -p:PublishSingleFile=true \
    -r linux-musl-x64 \
    --self-contained true \
    -p:PublishTrimmed=True \
    -p:TrimMode=Link \
    -c release \
    -o /cartservice \
    --no-restore

# Stage 2: Minimal Alpine Runtime
FROM mcr.microsoft.com/dotnet/runtime-deps:8.0-alpine AS runtime
WORKDIR /app

# Download statically compiled grpc_health_probe
ENV GRPC_HEALTH_PROBE_VERSION=v0.4.19
RUN wget -qO /bin/grpc_health_probe https://github.com/grpc-ecosystem/grpc-health-probe/releases/download/${GRPC_HEALTH_PROBE_VERSION}/grpc_health_probe-linux-amd64 \
    && chmod +x /bin/grpc_health_probe

# Copy published binary from builder
COPY --from=builder /cartservice .

ENV DOTNET_EnableDiagnostics=0 \
    ASPNETCORE_URLS=http://*:7070 \
    LISTEN_PORT=7070

EXPOSE 7070
USER 1000

ENTRYPOINT ["/app/cartservice"]
