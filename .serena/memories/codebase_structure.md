# Codebase Structure

## Overview
The project follows a modular architecture with clear separation of concerns. The main entry point is `src/main.ts` which extends Obsidian's Plugin class.

## Core Architecture
```
src/
├── main.ts                 # Plugin entry point and lifecycle management
├── constants.ts           # Application constants and view types
├── ApplyView.tsx          # Apply suggestions view component
├── ChatView.tsx           # Main chat interface component
│
├── components/            # React UI components
│   ├── chat-view/         # Chat interface components
│   ├── settings/          # Settings panel components
│   ├── modals/            # Modal dialogs
│   └── common/            # Shared UI components
│
├── contexts/              # React Context providers
│   ├── settings-context.tsx
│   ├── chat-view-context.tsx
│   ├── mcp-context.tsx
│   └── database-context.tsx
│
├── core/                  # Core business logic
│   ├── llm/               # Language model integrations
│   ├── mcp/               # Model Context Protocol
│   └── rag/               # Retrieval-Augmented Generation
│
├── database/              # Database management
│   ├── schema.ts          # Database schema definitions
│   ├── DatabaseManager.ts # Main database interface
│   ├── migrations.json    # Compiled migration files
│   └── modules/           # Database modules (vector, template)
│
├── settings/              # Settings and configuration
│   ├── SettingTab.tsx     # Settings UI
│   └── schema/            # Settings schema and validation
│
├── types/                 # TypeScript type definitions
│   ├── llm/               # LLM-related types
│   ├── chat.ts            # Chat functionality types
│   └── provider.types.ts  # Provider configuration types
│
├── utils/                 # Utility functions
│   ├── llm/               # LLM utilities (tokens, pricing, etc.)
│   ├── chat/              # Chat utilities (parsing, generation)
│   ├── obsidian.ts        # Obsidian-specific utilities
│   └── common/            # General utility functions
│
└── hooks/                 # Custom React hooks
```

## Key Components

### Main Plugin (`main.ts`)
- Extends Obsidian's `Plugin` class
- Manages plugin lifecycle (load/unload)
- Registers views, commands, and settings
- Coordinates database, RAG engine, and MCP manager
- Handles settings management and validation

### Views
- **ChatView**: Main chat interface with message history
- **ApplyView**: Shows and applies AI suggestions
- Both are Obsidian workspace leaf views

### Core Systems
- **LLM Manager**: Handles multiple AI provider integrations
- **MCP Manager**: Manages Model Context Protocol connections
- **RAG Engine**: Retrieval-Augmented Generation for vault search
- **Database Manager**: PGlite-based database with JSON fallback

### Database Architecture
- **PGlite**: PostgreSQL implementation for browser
- **Drizzle ORM**: Type-safe database operations
- **Migration System**: Version-controlled schema changes
- **Multiple Storage**: Vector embeddings, chat history, templates

### Settings System
- **Schema-based**: TypeScript schema validation
- **Migration Support**: Version upgrades with data migration
- **Provider Configuration**: Multiple AI provider settings
- **UI Integration**: React-based settings interface

## Development Patterns

### React Integration
- Functional components with hooks
- Context providers for state management
- Custom hooks for complex logic
- Lexical editor for rich text input

### TypeScript Usage
- Strict type checking enabled
- Interface-based type definitions
- Generic types for reusable components
- Type-safe database operations

### Error Handling
- Custom exception classes
- Obsidian Notice API for user feedback
- Graceful degradation for optional features
- Comprehensive logging for debugging

### Performance Considerations
- Lazy loading for heavy components
- Debouncing for search operations
- Efficient database queries
- Memory management for long sessions

## Testing Structure
- Jest framework with TypeScript support
- Unit tests for utilities and core logic
- Mock implementations for Obsidian API
- Test files co-located with source files

## Build System
- esbuild for fast compilation
- Development mode with hot reloading
- Production builds with optimization
- Source maps for debugging