# Suggested Commands for Development

## Development Workflow

### Start Development Server
```bash
npm run dev
```
- Starts the development build with hot reloading
- Watches for file changes and rebuilds automatically
- Essential for active development

### Build for Production
```bash
npm run build
```
- TypeScript compilation and production build
- Creates optimized bundle in `main.js`
- Required before testing in Obsidian

### Version Management
```bash
npm run version
```
- Bumps version numbers across all relevant files
- Updates manifest.json, package.json, and versions.json
- Use before releasing new versions

## Code Quality

### Lint and Format Check
```bash
npm run lint:check
```
- Runs Prettier formatting check
- Runs ESLint for code quality issues
- Should pass before committing code

### Auto-fix Lint and Format
```bash
npm run lint:fix
```
- Automatically fixes formatting with Prettier
- Automatically fixes ESLint issues where possible
- Use when lint:check fails

### Type Checking
```bash
npm run type:check
```
- Runs TypeScript compiler in check mode
- Validates all type definitions
- Should pass before committing

## Testing

### Run Test Suite
```bash
npm test
```
- Executes Jest test runner
- Runs all unit tests
- Should pass before merging changes

### Run Tests in Watch Mode
```bash
npm run test:watch
```
- Continuous testing during development
- Re-runs tests on file changes
- Useful for TDD workflow

## Database Management

### Generate Database Migrations
```bash
npx drizzle-kit generate --name <migration-name>
```
- Creates new migration files from schema changes
- Replace `<migration-name>` with descriptive name
- Review generated files before committing

### Compile Migration Files
```bash
npm run migrate:compile
```
- Compiles migration files into `src/database/migrations.json`
- Required after generating new migrations
- Must run before database changes take effect

## Obsidian Integration

### Install in Development
1. Copy/symlink plugin to Obsidian plugins directory:
```bash
ln -s /path/to/obsidian-smart-composer /path/to/vault/.obsidian/plugins/
```
2. Enable plugin in Obsidian settings
3. Run `npm run dev` for hot reloading

### Test Plugin Commands
- **Open Chat**: Ribbon icon or command palette
- **Add Selection to Chat**: Select text and use command
- **Rebuild Vault Index**: For RAG functionality
- **Update Vault Index**: For modified files

## Debugging

### Enable Debug Logging
Edit `esbuild.config.mjs`:
```javascript
logLevel: 'debug'
```
- Provides detailed build output
- Helps identify compilation issues
- Remember to disable for production

### Database Debugging
1. Open Obsidian developer console
2. Look for "Smart composer database initialized" message
3. Right-click and "Store as global variable"
4. Run SQL queries: `await temp1.pgClient.query('SELECT ...')`
5. Save changes: `await temp1.save()`

## Utility Commands

### Git Operations
```bash
# Check status
cd /path/to/project && git status

# Stage changes
git add .

# Commit with message
git commit -m "feat: add new feature"

# Push to remote
git push origin main
```

### File Operations (macOS)
```bash
# List files
ls -la

# Find files
find . -name "*.ts" -type f

# Search in files
grep -r "functionName" src/

# Create directory
mkdir -p new-feature
```

### Node.js and npm
```bash
# Check versions
node --version
npm --version

# Install dependencies
npm install

# Update dependencies
npm update

# Clear npm cache
npm cache clean --force
```

## Hot Reload Setup (Optional)
1. Install Hot Reload plugin in Obsidian
2. Enable in Community Plugins
3. Changes will reload automatically during development
4. Faster than manual reloading for active development

## Performance Monitoring
- Monitor Obsidian developer console for errors
- Check memory usage during long development sessions
- Watch for memory leaks when reloading plugin frequently
- Use browser dev tools if webview issues occur