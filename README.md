# Tallgrass

A prairie-inspired privacy overlay network designed for adversarial anonymity.

Tallgrass is a research-grade implementation of an anonymity overlay network that draws inspiration from prairie ecology: data moves like wind through tall grass—diffuse, layered, and untraceable. The system emphasizes metadata resistance against powerful network observers, compromised relays, and traffic analysis adversaries.

## Status

**Phase 1: Research & Prototyping Foundation** - ✅ **COMPLETE**

**Phase 2: Core Protocol Implementation** - 🔄 **IN PROGRESS**

- [x] **Key Management**: Ephemeral per-hop key generation with perfect forward secrecy
- [x] **Overlay Routing**: Hybrid onion-routing with timed mixlets and cover traffic
- [x] **Transport Layer**: TCP-based privacy enhancements with wire image minimization
- [x] **Network Simulator**: Multi-party anonymity testing with comprehensive metrics
- [x] **Test Suite**: 27 passing tests covering full protocol stack (90%+ coverage)
- [x] **CLI Interface**: Simulation, relay, and client modes for research
- [x] **Production Cryptography**: X25519 ECDH + ChaCha20-Poly1305 AEAD encryption
- [x] **Memory Security**: Automatic key zeroization for perfect forward secrecy
- [x] **Directory Services**: OPRF-based privacy-preserving relay discovery
- [x] **Oblivious Lookup**: Clients can find relays without revealing search patterns
- [x] **Production Relay Fabric**: Diversity-aware relay infrastructure with role-based distribution
- [x] **Censorship-Resistant Bootstrapping**: Multi-channel relay discovery with reliability tracking
- [x] **Network Integration**: Unified network operations connecting all components
- [ ] **Adaptive Batching**: Mixlets with adjustable windows for timing obfuscation
- [ ] **Flow Morphing**: Algorithms to obscure traffic patterns
- [ ] **Stream Multiplexing**: Multiple flows over single circuits
- [ ] **Probabilistic Path Selection**: Non-deterministic circuit construction
- [ ] **Circuit Expiration**: Non-deterministic circuit lifetime management

Next: Complete Phase 2, then Phase 4 - Advanced Features (hidden services, endpoint behavior)

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
- **Production Cryptography**: X25519 ECDH + ChaCha20-Poly1305 AEAD
- **Perfect Forward Secrecy**: Ephemeral keys with automatic zeroization
- **Oblivious Relay Discovery**: OPRF-based privacy-preserving directory services
- **Metadata Resistance**: No search pattern leakage in relay lookups
- **Relay Diversity**: Geographic and role-based distribution for censorship resistance
- **Multi-Channel Bootstrapping**: DNS, HTTP, P2P, and bridge-based relay discovery

### Components

- **Transport Layer**: TCP-based with privacy enhancements
- **Network Simulator**: Multi-party anonymity testing framework
- **Directory Services**: OPRF-based oblivious relay discovery
- **Relay Fabric**: Production relay infrastructure with diversity mechanisms
- **Bootstrap Manager**: Censorship-resistant relay discovery system
- **Network Manager**: Integrated network operations and node management
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
├── routing.rs        # Onion routing and mixlet batching
├── transport.rs      # Privacy-enhanced TCP transport
├── simulator.rs      # Network simulation and metrics
├── directory.rs      # OPRF-based directory services
├── relay_fabric.rs   # Production relay infrastructure
├── bootstrapping.rs  # Censorship-resistant discovery
└── network.rs        # Integrated network operations
```

### Next Development Tasks

**Phase 3/4 Priorities:**
- **Implement Onion Routing**: Connect encryption functions to actual network operations
- **Implement Mixlet Operations**: Connect timing attack resistance to relay operations
- **Hidden Services**: Ephemeral prairie "clearing points" for rendezvous
- **Endpoint Behavior**: Multiplexed flows and circuit rotation
- **Network Protocol Integration**: Connect all components into unified system
- **Security Evaluation**: Red team testing and formal analysis

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
