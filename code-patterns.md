# Code Generation Patterns

Standards for generating well-documented, beginner-friendly, production-ready code.

---

## Recommended Stacks by App Type

### Quick Selection Guide

```
┌─────────────────────────────────────────────────────────────────────┐
│                    STACK SELECTION DECISION TREE                    │
└─────────────────────────────────────────────────────────────────────┘

Is this a web app or mobile app?
│
├─► WEB APP
│   │
│   ├─► No user data needed?
│   │   └─► STACK A: Static Web App
│   │
│   ├─► User data, but no accounts?
│   │   └─► STACK B: Web App with Anonymous Data
│   │
│   ├─► User accounts required?
│   │   ├─► Simple CRUD app → STACK C: Full-Stack Web App (Firebase)
│   │   └─► Complex logic → STACK D: Full-Stack Web App (Custom Backend)
│   │
│   └─► Real-time features needed?
│       └─► STACK E: Real-Time Web App
│
└─► MOBILE APP
    │
    ├─► Single platform (iOS OR Android)?
    │   └─► STACK F: Native Mobile App
    │
    └─► Both platforms needed?
        └─► STACK G: Cross-Platform Mobile App
```

---

### Stack A: Static Web App (No User Data)

**Use case**: Calculators, converters, portfolios, landing pages, documentation sites

```
Frontend:     HTML/CSS/JavaScript  OR  React
Build Tool:   Vite (if using React)
Hosting:      Vercel or Netlify (free tier)
```

**Example apps**: Tip calculator, unit converter, personal portfolio

**File structure**:
```
project-name/
├── index.html
├── styles.css
├── script.js
└── README.md
```

---

### Stack B: Web App with Anonymous Data

**Use case**: Apps that save data but don't need user accounts

```
Frontend:     React
State:        React useState/useReducer
Storage:      localStorage (device only) OR Firebase Firestore (cloud)
Hosting:      Vercel
```

**Example apps**: Todo list, notes app, local inventory tracker

**File structure**:
```
project-name/
├── src/
│   ├── components/
│   ├── hooks/
│   ├── utils/
│   ├── App.jsx
│   └── main.jsx
├── index.html
├── package.json
└── README.md
```

---

### Stack C: Full-Stack Web App (Firebase Backend)

**Use case**: Apps with user accounts where simplicity is priority

```
Frontend:     React
Backend:      Firebase (Firestore + Functions)
Auth:         Firebase Authentication
Hosting:      Vercel (frontend) + Firebase (backend)
```

**Example apps**: Personal journal, expense tracker, recipe collection

**File structure**:
```
project-name/
├── src/
│   ├── components/
│   ├── pages/
│   ├── hooks/
│   ├── services/
│   │   ├── firebase.js       # Firebase config
│   │   ├── auth.js           # Auth functions
│   │   └── database.js       # Firestore functions
│   ├── utils/
│   ├── App.jsx
│   └── main.jsx
├── functions/                 # Firebase Cloud Functions
│   ├── index.js
│   └── package.json
├── firebase.json
├── .env.example
├── package.json
└── README.md
```

---

### Stack D: Full-Stack Web App (Custom Backend)

**Use case**: Complex business logic, custom requirements, more control

```
Frontend:     React
Backend:      Node.js + Express  OR  Python + FastAPI
Database:     PostgreSQL (via Supabase or Railway)
Auth:         JWT tokens  OR  Supabase Auth
Hosting:      Vercel (frontend) + Railway (backend + database)
```

**Example apps**: Booking system, e-commerce, multi-tenant SaaS

**File structure**:
```
project-name/
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── hooks/
│   │   ├── services/
│   │   │   └── api.js        # API client
│   │   ├── utils/
│   │   ├── App.jsx
│   │   └── main.jsx
│   ├── package.json
│   └── vite.config.js
├── backend/
│   ├── routes/
│   │   ├── auth.js
│   │   ├── users.js
│   │   └── [resource].js
│   ├── models/
│   │   ├── User.js
│   │   └── [Resource].js
│   ├── middleware/
│   │   ├── auth.js
│   │   └── errorHandler.js
│   ├── utils/
│   ├── server.js
│   ├── package.json
│   └── .env.example
├── docs/
│   └── ARCHITECTURE.md
└── README.md
```

---

### Stack E: Real-Time Web App

**Use case**: Live collaboration, chat, live updates, multiplayer games

