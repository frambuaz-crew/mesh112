# MESH112 - AI Copilot Instructions

## Project Overview

**MESH112** is an emergency disaster communication platform using mesh networking and on-device AI to enable communication when GSM/internet infrastructure fails. Named after Turkey's emergency number (112), this React Native app creates a decentralized peer-to-peer network via Bluetooth Low Energy and WiFi Direct.

**Core Mission**: Enable survivors, rescue teams, and medical personnel to communicate, share locations, and request help during earthquakes and disasters without internet connectivity.

## Architecture & Key Components

### Multi-Layer Architecture
```
UI Layer (React Native)
├─ Chat Screen: WhatsApp-like messaging with AI priority indicators
├─ Map Screen: Real-time user locations, SOS markers, safe zones
├─ Profile Screen: Blood type, medical info, emergency contacts
└─ SOS Button: One-tap emergency broadcast with GPS

Business Logic Layer
├─ Message Manager: Queue, routing, deduplication
├─ AI Engine: On-device NLP for message prioritization
└─ Location Service: GPS tracking and proximity detection

Network Layer (Decentralized)
├─ BLE Mesh: 10-50m range, low power consumption
├─ WiFi Direct: 100m+ range, faster data transfer
└─ Multi-hop Routing: Auto-relaying messages across network

Data Layer (Offline-First)
├─ SQLite: Message history, user profiles
└─ AsyncStorage: App settings, cached data
```

### Critical Data Flows

**Message Broadcast Flow**:
1. User sends message → AI analyzes (category + urgency 0.0-1.0)
2. Auto-attach GPS coordinates
3. Broadcast via BLE/WiFi mesh to all nodes
4. Each node relays message to extend range
5. Recipients see prioritized messages (🔴 Critical → 🟡 Low)

**SOS Flow**: 
Single tap → Broadcast "EMERGENCY! [Name] [GPS] [Timestamp]" to entire network + mark location on all maps

## Technology Stack

### Mobile Framework
- **React Native**: Cross-platform (iOS + Android)
- **React Navigation**: Multi-screen routing
- **AsyncStorage**: Persistent key-value storage

### Mesh Networking
- **Bluetooth Low Energy (BLE)**: Primary communication protocol
- **WiFi Direct**: Extended range communication
- **Custom Routing Algorithm**: Multi-hop message relay (AODV/Flooding hybrid)

### On-Device AI (No Internet Required!)
- **Model**: TinyLlama 1.1B or Phi-2 (quantized to 4-bit)
- **Runtime**: ONNX Runtime Mobile
- **Tasks**: 
  - Message classification (Medical/Emergency/Location/Need/Info)
  - Urgency scoring (0.0-1.0)
  - Multi-language translation (TR/EN/AR/KU)
  - Spam filtering

### Geolocation
- **GPS**: Continuous location tracking
- **Geofencing**: Proximity alerts for nearby help requests

## Development Conventions

### Message Priority System
When implementing message handling, always apply AI categorization:
```javascript
// AI returns priority level
const priority = {
  CRITICAL: 1.0,  // 🔴 "Trapped under rubble, bleeding"
  HIGH: 0.75,     // 🟠 "AB+ blood needed urgently"
  MEDIUM: 0.5,    // 🟡 "Need water supplies"
  LOW: 0.25       // ⚪ "Checking in, are you safe?"
}

// Sort messages by priority DESC, timestamp ASC
messages.sort((a, b) => b.priority - a.priority || a.timestamp - b.timestamp)
```

### Network Node Management
Each device acts as both client and relay:
- **Scanning Interval**: 30 seconds normal, 2 minutes battery-saver mode
- **Message TTL**: 24 hours (after which messages expire)
- **Max Hops**: 10 (prevent infinite loops)
- **Deduplication**: Track message IDs to avoid re-broadcasting

### Profile Data Structure
Critical emergency info stored locally:
```javascript
userProfile = {
  name: string,
  bloodType: 'A+' | 'A-' | 'B+' | 'B-' | 'AB+' | 'AB-' | '0+' | '0-',
  chronicDiseases: string[],
  allergies: string[],
  medications: string[],
  emergencyContacts: [{name, phone}]
}
```

### Battery Optimization Strategies
- Reduce BLE scanning frequency in low-battery mode
- Throttle GPS updates (1-minute intervals instead of continuous)
- Minimize AI inference (cache results for similar messages)
- Target: **24+ hours continuous operation**

## Testing Requirements

### Network Testing
- **Unit**: Message routing logic, deduplication, TTL expiration
- **Integration**: BLE/WiFi connectivity, multi-hop relay simulation
- **Load**: 100+ concurrent users, 1000+ messages/hour
- **Field**: Real-world disaster drill scenarios with 50+ devices

### AI Model Testing
- **Accuracy**: >85% correct categorization on Turkish disaster messages
- **Latency**: <1 second inference time on mid-range smartphones
- **Offline**: Must work with zero internet connectivity

### Performance Benchmarks
- Message latency: <2 seconds for 3-hop relay
- Network range: 10 devices × 50m = 500m+ total coverage
- Battery drain: <5% per hour active usage
- Crash-free rate: >99%

## Key Workflows

