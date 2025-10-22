# Code Style and Conventions

## TypeScript Configuration
- **Target**: ES6
- **Module**: ESNext
- **Strict Type Checking**: Enabled with strictNullChecks
- **JSX**: React JSX syntax
- **Import Helpers**: Enabled for better tree shaking
- **Isolated Modules**: Enabled for better compilation

## Code Formatting (Prettier)
- **Tab Width**: 2 spaces
- **Use Tabs**: false (spaces only)
- **Semicolons**: false (no semicolons)
- **Quotes**: Single quotes
- **Trailing Commas**: All (including function parameters and arrays)

## Linting (ESLint)
- **TypeScript Strict Rules**: Enabled with some exceptions
- **React Hooks**: Required rules enabled
- **Import Organization**: Alphabetical ordering with newlines between groups
- **Unused Variables**: Error for unused vars, but ignores variables starting with `_`
- **Empty Functions**: Disabled (allowed for interface implementations)
- **Floating Promises**: Disabled (async operations handled by Obsidian)
- **Unsafe Operations**: Disabled for Obsidian plugin compatibility

## Naming Conventions
- **Variables**: camelCase
- **Functions**: camelCase
- **Classes**: PascalCase
- **Interfaces**: PascalCase (typically with descriptive names)
- **Types**: PascalCase
- **Constants**: UPPER_CASE
- **Files**: kebab-case for components, camelCase for utilities

## Import Organization
- **External Libraries**: First (alphabetical)
- **Obsidian API**: Second
- **Internal Modules**: Third (relative paths)
- **Type Imports**: Separated from value imports
- **Newlines**: Between different import groups

## React Conventions
- **Functional Components**: Preferred over class components
- **Hooks**: Custom hooks for shared logic
- **Props**: Destructured in function parameters
- **State**: useState for simple state, useReducer for complex state
- **Effects**: useEffect for side effects
- **Context**: React Context for shared state

## File Organization
- **Components**: Feature-based organization in `src/components/`
- **Hooks**: Custom hooks in `src/hooks/`
- **Utils**: Utility functions in `src/utils/`
- **Types**: Type definitions in `src/types/`
- **Core Logic**: Business logic in `src/core/`
- **Database**: Database-related code in `src/database/`
- **Settings**: Configuration in `src/settings/`

## Documentation
- **JSDoc**: For complex functions and classes
- **Inline Comments**: For complex logic
- **README**: Comprehensive documentation for features
- **Type Definitions**: Self-documenting with clear names

## Testing
- **Jest**: Testing framework
- **Test Files**: `.test.ts` or `.test.tsx` suffix
- **Test Organization**: Tests co-located with source files
- **Mocking**: Obsidian API and external dependencies
- **Coverage**: Unit tests for critical functionality

## Error Handling
- **Try/Catch**: For async operations
- **Custom Exceptions**: For specific error types
- **User Notifications**: Obsidian Notice API for user feedback
- **Logging**: Console logging for debugging

## Performance Considerations
- **React.memo**: For expensive components
- **useCallback**: For event handlers
- **useMemo**: For expensive calculations
- **Lazy Loading**: For heavy components
- **Debouncing**: For search and input operations