```
Frontend:     React
Backend:      Node.js + Socket.io  OR  Firebase Realtime Database
Database:     Firebase Realtime DB  OR  PostgreSQL + Redis
Hosting:      Railway (supports WebSockets)
```

**Example apps**: Chat app, live whiteboard, multiplayer game, live dashboard

---

### Stack F: Native Mobile App

**Use case**: Single platform with full device access requirements

**Android**:
```
Language:     Kotlin
UI:           Jetpack Compose
Architecture: MVVM
Build:        Gradle
IDE:          Android Studio
```

**iOS**:
```
Language:     Swift
UI:           SwiftUI
Architecture: MVVM
Build:        Xcode
IDE:          Xcode (macOS required)
```

---

### Stack G: Cross-Platform Mobile App

**Use case**: iOS + Android from single codebase

**Option 1: React Native** (if team knows JavaScript)
```
Framework:    React Native + Expo
Language:     TypeScript
Navigation:   React Navigation
State:        React Context  OR  Zustand
Backend:      Firebase  OR  Custom API
```

**Option 2: Flutter** (if starting fresh)
```
Framework:    Flutter
Language:     Dart
State:        Provider  OR  Riverpod
Backend:      Firebase  OR  Custom API
```

---

## File Organization Standards

### General Principles

1. **Group by feature** for large apps, **group by type** for small apps
2. **Flat structure** until a folder has 7+ files, then create subfolders
3. **Consistent naming**: Use the same convention throughout (camelCase, kebab-case, PascalCase)
4. **Index files**: Use `index.js` to simplify imports for folders with multiple exports

### React Project Structure (Standard)

```
src/
├── components/           # Reusable UI components
│   ├── common/          # Shared across features (Button, Input, Modal)
│   │   ├── Button.jsx
│   │   ├── Input.jsx
│   │   └── index.js     # Export all common components
│   └── [feature]/       # Feature-specific components
│       ├── FeatureCard.jsx
│       └── FeatureList.jsx
│
├── pages/               # Route-level components (one per route)
│   ├── HomePage.jsx
│   ├── DashboardPage.jsx
│   └── NotFoundPage.jsx
│
├── hooks/               # Custom React hooks
│   ├── useAuth.js
│   ├── useLocalStorage.js
│   └── index.js
│
├── services/            # External service integrations
│   ├── api.js           # HTTP client configuration
│   ├── auth.js          # Authentication functions
│   └── storage.js       # Data persistence
│
├── utils/               # Pure utility functions
│   ├── formatters.js    # Date, currency, string formatting
│   ├── validators.js    # Input validation
│   └── constants.js     # App-wide constants
│
├── context/             # React Context providers
│   ├── AuthContext.jsx
│   └── ThemeContext.jsx
│
├── assets/              # Static files
│   ├── images/
│   └── fonts/
│
├── styles/              # Global styles (if not using CSS-in-JS)
│   ├── global.css
│   └── variables.css
│
├── App.jsx              # Root component
├── main.jsx             # Entry point
└── routes.jsx           # Route definitions
```

### Node.js/Express Backend Structure

```
backend/
├── routes/              # API endpoint definitions
│   ├── index.js         # Route aggregator
│   ├── auth.routes.js
│   ├── users.routes.js
│   └── [resource].routes.js
│
├── controllers/         # Request handlers (business logic)
│   ├── auth.controller.js
│   ├── users.controller.js
│   └── [resource].controller.js
│
├── models/              # Database schemas/models
│   ├── User.model.js
│   └── [Resource].model.js
│
├── middleware/          # Express middleware
│   ├── auth.middleware.js      # JWT verification
│   ├── validate.middleware.js  # Input validation
│   └── error.middleware.js     # Error handling
│
├── services/            # External service integrations
│   ├── email.service.js
│   └── payment.service.js
│
├── utils/               # Utility functions
│   ├── logger.js
│   └── helpers.js
│
├── config/              # Configuration
│   ├── database.js
│   └── constants.js
│
├── server.js            # App entry point
├── package.json
└── .env.example         # Environment variable template
```

---

## Documentation Standards

### File Header Template

Every file must start with a header explaining its purpose.

