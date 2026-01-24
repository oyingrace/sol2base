# Contributing to Terminally Onchain

Thank you for your interest in contributing! This guide will help you understand the project and identify ways to contribute.

## 🎯 Project Overview

**Terminally Onchain** is a bridge application that allows users to:
- Bridge SOL and SPL tokens between Solana (Devnet/Mainnet) and Base (Sepolia/Mainnet)
- Call any Base contract directly from a Solana wallet
- Use a terminal-style interface with a "hacker" aesthetic

## 🚀 Quick Start for Contributors

1. **Fork and clone the repository**
   ```bash
   git clone https://github.com/YOUR_USERNAME/terminally-onchain.git
   cd terminally-onchain
   ```

2. **Install dependencies**
   ```bash
   npm install --legacy-peer-deps
   ```

3. **Set up environment**
   ```bash
   cp env.template .env.local
   # Optionally add CDP API credentials for faucet testing
   ```

4. **Start development server**
   ```bash
   npm run dev
   ```

## 📋 Contribution Opportunities

### 🔴 High Priority

#### 1. **Add Test Coverage** (Currently 0%)
The project has no tests. This is a critical area for contribution:

- **Unit Tests**: Test core bridge logic, address resolution, terminal parsing
  - `src/lib/bridge.ts` - Bridge transaction creation
  - `src/lib/terminalParser.ts` - Command parsing
  - `src/lib/addressResolver.ts` - ENS/Basename resolution
  - `src/lib/realBridgeImplementation.ts` - Bridge implementation

- **Integration Tests**: Test end-to-end bridge flows
  - Bridge SOL from Solana to Base
  - Bridge SPL tokens
  - Contract call attachments

- **Component Tests**: Test React components
  - `src/components/MainContent.tsx` - Main terminal interface
  - `src/components/WalletConnection.tsx` - Wallet integration
  - `src/components/terminal/*` - Terminal components

**Suggested Testing Stack:**
- Jest + React Testing Library for unit/component tests
- Playwright or Cypress for E2E tests
- Mock Solana/Base RPC calls for integration tests

#### 2. **Improve Error Handling**
While error handling exists, it could be more comprehensive:

- Add retry logic for failed transactions
- Better error messages for common failure scenarios
- User-friendly error recovery suggestions
- Transaction status polling improvements

**Files to improve:**
- `src/lib/bridge.ts` - Add retry mechanisms
- `src/lib/realBridgeImplementation.ts` - Better error diagnostics
- `src/components/MainContent.tsx` - Enhanced error display

#### 3. **Documentation Improvements**
- API documentation
- Architecture diagrams
- Bridge flow documentation
- Troubleshooting guide
- Video tutorials or GIFs showing usage

### 🟡 Medium Priority

#### 4. **UI/UX Enhancements**
- **Transaction History**: Better visualization of bridge history
- **Loading States**: More informative loading indicators
- **Mobile Responsiveness**: Improve mobile experience
- **Accessibility**: Add ARIA labels, keyboard navigation
- **Dark/Light Mode**: Optional theme toggle (keeping hacker aesthetic)

#### 5. **Performance Optimizations**
- **RPC Optimization**: Batch RPC calls where possible
- **Caching**: Cache address resolutions, balances
- **Code Splitting**: Lazy load components
- **Bundle Size**: Analyze and reduce bundle size

#### 6. **New Features**
- **Transaction Status Tracking**: Real-time status updates from Base
- **Multi-token Support**: Easier management of multiple SPL tokens
- **Bridge History Persistence**: Save transaction history locally
- **Export/Import**: Export bridge commands for reuse
- **Batch Operations**: Bridge multiple tokens in one transaction
- **Gas Estimation**: Show estimated gas costs before bridging

#### 7. **Developer Experience**
- **Type Safety**: Improve TypeScript types
- **ESLint Rules**: Add more strict linting rules
- **Pre-commit Hooks**: Add Husky for linting/formatting
- **CI/CD**: Add GitHub Actions for testing/linting
- **Code Formatting**: Add Prettier configuration

