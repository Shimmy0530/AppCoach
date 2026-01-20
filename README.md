# AppCoach

> Guide non-technical users from app idea to working code through Socratic coaching.

## What is AppCoach?

AppCoach is a Claude skill that transforms anyone into an app creator — no coding experience required. It provides patient, structured guidance through every stage of app development, from initial concept to deployed application.

### Key Capabilities

- **Complete journey coverage**: Idea → Design → Code → Deployment → Support
- **Platform agnostic**: Web apps, PWAs, native mobile (Android/iOS), cross-platform
- **Beginner-first design**: Every technical term explained with real-world analogies
- **Production-ready output**: Fully documented, secure, deployable code
- **Scope protection**: Active MVP management to prevent feature creep

## The AppCoach Workflow

```
┌─────────────────────────────────────────────────────────────────────┐
│                           APPCOACH                                  │
└─────────────────────────────────────────────────────────────────────┘

    ┌─────────────┐     ┌─────────────┐     ┌─────────────┐
    │  DISCOVERY  │ ──► │  FEATURES   │ ──► │  PLATFORM   │
    │  What & Why │     │  MVP Scope  │     │  Web/Mobile │
    └─────────────┘     └─────────────┘     └─────────────┘
           │                                       │
           ▼                                       ▼
    ┌─────────────┐     ┌─────────────┐     ┌─────────────┐
    │   SUPPORT   │ ◄── │  DELIVERY   │ ◄── │  TECHNICAL  │
    │  Iterate    │     │  Deploy     │     │ Architecture│
    └─────────────┘     └─────────────┘     └─────────────┘
                               ▲
                               │
                        ┌─────────────┐
                        │ DEVELOPMENT │
                        │ Generate    │
                        └─────────────┘
```

### Phase Overview

| Phase | Goal | Output |
|-------|------|--------|
| **1. Discovery** | Understand vision, audience, problem | Problem Statement Document |
| **2. Features** | Define MVP with MoSCoW prioritization | Feature Specification |
| **3. Platform** | Choose web/mobile/cross-platform | Platform Decision |
| **4. Technical** | Design architecture, select stack | Technical Specification |
| **5. Development** | Generate complete, documented code | Full Codebase |
| **6. Delivery** | Package with README and deploy guide | Deployable App |
| **7. Support** | Test, debug, iterate, extend | Refined App |

## Installation

### For Claude Computer Use

Place the skill directory in your user skills folder:

```
/mnt/skills/user/AppCoach/
├── SKILL.md
└── references/
    ├── code-patterns.md
    └── tech-explanations.md
```

### For Claude Projects

1. Create a new Claude Project
2. Copy the contents of `SKILL.md` into the project's custom instructions
3. Optionally, append the reference files for enhanced code generation

## Usage

### Trigger Phrases

AppCoach activates when users express app development intent:

- "I have an app idea"
- "Help me build an app"
- "I want to create an app"
- "Design an app for me"
- "Can you help me make a [type] app?"

### Example Session

```
User: I have an app idea!

AppCoach: Exciting! I'd love to help you build it. Let's start by 
understanding your vision.

In one sentence, what does your app do?

User: It helps people track their water intake

AppCoach: Great concept! Staying hydrated is important. A few more 
questions to make sure we build exactly what you need:

1. What problem does this solve? What's frustrating about how people 
   currently track water intake?
2. Who will use this — fitness enthusiasts, office workers, everyone?
3. Where would someone use this — quick logging throughout the day, 
   or detailed tracking at home?

[Conversation continues through all phases...]
```

## What's Included

```
AppCoach/
├── README.md                          # This file
├── SKILL.md                           # Core skill definition (12KB)
│   ├── Core Principles
│   ├── 7-Phase Workflow
│   ├── Decision Trees
│   ├── Output Templates
│   ├── Interaction Guidelines
│   └── Example Dialogues
└── references/
    ├── code-patterns.md               # Code generation standards (12KB)
    │   ├── Stack Selection Guide
    │   ├── File Organization
    │   ├── Documentation Standards
    │   ├── Security Best Practices
    │   └── Testing Guidelines
    └── tech-explanations.md           # Technical glossary (10KB)
        ├── Architecture Concepts
        ├── Data Concepts
        ├── Deployment & Hosting
        ├── Mobile Development
        └── Security Basics
```

## Supported Platforms

| Platform | Stack | Complexity |
|----------|-------|------------|
| **Static Web App** | HTML/CSS/JS or React | ⭐ Easy |
| **Web App + Data** | React + Firebase | ⭐⭐ Moderate |
| **Full-Stack Web** | React + Node/Python + PostgreSQL | ⭐⭐⭐ Moderate |
| **Progressive Web App** | React + Service Worker | ⭐⭐ Moderate |
| **Android Native** | Kotlin + Jetpack Compose | ⭐⭐⭐⭐ Advanced |
| **iOS Native** | Swift + SwiftUI | ⭐⭐⭐⭐ Advanced |
| **Cross-Platform Mobile** | React Native or Flutter | ⭐⭐⭐ Moderate |

## Design Principles

### For the User

- **Zero assumed knowledge**: Every term explained in plain language
- **Socratic method**: Questions guide discovery, not dictation
- **Patience built-in**: No rushing; explore alternatives before deciding
- **Scope protection**: Actively prevent feature creep with MVP discipline
- **Celebration of progress**: Positive reinforcement at each milestone

### For the Code

- **Complete and runnable**: No TODO placeholders; everything works
- **Heavily documented**: Every file has a header; every function explained
- **Beginner-readable**: Clarity over cleverness; verbose over terse
- **Secure by default**: Input validation, parameterized queries, no hardcoded secrets
- **Modular structure**: Clean separation matching the feature breakdown

## Customization

### Adjusting Technical Depth

The skill defaults to beginner-friendly explanations. For users with some experience, modify the Core Principles section:

```markdown
## Core Principles
- **Calibrate to user level** — ask about experience; adjust depth accordingly
```

### Adding New Platforms

Extend `references/code-patterns.md` with additional stack definitions:

```markdown
### Stack H: [New Platform]

**Use case**: [When to use this]

\```
Frontend:     [Technology]
Backend:      [Technology]
Database:     [Technology]
\```
```

### Customizing Output Style

Modify the documentation templates in `references/code-patterns.md` to match your organization's standards.

## License

MIT — Free to use, modify, and distribute.

## Contributing

Suggestions, improvements, and bug reports welcome:

1. Fork the repository
2. Create a feature branch
3. Submit a pull request with clear description

## Acknowledgments

Built for the Claude ecosystem by developers who believe everyone should be able to bring their app ideas to life.