**JavaScript/React**:
```javascript
/**
 * ═══════════════════════════════════════════════════════════════════════
 * FILE: ComponentName.jsx
 * PURPOSE: [One sentence describing what this file does]
 * ═══════════════════════════════════════════════════════════════════════
 *
 * [2-3 sentences providing more context about functionality]
 *
 * FEATURES:
 * - [Feature 1 this file implements]
 * - [Feature 2 this file implements]
 *
 * CONNECTIONS:
 * - Imports: [key dependencies]
 * - Used by: [parent components or callers]
 *
 * ═══════════════════════════════════════════════════════════════════════
 */
```

**Python**:
```python
"""
═══════════════════════════════════════════════════════════════════════════
FILE: module_name.py
PURPOSE: [One sentence describing what this file does]
═══════════════════════════════════════════════════════════════════════════

[2-3 sentences providing more context about functionality]

FEATURES:
- [Feature 1 this file implements]
- [Feature 2 this file implements]

CONNECTIONS:
- Imports: [key dependencies]
- Used by: [calling modules]

═══════════════════════════════════════════════════════════════════════════
"""
```

### Function Documentation

**JavaScript (JSDoc)**:
```javascript
/**
 * Calculates the total price including tax and discounts.
 *
 * Takes a list of items and applies any applicable discounts before
 * adding the appropriate tax rate based on the user's location.
 *
 * @param {Array<Object>} items - Array of items with price and quantity
 * @param {number} items[].price - Unit price of the item
 * @param {number} items[].quantity - Number of items
 * @param {string} taxRegion - Region code for tax calculation (e.g., 'US-CA')
 * @param {string} [discountCode] - Optional discount code to apply
 * @returns {Object} Calculated totals
 * @returns {number} returns.subtotal - Sum before tax
 * @returns {number} returns.tax - Tax amount
 * @returns {number} returns.discount - Discount amount (0 if none)
 * @returns {number} returns.total - Final total
 *
 * @example
 * const items = [{ price: 10.00, quantity: 2 }, { price: 5.00, quantity: 1 }];
 * const result = calculateTotal(items, 'US-CA', 'SAVE10');
 * // { subtotal: 25.00, tax: 2.19, discount: 2.50, total: 24.69 }
 *
 * @throws {Error} If items array is empty
 * @throws {Error} If taxRegion is not recognized
 */
function calculateTotal(items, taxRegion, discountCode = null) {
  // Implementation
}
```

**Python (Docstring)**:
```python
def calculate_total(
    items: list[dict],
    tax_region: str,
    discount_code: str | None = None
) -> dict:
    """
    Calculate the total price including tax and discounts.

    Takes a list of items and applies any applicable discounts before
    adding the appropriate tax rate based on the user's location.

    Args:
        items: List of items, each with 'price' and 'quantity' keys.
        tax_region: Region code for tax calculation (e.g., 'US-CA').
        discount_code: Optional discount code to apply.

    Returns:
        Dictionary with keys:
        - subtotal: Sum before tax
        - tax: Tax amount
        - discount: Discount amount (0 if none)
        - total: Final total

    Raises:
        ValueError: If items list is empty.
        KeyError: If tax_region is not recognized.

    Example:
        >>> items = [{'price': 10.00, 'quantity': 2}, {'price': 5.00, 'quantity': 1}]
        >>> calculate_total(items, 'US-CA', 'SAVE10')
        {'subtotal': 25.00, 'tax': 2.19, 'discount': 2.50, 'total': 24.69}
    """
    # Implementation
```

### Inline Comments

**When to comment**:
- Non-obvious business logic
- Workarounds for bugs or edge cases
- Complex algorithms
- Security-critical code
- "Why" not "what"

**Examples**:
```javascript
// BAD: Describes what the code does (obvious from reading it)
const total = price + tax; // Add price and tax

// GOOD: Explains WHY
const total = price + tax; // Tax must be included per state law AB-1234

// GOOD: Documents a workaround
// Safari doesn't support date input type, so we use a polyfill
// See: https://bugs.webkit.org/show_bug.cgi?id=119175
import DatePolyfill from 'date-polyfill';

// GOOD: Explains complex logic
// Using binary search here because the list is always sorted and
// we need O(log n) performance for lists up to 1M items
const index = binarySearch(sortedList, target);

// GOOD: Security-critical explanation
// Rate limit login attempts to prevent brute force attacks
// After 5 failures, require CAPTCHA; after 10, lock for 15 minutes
if (failedAttempts >= 5) {
  requireCaptcha = true;
}
```

---

## README Template

Every project must include a comprehensive README:

