# Task Completion Guidelines

## Development Workflow

### Before Starting Any Task
1. **Check Current State**: Review existing code and understand the current implementation
2. **Understand Requirements**: Clarify what needs to be built or changed
3. **Plan Approach**: Consider multiple implementation strategies
4. **Check Dependencies**: Ensure all required packages are available

### During Development
1. **Follow Code Style**: Adhere to Prettier and ESLint rules
2. **Write Tests**: Add tests for new functionality
3. **Type Safety**: Ensure TypeScript compilation passes
4. **Test Integration**: Verify Obsidian plugin functionality
5. **Handle Errors**: Implement proper error handling and user feedback

### Before Completing Any Task
1. **Run Quality Checks**:
   ```bash
   npm run lint:check    # Check formatting and linting
   npm run type:check    # Verify TypeScript types
   npm test              # Run test suite
   ```

2. **Test in Obsidian**:
   - Reload plugin in Obsidian
   - Test new functionality manually
   - Verify no console errors
   - Check memory usage (avoid leaks)

3. **Update Documentation**:
   - Update README if new features added
   - Add JSDoc comments for public APIs
   - Update type definitions
   - Document any breaking changes

4. **Database Changes** (if applicable):
   ```bash
   npx drizzle-kit generate --name <migration-name>
   npm run migrate:compile
   ```
   - Test migrations in development
   - Ensure data integrity
   - Update schema documentation

## Code Quality Standards

### Must Always Pass
- **Linting**: `npm run lint:check` should pass without errors
- **Type Checking**: `npm run type:check` should pass
- **Tests**: `npm test` should pass (add tests for new code)
- **Build**: `npm run build` should succeed

### Should Follow
- **Error Handling**: Proper try/catch blocks and user feedback
- **Type Safety**: Avoid `any` types, use proper TypeScript
- **Performance**: Consider memory usage and performance impact
- **Accessibility**: Use semantic HTML and ARIA labels
- **Security**: Validate inputs and handle sensitive data properly

## Testing Requirements

### For New Features
1. **Unit Tests**: Test core functionality in isolation
2. **Integration Tests**: Test with Obsidian API mocks
3. **Manual Testing**: Verify in actual Obsidian environment
4. **Edge Cases**: Test error conditions and boundary cases

### For Bug Fixes
1. **Regression Tests**: Ensure fix doesn't break existing functionality
2. **Reproduction Steps**: Document how to reproduce the original issue
3. **Verification**: Confirm fix resolves the issue

## Database Schema Changes

### When Modifying Schema
1. **Create Migration**: Use `npx drizzle-kit generate --name <name>`
2. **Review Generated Files**: Check migration SQL for correctness
3. **Test Migration**: Run in development environment
4. **Compile Migration**: Run `npm run migrate:compile`
5. **Update Types**: Ensure TypeScript types are current

### Migration Best Practices
- **Atomic Changes**: Each migration should be reversible
- **Descriptive Names**: Use clear, descriptive migration names
- **Data Preservation**: Ensure existing data is preserved
- **Testing**: Test migrations on copy of production data

## Documentation Updates

### When Adding Features
1. **README**: Update feature descriptions and setup instructions
2. **JSDoc**: Add comprehensive documentation for public APIs
3. **Type Definitions**: Ensure all types are well-documented
4. **Examples**: Provide usage examples where appropriate

### When Changing Behavior
1. **Breaking Changes**: Document what changed and migration path
2. **Deprecation**: Mark old APIs as deprecated with alternatives
3. **Migration Guide**: Provide steps for users to upgrade

## Performance Considerations

### Always Check
1. **Memory Usage**: Monitor for memory leaks during development
2. **Bundle Size**: Ensure changes don't significantly increase bundle size
3. **Runtime Performance**: Test with large vaults and many chats
4. **Database Queries**: Optimize slow queries and add indexes if needed

### Optimization Techniques
1. **Lazy Loading**: Load heavy components only when needed
2. **Memoization**: Cache expensive calculations
3. **Debouncing**: Debounce rapid user inputs
4. **Virtualization**: Use for long lists or large datasets

## Security Considerations

### For AI Integration
1. **API Keys**: Never commit API keys to version control
2. **Input Validation**: Validate all user inputs and AI responses
3. **Rate Limiting**: Implement rate limiting for API calls
4. **Error Messages**: Avoid exposing sensitive information in errors

### For Database
1. **SQL Injection**: Use parameterized queries (Drizzle handles this)
2. **Data Validation**: Validate data before database insertion
3. **Access Control**: Ensure proper file access permissions
4. **Encryption**: Encrypt sensitive data at rest

## Release Checklist

### Before Publishing
- [ ] All tests pass (`npm test`)
- [ ] Type checking passes (`npm run type:check`)
- [ ] Linting passes (`npm run lint:check`)
- [ ] Build succeeds (`npm run build`)
- [ ] Manual testing in Obsidian completed
- [ ] Documentation updated
- [ ] Database migrations tested
- [ ] Version bumped (`npm run version`)
- [ ] No console errors in development
- [ ] Performance testing completed
- [ ] Security review completed

### After Publishing
- [ ] Monitor for user feedback and issues
- [ ] Address any immediate bug reports
- [ ] Update documentation based on user questions
- [ ] Plan next iteration based on usage patterns