### 🟢 Low Priority / Nice to Have

#### 8. **Additional Integrations**
- Support for more Solana wallets
- Support for more Base RPC providers
- Integration with block explorers
- Price feeds for tokens

#### 9. **Analytics & Monitoring**
- Error tracking (Sentry, etc.)
- Usage analytics (privacy-respecting)
- Performance monitoring

#### 10. **Internationalization**
- Multi-language support
- Localized error messages

## 🛠️ Development Guidelines

### Code Style
- Follow existing code patterns
- Use TypeScript strictly (no `any` types)
- Use functional React components with hooks
- Follow the "hacker" aesthetic theme (green on black)

### Git Workflow
1. Create a feature branch: `git checkout -b feature/your-feature-name`
2. Make your changes
3. Test your changes thoroughly
4. Commit with clear messages: `git commit -m 'Add: description of changes'`
5. Push to your fork: `git push origin feature/your-feature-name`
6. Open a Pull Request

### Commit Message Format
```
Type: Brief description

Longer explanation if needed
```

Types: `Add`, `Fix`, `Update`, `Refactor`, `Docs`, `Test`, `Style`

### Pull Request Guidelines
- **Title**: Clear, descriptive title
- **Description**: 
  - What changes were made
  - Why the changes were needed
  - How to test the changes
  - Screenshots/GIFs for UI changes
- **Size**: Keep PRs focused and reasonably sized
- **Tests**: Include tests for new features
- **Documentation**: Update docs if needed

## 🐛 Reporting Bugs

When reporting bugs, please include:
1. **Environment**: Node version, OS, browser
2. **Steps to Reproduce**: Clear steps to reproduce the issue
3. **Expected Behavior**: What should happen
4. **Actual Behavior**: What actually happens
5. **Screenshots/Logs**: If applicable
6. **Network**: Which network (devnet/mainnet) you were using

## 💡 Feature Requests

For feature requests:
1. Check if the feature already exists or is planned
2. Open an issue describing:
   - The problem you're trying to solve
   - Your proposed solution
   - Use cases

## 📚 Key Files to Understand

### Core Bridge Logic
- `src/lib/bridge.ts` - Main bridge service interface
- `src/lib/realBridgeImplementation.ts` - Actual bridge transaction building
- `src/lib/constants.ts` - Network configurations and addresses

### UI Components
- `src/components/MainContent.tsx` - Main terminal interface (1000+ lines)
- `src/components/terminal/TerminalInput.tsx` - Command input
- `src/components/WalletConnection.tsx` - Wallet integration

### Utilities
- `src/lib/terminalParser.ts` - Parses terminal commands
- `src/lib/addressResolver.ts` - Resolves ENS/Basename addresses
- `src/lib/cdpFaucet.ts` - Coinbase Developer Platform faucet

### API Routes
- `src/app/api/faucet/sol/route.ts` - SOL faucet endpoint
- `src/app/api/faucet/route.ts` - General faucet endpoint

## 🎨 Design Principles

- **Terminal-First**: The UI mimics a terminal interface
- **Hacker Aesthetic**: Green (#00ff00) on black background
- **Minimalist**: Clean, focused interface
- **Functional**: Every feature should have a clear purpose

## 🔍 Areas Needing Attention

Based on code analysis:

1. **No Test Coverage**: Critical for reliability
2. **Large Component Files**: `MainContent.tsx` is 1000+ lines - could be split
3. **Error Recovery**: Limited retry/recovery mechanisms
4. **Transaction Status**: Basic status tracking, could be enhanced
5. **Documentation**: README is good, but could use more technical docs

## 🤝 Getting Help

- Check existing issues and PRs
- Review the README.md
- Look at the code comments
- Open a discussion issue for questions

## 📝 License

By contributing, you agree that your contributions will be licensed under the MIT License.

---

**Remember**: Every contribution, no matter how small, is valuable! Whether it's fixing a typo, adding a test, or implementing a new feature, your help makes this project better.

Thank you for contributing! 🚀

