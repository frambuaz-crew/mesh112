# 🤝 Contributing to MESH112

Thank you for your interest in contributing to **MESH112** - an emergency disaster communication platform! This document provides guidelines for contributing to the project.

---

## 📋 Table of Contents

- [Code of Conduct](#code-of-conduct)
- [How Can I Contribute?](#how-can-i-contribute)
- [Development Setup](#development-setup)
- [Coding Standards](#coding-standards)
- [Commit Conventions](#commit-conventions)
- [Pull Request Process](#pull-request-process)
- [Testing Guidelines](#testing-guidelines)

---

## 📜 Code of Conduct

### Our Pledge

In the interest of fostering an open and welcoming environment, we pledge to:
- Be respectful and inclusive
- Accept constructive criticism gracefully
- Focus on what's best for the community and disaster victims
- Show empathy towards other community members

### Unacceptable Behavior
- Harassment, discrimination, or trolling
- Political or religious debates unrelated to the project
- Spam or self-promotion

---

## 🚀 How Can I Contribute?

### 1. Reporting Bugs

**Before submitting a bug report**:
- Check existing [Issues](https://github.com/your-team/mesh112/issues)
- Test on latest version
- Collect debug logs

**Good bug report includes**:
```markdown
**Device**: iPhone 13, iOS 16.5 / Samsung S21, Android 13
**App Version**: v0.5.0-beta
**Steps to Reproduce**:
1. Open Chat screen
2. Send message with emoji
3. App crashes

**Expected**: Message sends successfully
**Actual**: App crashes with error "..."
**Logs**: (paste crash log)
```

### 2. Suggesting Features

**Feature request template**:
```markdown
**Problem**: Currently, users can't filter messages by category
**Proposed Solution**: Add filter dropdown (Medical/Emergency/Info)
**Alternatives**: Search bar with category tags
**Priority**: Medium (nice-to-have for MVP)
```

### 3. Translating

We need translations for:
- Turkish (primary)
- English
- Arabic
- Kurdish

See `src/i18n/` for translation files.

### 4. Writing Code

**Good first issues**:
- Look for `good-first-issue` label
- Documentation improvements
- UI component refinements
- Unit test additions

---

## 💻 Development Setup

### Prerequisites
- **Node.js**: 18+ (LTS)
- **React Native CLI**: Latest
- **Xcode**: 14+ (macOS, for iOS)
- **Android Studio**: Latest
- **Git**: Latest
- **Physical devices** (BLE doesn't work in simulators!)

### Installation

```bash
# 1. Fork the repository on GitHub
# 2. Clone your fork
git clone https://github.com/YOUR_USERNAME/mesh112.git
cd mesh112

# 3. Add upstream remote
git remote add upstream https://github.com/your-team/mesh112.git

# 4. Install dependencies
npm install

# 5. iOS setup (macOS only)
cd ios && pod install && cd ..

# 6. Download AI model
npm run download-model

# 7. Start Metro bundler
npm start

# 8. Run on device (in new terminal)
npx react-native run-android
# or
npx react-native run-ios
```

### Environment Variables

Create `.env` file:
```bash
# Optional backend API (for cloud sync)
API_URL=http://localhost:3000
FIREBASE_API_KEY=your_key_here

# AI Model
MODEL_PATH=assets/models/tinyllama-4bit.onnx

# Debug
DEBUG_MODE=true
```

---

## 📝 Coding Standards

### TypeScript

**Use TypeScript** for all new code:
```typescript
// ✅ Good
interface Message {
  id: string;
  content: string;
  priority: number;
  timestamp: Date;
}

function sendMessage(message: Message): Promise<void> {
  // implementation
}

// ❌ Bad (no types)
function sendMessage(message) {
  // implementation
}
```

### Naming Conventions

| Type | Convention | Example |
|------|-----------|---------|
| **Components** | PascalCase | `ChatScreen.tsx`, `SosButton.tsx` |
| **Hooks** | useCamelCase | `useBleMesh.ts`, `useGpsLocation.ts` |
| **Utils** | camelCase | `formatTimestamp.ts`, `calculateDistance.ts` |
| **Constants** | UPPER_SNAKE_CASE | `MAX_HOPS`, `DEFAULT_TTL` |
| **Types/Interfaces** | PascalCase | `Message`, `UserProfile` |

### File Structure

```
src/
├─ features/           # Feature-based organization
│  ├─ messaging/
│  │  ├─ components/   # Feature-specific components
│  │  ├─ hooks/        # Custom hooks
│  │  ├─ screens/      # Screen components
│  │  └─ utils/        # Helper functions
│  ├─ maps/
│  └─ profile/
├─ components/         # Shared components
│  ├─ common/          # Button, Input, Card, etc.
│  └─ layout/          # Header, Footer, etc.
├─ navigation/         # React Navigation setup
├─ services/           # API, BLE, GPS services
│  ├─ ble/
│  ├─ ai/
│  └─ location/
├─ store/              # State management (Zustand)
├─ utils/              # Global utilities
├─ assets/             # Images, models, fonts
└─ types/              # TypeScript type definitions
```

### Code Style

**Use ESLint + Prettier**:
```bash
# Lint check
npm run lint

# Auto-fix
npm run lint:fix

# Format
npm run format
```

**Key rules**:
- No `any` type (use `unknown` if needed)
- Prefer `const` over `let`
- Use arrow functions for callbacks
- Max line length: 100 characters
- Always use semicolons

---

## 🔖 Commit Conventions

We use **semantic commit messages**:

```
<type>(<scope>): <subject>

<body>

<footer>
```

### Types

| Type | Description | Example |
|------|-------------|---------|
| `feat` | New feature | `feat(ble): add multi-hop routing` |
| `fix` | Bug fix | `fix(chat): resolve message duplication` |
| `perf` | Performance improvement | `perf(ai): optimize inference latency` |
| `docs` | Documentation | `docs(readme): add Turkish translation` |
| `style` | Code formatting | `style: apply prettier formatting` |
| `refactor` | Code refactoring | `refactor(network): simplify routing logic` |
| `test` | Test additions | `test(ble): add connection test` |
| `chore` | Build/tooling | `chore: update dependencies` |
| `ai` | AI model updates | `ai: upgrade to TinyLlama 1.2B` |

### Examples

```bash
# Good commits
git commit -m "feat(sos): add emergency broadcast button"
git commit -m "fix(map): correct GPS coordinate formatting"
git commit -m "perf(battery): reduce BLE scanning frequency"

# Bad commits (avoid)
git commit -m "fixed stuff"
git commit -m "update"
git commit -m "WIP"
```

### Scope

Common scopes:
- `ble`, `wifi`, `network`, `routing`
- `ai`, `ml`, `model`
- `chat`, `map`, `profile`, `sos`
- `ui`, `design`, `animation`
- `database`, `storage`
- `test`, `ci`, `build`

---

## 🔄 Pull Request Process

### Before Submitting

1. **Create a branch**:
```bash
git checkout -b feat/blood-type-matching
```

2. **Make changes** and commit following conventions

3. **Pull latest changes**:
```bash
git fetch upstream
git rebase upstream/main
```

4. **Run tests**:
```bash
npm run test
npm run lint
```

5. **Push to your fork**:
```bash
git push origin feat/blood-type-matching
```

### PR Template

```markdown
## Description
Brief description of changes

## Type of Change
- [ ] Bug fix
- [ ] New feature
- [ ] Breaking change
- [ ] Documentation update

## Testing
- [ ] Unit tests added/updated
- [ ] E2E tests pass
- [ ] Tested on physical device (Android/iOS)

## Screenshots (if UI change)
![Before](url) ![After](url)

## Checklist
- [ ] Code follows style guidelines
- [ ] Self-review completed
- [ ] Comments added for complex logic
- [ ] Documentation updated
- [ ] No new warnings
```

### Code Review

**Reviewers will check**:
- Code quality and readability
- Test coverage
- Performance implications (battery, latency)
- Security concerns
- Accessibility (a11y)

**Expected turnaround**: <24 hours for initial review

---

## 🧪 Testing Guidelines

### Unit Tests (Jest)

```typescript
// src/utils/__tests__/calculateDistance.test.ts
import { calculateDistance } from '../calculateDistance';

describe('calculateDistance', () => {
  it('should calculate distance between two GPS points', () => {
    const pointA = { lat: 39.9334, lng: 32.8597 }; // Ankara
    const pointB = { lat: 41.0082, lng: 28.9784 }; // Istanbul
    
    const distance = calculateDistance(pointA, pointB);
    
    expect(distance).toBeCloseTo(350, 0); // ~350km
  });
});
```

**Run tests**:
```bash
npm run test                # All tests
npm run test:watch          # Watch mode
npm run test:coverage       # With coverage
```

**Coverage target**: >70%

### E2E Tests (Detox)

```typescript
// e2e/chat.e2e.ts
describe('Chat Flow', () => {
  beforeAll(async () => {
    await device.launchApp();
  });

  it('should send a message', async () => {
    await element(by.id('chat-input')).typeText('Test message');
    await element(by.id('send-button')).tap();
    
    await expect(element(by.text('Test message'))).toBeVisible();
  });
});
```

**Run E2E**:
```bash
npm run e2e:build:android
npm run e2e:test:android
```

### Manual Testing Checklist

Before PR, test:
- [ ] **BLE Connection**: Scan and connect to 2+ devices
- [ ] **Message Flow**: Send message, verify multi-hop relay
- [ ] **AI Priority**: Send "Help!" → should be high priority
- [ ] **SOS**: Tap SOS button → broadcast to all devices
- [ ] **GPS**: Location appears on map correctly
- [ ] **Offline**: Airplane mode ON → app still works
- [ ] **Battery**: <5% drain per hour (use Xcode Energy Log)

---

## 🐛 Debugging

### React Native Debugger

```bash
# Install
brew install --cask react-native-debugger

# Run
open "rndebugger://set-debugger-loc?host=localhost&port=8081"
```

### Flipper

```bash
# Already configured in project
# Open Flipper app, select device
# Available plugins:
# - Network inspector
# - Redux DevTools
# - Crash reporter
# - Performance monitor
```

### BLE Debugging

**Android**:
```bash
# Enable BLE HCI snoop log
adb shell settings put secure bluetooth_hci_log 1
adb bugreport
```

**iOS**:
```bash
# Xcode → Window → Devices and Simulators
# Select device → View Device Logs
# Filter: Bluetooth
```

---

## 🌍 Internationalization (i18n)

### Adding Translations

1. Open `src/i18n/locales/tr.json`
2. Add key-value pairs:

```json
{
  "common": {
    "send": "Gönder",
    "cancel": "İptal"
  },
  "chat": {
    "messagePlaceholder": "Mesajınızı yazın..."
  }
}
```

3. Use in component:

```typescript
import { useTranslation } from 'react-i18next';

function ChatScreen() {
  const { t } = useTranslation();
  
  return (
    <TextInput placeholder={t('chat.messagePlaceholder')} />
  );
}
```

---

## 📦 Release Process

### Versioning (Semantic Versioning)

- **MAJOR**: Breaking changes (v2.0.0)
- **MINOR**: New features (v1.1.0)
- **PATCH**: Bug fixes (v1.0.1)

### Release Checklist

- [ ] Update version in `package.json`
- [ ] Update `CHANGELOG.md`
- [ ] Run full test suite
- [ ] Build Android AAB + iOS IPA
- [ ] Test on 3+ physical devices
- [ ] Upload to TestFlight / Play Console (Internal Testing)
- [ ] Create GitHub release with notes
- [ ] Tag commit: `git tag v1.0.0`

---

## 🙏 Thank You!

Every contribution helps save lives in disaster scenarios. Whether it's code, documentation, translation, or testing - **you're making a difference!**

**Contributors Hall of Fame**: [CONTRIBUTORS.md](CONTRIBUTORS.md)

---

## 📞 Questions?

- **GitHub Discussions**: [github.com/your-team/mesh112/discussions](https://github.com/your-team/mesh112/discussions)
- **Discord**: MESH112 Community (coming soon)
- **Email**: dev@mesh112.org

---

<div align="center">

**MESH112 - Open Source Disaster Response**

*Afet anında her satır kod, bir hayat kurtarabilir.*  
*In disasters, every line of code can save a life.*

</div>