```markdown
# [App Name]

[One sentence describing what the app does and who it's for.]

![Screenshot](./docs/screenshot.png)

## Features

- **[Feature 1]**: [What it does and why it's useful]
- **[Feature 2]**: [What it does and why it's useful]
- **[Feature 3]**: [What it does and why it's useful]

## Quick Start

### Prerequisites

Before you begin, make sure you have:

- **Node.js** (v18 or higher) - [Download here](https://nodejs.org)
- **npm** (comes with Node.js) or **yarn**
- **Git** - [Download here](https://git-scm.com)

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/username/project-name.git
   cd project-name
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Set up environment variables**
   ```bash
   cp .env.example .env
   # Edit .env with your values (see Configuration section)
   ```

4. **Start the development server**
   ```bash
   npm run dev
   ```

5. **Open in browser**
   Navigate to `http://localhost:5173`

## Configuration

Create a `.env` file with the following variables:

| Variable | Description | Required | Example |
|----------|-------------|----------|---------|
| `DATABASE_URL` | PostgreSQL connection string | Yes | `postgres://user:pass@host:5432/db` |
| `JWT_SECRET` | Secret for signing tokens | Yes | `your-secret-key-here` |
| `API_KEY` | Third-party API key | No | `sk_live_abc123` |

## Project Structure

```
project-name/
├── src/
│   ├── components/    # Reusable UI components
│   ├── pages/         # Route-level components
│   ├── hooks/         # Custom React hooks
│   ├── services/      # API and external services
│   └── utils/         # Helper functions
├── backend/           # Server code
└── docs/              # Documentation
```

## Architecture

```
┌──────────────┐      HTTP       ┌──────────────┐      SQL       ┌──────────────┐
│   Frontend   │ ──────────────► │   Backend    │ ─────────────► │   Database   │
│   (React)    │ ◄────────────── │  (Express)   │ ◄───────────── │ (PostgreSQL) │
└──────────────┘      JSON       └──────────────┘     Data       └──────────────┘
```

## API Reference

### Authentication

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/api/auth/register` | POST | Create new account |
| `/api/auth/login` | POST | Sign in |
| `/api/auth/logout` | POST | Sign out |

### Resources

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/api/items` | GET | List all items |
| `/api/items/:id` | GET | Get single item |
| `/api/items` | POST | Create item |
| `/api/items/:id` | PUT | Update item |
| `/api/items/:id` | DELETE | Delete item |

## Deployment

### Deploy to Vercel (Frontend)

