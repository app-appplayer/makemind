# MCP UI Runtime Documentation

Welcome to the MCP (Model Context Protocol) UI Runtime documentation. This documentation covers the specification, implementation, and usage of the MCP UI DSL (Domain Specific Language) for building dynamic, server-driven user interfaces.

## Documentation Structure

- **[Specification](./specification/)** - MCP UI DSL v1.0 specification and protocol details
- **[API Reference](./api/)** - Complete API documentation for all packages
  - [Widget Reference](./api/widget-reference.md) - Comprehensive widget catalog
  - [Flutter Runtime API](./api/flutter-runtime.md) - Runtime implementation details
- **[Architecture](./architecture/)** - System architecture and design decisions
- **[Guides](./guides/)** - Step-by-step guides for common tasks
  - [Getting Started](./guides/getting-started.md) - Quick start guide
  - [Migration to v1.0](./guides/migration-v1.0.md) - Upgrade from older versions
- **[Examples](./examples/)** - Code examples and sample applications
  - [Counter App](./examples/counter-app.md) - Simple interactive example

## Quick Links

- [Getting Started Guide](./guides/getting-started.md)
- [MCP UI DSL Specification](./specification/MCP_UI_DSL_v1.0_Specification.md)
- [Widget Reference](./api/widget-reference.md)
- [Flutter Runtime API](./api/flutter-runtime.md)
- [Migration Guide v1.0](./guides/migration-v1.0.md)
- [Architecture Overview](./architecture/overview.md)

## Overview

The MCP UI Runtime is a framework for building server-driven user interfaces using a JSON-based domain-specific language. It enables dynamic UI updates without app deployments and supports real-time data synchronization through resource subscriptions.

### Key Features

- **Server-Driven UI**: Define your entire UI in JSON on the server
- **Real-Time Updates**: Subscribe to resources for live data updates
- **Cross-Platform**: Implementations for Flutter, React, and more
- **Type-Safe**: Full TypeScript/Dart type definitions
- **Extensible**: Easy to add custom widgets and actions
- **Rich Widget Set**: Over 40 built-in widgets including charts, tables, and dialogs
- **Advanced Interactions**: Support for drag-and-drop, gestures, and animations

### Core Concepts

1. **Resources**: UI definitions and data stored on MCP servers
2. **Tools**: Server-side functions that can be called from the UI
3. **Subscriptions**: Real-time data updates via resource notifications
4. **State Management**: Built-in state handling with bindings
5. **Navigation**: Multi-page application support with routing

## Package Structure

The MCP UI ecosystem consists of several packages:

- `flutter_mcp_ui_runtime` - Flutter implementation of the runtime
- `flutter_mcp_ui_generator` - Code generation for Flutter widgets
- `flutter_mcp_ui_core` - Core abstractions and interfaces
- `mcp_client` - MCP protocol client implementation
- `mcp_server` - MCP protocol server implementation

## Latest Updates (v1.0)

The MCP UI DSL v1.0 specification brings significant improvements:

- **Unified Layout System**: `column` and `row` widgets are now unified as `linear` with direction
- **Consistent Naming**: Standardized widget types (`text` instead of `label`) and properties
- **New Widgets**: Added 14 new widgets including conditional rendering, advanced inputs, and dialogs
- **Improved Actions**: New action types for batch operations and conditional execution
- **Better Event Handling**: Standardized event names (`click` instead of `onTap`)

For detailed migration instructions, see the [Migration Guide](./guides/migration-v1.0.md).

## Contributing

See [CONTRIBUTING.md](../CONTRIBUTING.md) for guidelines on contributing to this project.

## License

This project is licensed under the MIT License - see the [LICENSE](../LICENSE) file for details.