### Development Setup
1. Install React Native CLI and dependencies
2. Download quantized AI model (TinyLlama 4-bit ONNX)
3. Enable Bluetooth permissions (iOS: Info.plist, Android: AndroidManifest.xml)
4. Test on physical devices (BLE won't work in simulators)

### Building for Production
- **iOS**: Code signing, TestFlight beta distribution
- **Android**: Generate signed APK/AAB for Play Store
- **App size target**: <100MB total

### Disaster Simulation Testing
Create test scenarios matching real-world usage:
1. **Earthquake scenario**: Disable WiFi/cellular, enable airplane mode
2. **Multi-hop test**: Place devices 50m apart (measure actual relay range)
3. **Blood type matching**: Test AI auto-matching donors to requests
4. **Battery stress**: 24-hour continuous operation test

## Critical Design Principles

### Offline-First Architecture
Every feature MUST work without internet:
- Message storage in SQLite (sync to cloud only when online)
- AI model embedded in app bundle
- Map tiles cached for offline use (OpenStreetMap)

### Decentralized & Unstoppable
- No single point of failure (no central server required)
- P2P mesh = resistant to censorship and infrastructure collapse
- Each user contributes to network resilience

### Emergency UX Patterns
- **One-tap SOS**: No nested menus in panic situations
- **High contrast colors**: Red for critical, green for safe zones
- **Large touch targets**: Usable with trembling hands
- **Audio confirmations**: Beeps/vibrations for message sent/received

## Integration Points

### Optional Cloud Sync (When Internet Available)
- **Purpose**: Analytics, backup, message history recovery
- **Backend**: Node.js REST API or Firebase
- **Privacy**: End-to-end encryption, opt-in data sharing

### AFAD/Kızılay Integration
- Official toplanma noktası (gathering point) data feeds
- Real-time disaster zone updates
- Coordination with professional rescue teams

### External Dependencies
- **Maps**: OpenStreetMap (offline tiles)
- **AI Model**: Hugging Face model hub (download once)
- **BLE Library**: react-native-ble-plx
- **WiFi Direct**: Platform-native implementations

## Turkish-Specific Context

### Language & Localization
- Primary language: **Turkish** (UI and AI model training)
- Support for Turkish characters (ı, ğ, ş, ç, ö, ü)
- Disaster-specific vocabulary (enkaz=rubble, yardım=help, kan grubu=blood type)

### Turkish Emergency System Integration
- **112**: Emergency hotline reference in branding
- **AFAD**: Turkey's Disaster and Emergency Management Presidency
- **UMKE**: National Medical Rescue Teams
- **Kızılay**: Turkish Red Crescent

### Earthquake Preparedness
Informed by real disasters:
- **1999 Marmara Earthquake**: Communication infrastructure collapse lessons
- **2023 Kahramanmaraş Earthquake**: 50,000+ casualties, GSM network failure
- Design decisions prioritize rubble/collapsed building scenarios

## Project Management

### Team Structure (5 People)
1. **Project Manager / Full Stack** - Sprint planning, backend API, cloud sync
2. **AI/ML Engineer** - On-device AI, ONNX integration, message classification
3. **Mobile Developer** - React Native core, BLE/WiFi, iOS/Android builds
4. **Network Engineer** - Mesh routing, multi-hop logic, message deduplication
5. **UI/UX Designer** - Figma design, React Native components, usability testing

### Development Workflow
- **Sprints**: 3-week cycles (18 weeks total = 6 sprints)
- **Daily Standup**: 15 minutes (09:00 daily)
- **Sprint Planning**: 2 hours (sprint start)
- **Sprint Review**: 1.5 hours (sprint end)
- **Code Review**: <24 hour turnaround on PRs

### Current Phase
See `PROJE_PLANI.md` for detailed 18-week roadmap with:
- Phase 1 (Week 1-3): Research & Analysis
- Phase 2 (Week 4-6): Design & Prototype
- Phase 3 (Week 7-12): MVP Development
- Phase 4 (Week 13-15): AI & Geolocation
- Phase 5 (Week 16-17): Testing & Optimization
- Phase 6 (Week 18): Deployment & Presentation

## Contributing Guidelines

### Code Structure
- Feature-based folder organization (e.g., `/features/messaging`, `/features/maps`)
- Shared components in `/components/common`
- AI model files in `/assets/models`

### Commit Conventions
Use semantic prefixes:
- `feat:` New features (e.g., "feat: add blood type matching")
- `fix:` Bug fixes
- `perf:` Performance improvements (critical for battery life)
- `ai:` AI model updates
- `docs:` Documentation updates
- `test:` Test additions or modifications

### Documentation
- All disaster-critical functions require inline comments
- Turkish comments accepted for Turkey-specific logic
- Update benchmarks when performance changes
- Reference `PROJE_PLANI.md` for sprint schedules and task assignments

## Success Metrics

### MVP Criteria (6-month target)
- ✅ 10+ devices stable mesh network
- ✅ Text messaging with AI prioritization (>85% accuracy)
- ✅ GPS location sharing + SOS button
- ✅ 24+ hour battery life

### Social Impact Goals
- **Beta**: 50+ campus testers
- **Launch**: 10,000+ downloads (Turkey App Store/Play Store)
- **Adoption**: Partnership with AFAD for official disaster drills
- **Global**: Adapt for earthquake-prone countries (Japan, Nepal, Chile)

---

**Disaster-Resilient Turkey Initiative | #MESH112 | #AcilDurum**

When in doubt, prioritize **offline functionality**, **battery efficiency**, and **one-tap emergency actions**. This app must work when everything else fails.
