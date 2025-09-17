# Tallgrass

A prairie-inspired privacy overlay network designed for adversarial anonymity.

Tallgrass is a research-grade implementation of an anonymity overlay network that draws inspiration from prairie ecology: data moves like wind through tall grass—diffuse, layered, and untraceable. The system emphasizes metadata resistance against powerful network observers, compromised relays, and traffic analysis adversaries.

## Status

**Phase 1: Research & Prototyping Foundation** - ✅ **COMPLETE**

- [x] Core transport layer with privacy hardening
- [x] Network simulator framework
- [x] CLI interface for testing
- [x] Basic anonymity metrics

Next: Phase 2 - Core Protocol Implementation (overlay routing, key management)

## Quick Start

### Prerequisites

- Rust 1.70+ (`curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh`)

### Building

```bash
git clone https://github.com/geeknik/tallgrass.git
cd tallgrass
cargo build --release
```

### Running Simulations

Start a basic anonymity network simulation:

```bash
# Start simulation with 3 relays and 5 clients for 30 seconds
cargo run simulate --relays 3 --clients 5 --duration 30
```

### Manual Testing

**Terminal 1 - Start Relay:**
```bash
cargo run relay --port 12345
```

**Terminal 2 - Connect Client:**
```bash
cargo run client --relay-addr 127.0.0.1:12345 --message "safe communication"
```

## Architecture Overview

### Privacy Features

- **Wire Image Minimization**: No persistent observable identifiers
- **Randomized Timing**: Connection delays break correlation analysis
- **Dynamic Padding**: Variable message sizes obscure traffic patterns
- **Ephemeral Connections**: Timeout-based link management

### Components

- **Transport Layer**: TCP-based with privacy enhancements
- **Network Simulator**: Multi-party anonymity testing framework
- **Metrics Engine**: Anonymity set and performance evaluation
- **CLI Interface**: Research and debugging tools

## Development

### Testing

Run the test suite:

```bash
cargo test
```

### Architecture

```
src/
├── main.rs           # CLI entry point
├── transport.rs      # Privacy-enhanced TCP transport
└── simulator.rs      # Network simulation and metrics
```

### Next Development Tasks

**Phase 2 Priorities:**
- Hybrid onion-routing with timed mixlets
- Ephemeral key generation and forward secrecy
- Distributed directory mechanisms
- Red team evaluation framework

## Design Principles

Tallgrass is built on security-by-design principles:

- Assume powerful, global passive adversaries
- Assume some relays are compromised
- Minimize metadata leakage and correlation surface
- Research-grade implementation for threat modeling

See [DESIGN.md](DESIGN.md) for complete technical specifications.

## Contributing

This is a research project focused on privacy engineering:

1. Study the threat model in [DESIGN.md](DESIGN.md)
2. Implement components following the TODO roadmap
3. Maintain >80% test coverage for security-critical code
4. Document findings in [CHANGELOG.md](CHANGELOG.md)

## License

MIT

## Disclaimer

Tallgrass is experimental research software. It is not intended for production use or to protect against nation-state adversaries at this stage.