1. Push code to GitHub
2. Connect repository to [Vercel](https://vercel.com)
3. Set environment variables in Vercel dashboard
4. Deploy

### Deploy to Railway (Backend)

1. Push code to GitHub
2. Create new project in [Railway](https://railway.app)
3. Add PostgreSQL database
4. Set environment variables
5. Deploy

## Common Modifications

### Adding a new page

1. Create component in `src/pages/NewPage.jsx`
2. Add route in `src/routes.jsx`
3. Add navigation link in `src/components/Navbar.jsx`

### Adding a new API endpoint

1. Create route in `backend/routes/newRoute.routes.js`
2. Create controller in `backend/controllers/newRoute.controller.js`
3. Register in `backend/routes/index.js`

## Troubleshooting

### "Module not found" error

**Cause**: Dependencies not installed
**Fix**: Run `npm install`

### "ECONNREFUSED" database error

**Cause**: Database not running
**Fix**: Start PostgreSQL service or check DATABASE_URL

### Blank page after deployment

**Cause**: Environment variables not set
**Fix**: Check all required env vars are configured in hosting dashboard

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit changes (`git commit -m 'Add amazing feature'`)
4. Push to branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## License

[MIT](LICENSE)
```

---

## Security Best Practices

### Never Do

```javascript
// ❌ NEVER: Hardcode secrets in code
const API_KEY = "sk_live_abc123xyz";

// ❌ NEVER: Concatenate SQL queries
const query = `SELECT * FROM users WHERE id = ${userId}`;

// ❌ NEVER: Trust user input
const html = `<div>${userInput}</div>`;

// ❌ NEVER: Store passwords in plain text
await db.insert({ password: userPassword });

// ❌ NEVER: Expose stack traces to users
app.use((err, req, res, next) => {
  res.status(500).json({ error: err.stack }); // Shows internal details!
});
```

### Always Do

```javascript
// ✅ ALWAYS: Use environment variables
const API_KEY = process.env.API_KEY;

// ✅ ALWAYS: Use parameterized queries
const query = `SELECT * FROM users WHERE id = $1`;
await db.query(query, [userId]);

// ✅ ALWAYS: Sanitize output
const html = `<div>${escapeHtml(userInput)}</div>`;

// ✅ ALWAYS: Hash passwords
const hashedPassword = await bcrypt.hash(userPassword, 12);
await db.insert({ password: hashedPassword });

// ✅ ALWAYS: Generic error messages in production
app.use((err, req, res, next) => {
  console.error(err); // Log internally
  res.status(500).json({ error: 'Something went wrong' }); // Generic to user
});
```

### Input Validation Template

```javascript
/**
 * Validates user registration input.
 * @param {Object} input - Registration data
 * @returns {Object} { valid: boolean, errors: string[] }
 */
function validateRegistration(input) {
  const errors = [];

  // Email validation
  if (!input.email) {
    errors.push('Email is required');
  } else if (!/^[^\s@]+@[^\s@]+\.[^\s@]+$/.test(input.email)) {
    errors.push('Email format is invalid');
  }

  // Password validation
  if (!input.password) {
    errors.push('Password is required');
  } else if (input.password.length < 8) {
    errors.push('Password must be at least 8 characters');
  } else if (!/[A-Z]/.test(input.password)) {
    errors.push('Password must contain at least one uppercase letter');
  } else if (!/[0-9]/.test(input.password)) {
    errors.push('Password must contain at least one number');
  }

  // Name validation
  if (!input.name) {
    errors.push('Name is required');
  } else if (input.name.length > 100) {
    errors.push('Name must be 100 characters or less');
  }

  return {
    valid: errors.length === 0,
    errors
  };
}
```

---

## Testing Guidelines

### Manual Testing Checklist

Include a testing checklist in every project:

```markdown
## Testing Checklist

### Authentication
- [ ] Can register with valid email/password
- [ ] Cannot register with existing email (shows error)
- [ ] Cannot register with weak password (shows error)
- [ ] Can log in with correct credentials
- [ ] Cannot log in with wrong password (shows error)
- [ ] Can log out
- [ ] Stays logged in after page refresh
- [ ] Cannot access protected pages when logged out

### Core Features
- [ ] Can create new [item]
- [ ] Can view list of [items]
- [ ] Can view single [item] details
- [ ] Can edit existing [item]
- [ ] Can delete [item] (with confirmation)
- [ ] Empty states show helpful message

### Edge Cases
- [ ] Handles empty input gracefully
- [ ] Handles very long input
- [ ] Handles special characters
- [ ] Handles slow network (loading states)
- [ ] Handles network failure (error states)
- [ ] Works on mobile viewport
- [ ] Works in different browsers

### Security
- [ ] Cannot access other users' data
- [ ] Cannot inject HTML/scripts in inputs
- [ ] API endpoints require authentication
- [ ] Sensitive data not exposed in browser console
```

---

## Code Style Conventions

### JavaScript/React

```javascript
// File naming: PascalCase for components, camelCase for utilities
// ✅ UserProfile.jsx, useAuth.js, formatDate.js
// ❌ user-profile.jsx, UseAuth.js, FormatDate.js

// Component naming: PascalCase, descriptive
// ✅ UserProfileCard, LoginForm, DashboardPage
// ❌ Card1, Form, Page

// Function naming: camelCase, verb + noun
// ✅ getUserById, calculateTotal, formatDate
// ❌ user, total, date

// Constant naming: SCREAMING_SNAKE_CASE
// ✅ MAX_RETRY_ATTEMPTS, API_BASE_URL
// ❌ maxRetryAttempts, apiBaseUrl

// Boolean naming: is/has/should prefix
// ✅ isLoading, hasError, shouldRefetch
// ❌ loading, error, refetch
```

### Python

```python
# File naming: snake_case
# ✅ user_service.py, auth_middleware.py
# ❌ UserService.py, authMiddleware.py

# Class naming: PascalCase
# ✅ UserProfile, DatabaseConnection
# ❌ user_profile, database_connection

# Function/variable naming: snake_case
# ✅ get_user_by_id, calculate_total
# ❌ getUserById, calculateTotal

# Constant naming: SCREAMING_SNAKE_CASE
# ✅ MAX_RETRY_ATTEMPTS, API_BASE_URL
# ❌ maxRetryAttempts, api_base_url
```
