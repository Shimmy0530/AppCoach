# Technical Terms Explained

Plain-language explanations for non-technical users. Use these definitions when introducing concepts.

---

## Core Architecture Concepts

### Frontend

**What it is**: The part of the app users see and interact with — buttons, text, images, forms, and everything visual.

**Analogy**: Like the dashboard of a car. You see the speedometer, buttons, and steering wheel, but not the engine underneath.

**What it does**:
- Displays information to users
- Collects user input (forms, clicks, gestures)
- Sends requests to the backend
- Updates the display based on responses

**Common technologies**:

| Technology | Description | Difficulty | Best for |
|------------|-------------|------------|----------|
| **HTML/CSS/JS** | The foundational building blocks of all websites | ⭐ Easy | Simple sites, learning |
| **React** | Component-based library by Meta; most popular choice | ⭐⭐⭐ Moderate | Most web apps |
| **Vue** | Progressive framework; gentle learning curve | ⭐⭐ Easy-Moderate | Beginners wanting structure |
| **Svelte** | Compiles away; very fast, minimal code | ⭐⭐ Easy-Moderate | Performance-focused apps |
| **Flutter (Web)** | Google's cross-platform toolkit | ⭐⭐⭐⭐ Challenging | Cross-platform apps |

---

### Backend

**What it is**: The "brain" of the app that runs on a server — handles logic, processes data, enforces rules, and talks to the database.

**Analogy**: Like the kitchen in a restaurant. Customers (users) never see it, but it's where orders are processed and food is prepared.

**What it does**:
- Receives requests from the frontend
- Validates and processes data
- Applies business logic (rules like "users can only see their own data")
- Reads/writes to the database
- Returns responses to the frontend

**Common technologies**:

| Technology | Language | Difficulty | Best for |
|------------|----------|------------|----------|
| **Node.js + Express** | JavaScript | ⭐⭐ Easy-Moderate | Full-stack JS developers |
| **Python + FastAPI** | Python | ⭐⭐ Easy-Moderate | Clean APIs, data science |
| **Python + Django** | Python | ⭐⭐⭐ Moderate | Full-featured apps, admin panels |
| **Firebase Functions** | JavaScript | ⭐ Easy | Serverless, small apps |
| **Ruby on Rails** | Ruby | ⭐⭐⭐ Moderate | Rapid prototyping |
| **Go** | Go | ⭐⭐⭐⭐ Advanced | High-performance APIs |

---

### Database

**What it is**: Where all the app's information is stored permanently — survives restarts, updates, and user sessions.

**Analogy**: Like a filing cabinet or a giant spreadsheet that remembers everything even when you turn off the computer.

**Types explained**:

| Type | How it works | Analogy | Best for |
|------|--------------|---------|----------|
| **SQL (Relational)** | Data in tables with rows and columns; tables can reference each other | Excel spreadsheets with formulas linking between tabs | Structured data with clear relationships |
| **NoSQL (Document)** | Data stored as flexible documents (like JSON files) | Folders full of sticky notes that can contain anything | Flexible schemas, rapid development |
| **Key-Value** | Simple pairs: a key (name) points to a value (data) | A dictionary or phone book | Caching, simple lookups, sessions |
| **Graph** | Data as nodes connected by relationships | Social network map | Complex relationships, recommendations |

**Common databases**:

| Database | Type | Difficulty | Best for |
|----------|------|------------|----------|
| **Firebase Firestore** | NoSQL (Document) | ⭐ Easy | Beginners, real-time apps |
| **PostgreSQL** | SQL (Relational) | ⭐⭐ Moderate | Most production apps |
| **MySQL** | SQL (Relational) | ⭐⭐ Moderate | Traditional web apps |
| **MongoDB** | NoSQL (Document) | ⭐⭐ Moderate | Flexible schemas |
| **SQLite** | SQL (Relational) | ⭐ Easy | Local/embedded databases |
| **Redis** | Key-Value | ⭐⭐ Moderate | Caching, sessions |

---

### API (Application Programming Interface)

**What it is**: A way for different parts of your app (or different apps entirely) to talk to each other using a defined set of rules.

**Analogy**: Like a waiter in a restaurant — takes your order (request), brings it to the kitchen (server), and returns with your food (response). The menu is the API documentation.

**Common types**:

| Type | How it works | Analogy | Best for |
|------|--------------|---------|----------|
| **REST API** | Use URLs to request resources; different actions (GET, POST, PUT, DELETE) for different operations | Asking specific questions with URLs | Most web/mobile apps |
| **GraphQL** | Ask for exactly the data you need in a single request | Ordering a custom meal with specific ingredients | Complex data needs, mobile apps |
| **WebSocket** | Keeps a connection open for real-time two-way communication | A phone call (vs. text messages) | Chat, live updates, games |

**REST API example** (plain English):
```
GET  /api/books        → "Give me all the books"
GET  /api/books/123    → "Give me the book with ID 123"
POST /api/books        → "Create a new book with this information"
PUT  /api/books/123    → "Update book 123 with this new information"
DELETE /api/books/123  → "Delete book 123"
```

---

### Authentication vs. Authorization

**Authentication** (AuthN): *Who are you?*
- Verifying identity (login)
- "Prove you are who you claim to be"

**Authorization** (AuthZ): *What can you do?*
- Checking permissions after login
- "Now that I know who you are, here's what you're allowed to access"

**Analogy**: 
- Authentication = Showing your ID at a building entrance
- Authorization = Your ID determines which floors you can access

**Common authentication methods**:

| Method | How it works | Pros | Cons |
|--------|--------------|------|------|
| **Email/Password** | Traditional username + password | Familiar to users, full control | You manage security, password resets |
| **OAuth** | "Sign in with Google/Apple/GitHub" | Easy for users, fewer passwords | Depends on third party |
| **Magic Link** | Email a one-time login link | No password to forget | Requires email access each time |
| **Passkeys** | Biometric or device-based authentication | Most secure, no passwords | Newer, not universal yet |
| **Two-Factor (2FA)** | Password + second verification | Much more secure | Slight friction for users |

---

## Data Concepts

### CRUD Operations

**What it is**: The four basic operations you can do with data.

| Letter | Operation | What it does | Example |
|--------|-----------|--------------|---------|
| **C** | Create | Add new data | Sign up a new user |
| **R** | Read | Retrieve existing data | View your profile |
| **U** | Update | Modify existing data | Edit your email address |
| **D** | Delete | Remove data | Delete your account |

**Analogy**: Like managing contacts on your phone — you can add new contacts, look them up, edit their info, or delete them.

---

### Data Validation

**What it is**: Checking that data meets certain rules before accepting it.

**Why it matters**: 
- Prevents errors (empty required fields)
- Prevents attacks (malicious input)
- Ensures data quality

**Examples**:
- Email must contain "@" and a domain
- Password must be at least 8 characters
- Age must be a positive number
- Date must be in the future (for appointments)

**Analogy**: Like a bouncer at a club checking IDs — wrong format? You don't get in.

---

### Data Relationships

**What it is**: How different pieces of data connect to each other.

| Relationship | Meaning | Example |
|--------------|---------|---------|
| **One-to-One** | Each A has exactly one B | User ↔ Profile |
| **One-to-Many** | One A has multiple Bs | Author → Books |
| **Many-to-Many** | Multiple As connect to multiple Bs | Students ↔ Classes |

**Analogy**: 
- One-to-One: Person and their driver's license
- One-to-Many: Mother and her children
- Many-to-Many: Actors and movies (actors appear in many movies; movies have many actors)

---

## Architecture Patterns

### Client-Server Model

**What it is**: The fundamental pattern where users' devices (clients) request things from a central computer (server).

```
┌──────────┐                      ┌──────────┐
│  Client  │ ───── request ─────► │  Server  │
│ (Browser)│ ◄──── response ───── │ (Backend)│
└──────────┘                      └──────────┘
```

**Analogy**: Like ordering at a restaurant. You (client) make a request, the kitchen (server) prepares it, and sends it back.

---

### Single Page Application (SPA)

**What it is**: An app that loads once and updates dynamically without refreshing the entire page.

**How it feels**: Smooth, app-like experience; clicking around doesn't cause page reloads.

**Analogy**: Like changing TV channels — the TV stays on, just the content changes.

**Technologies**: React, Vue, Angular, Svelte

---

### Server-Side Rendering (SSR)

**What it is**: The server builds the complete page before sending it to the user.

**Why it matters**: 
- Faster initial page load
- Better for search engines (SEO)
- Works without JavaScript

**Analogy**: Getting a fully cooked meal delivered vs. receiving ingredients to cook yourself.

**Technologies**: Next.js (React), Nuxt (Vue), SvelteKit

---

### Progressive Web App (PWA)

**What it is**: A web app enhanced to feel like a native mobile app.

**Features**:
- Can be "installed" on home screen
- Works offline (with limitations)
- Can send push notifications
- One codebase for web + mobile

**Analogy**: A website that wants to be an app when it grows up.

**Limitations**: Can't access all device features (some sensors, background tasks, etc.)

---

### Microservices vs. Monolith

| Architecture | What it is | Analogy | Best for |
|--------------|------------|---------|----------|
| **Monolith** | Everything in one codebase | A single restaurant that does everything | Small teams, early-stage apps |
| **Microservices** | Separate services for separate functions | Food court with specialized vendors | Large teams, complex systems |

**For beginners**: Always start with a monolith. Microservices add complexity that isn't needed until you have a large team and millions of users.

---

## Deployment & Hosting

### Hosting

**What it is**: Where your app "lives" on the internet so others can access it.

**Types**:

| Type | What it means | Analogy | Examples |
|------|---------------|---------|----------|
| **Static Hosting** | Serves files as-is; no server-side processing | A file cabinet anyone can read | Netlify, Vercel, GitHub Pages |
| **Server Hosting** | Runs your backend code | A kitchen that processes orders | Railway, Render, Heroku |
| **Serverless** | Code runs on-demand; you don't manage servers | Calling a taxi vs. owning a car | AWS Lambda, Vercel Functions |
| **Full Cloud** | Complete infrastructure you control | Building your own data center | AWS, GCP, Azure |

**Recommendation for beginners**: Start with Vercel (frontend) + Firebase or Railway (backend). Zero server management.

---

### Domain Names

**What it is**: Your app's human-readable address on the internet.

**Structure**: `subdomain.domain.tld`
- Example: `app.mycompany.com`
- `app` = subdomain
- `mycompany` = domain
- `com` = top-level domain (TLD)

**Where to buy**: Namecheap, Google Domains, Cloudflare

**Analogy**: Like a street address for your house. Without it, people have to remember a random string of numbers (IP address).

---

### SSL/HTTPS

**What it is**: Encryption that protects data between the user's browser and your server.

**Why it matters**:
- Prevents eavesdropping on sensitive data (passwords, credit cards)
- Required by browsers (shows padlock icon)
- Required for many APIs and features
- Better search engine ranking

**Analogy**: Like sending a letter in a locked box that only the recipient can open, vs. a postcard anyone can read.

**How to get it**: Most modern hosts (Vercel, Netlify, Railway) provide free SSL automatically.

---

### Environment Variables

**What it is**: Configuration values stored outside your code — secrets, API keys, settings that change between environments.

**Why it matters**:
- Keeps secrets out of code (critical for security!)
- Same code can run differently in development vs. production
- Easy to change settings without modifying code

**Example**:
```
DATABASE_URL=postgres://user:password@host:5432/db
API_KEY=sk_live_abc123xyz
DEBUG_MODE=false
```

**Analogy**: Like settings on your phone that change behavior without reinstalling apps.

**Critical rule**: NEVER commit `.env` files or secrets to version control (git).

---

## Mobile Development

### Native vs. Cross-Platform

| Approach | What it means | Technologies | Pros | Cons |
|----------|---------------|--------------|------|------|
| **Native** | Built specifically for one platform | Swift (iOS), Kotlin (Android) | Best performance, full device access | Separate codebases |
| **Cross-Platform** | One codebase, multiple platforms | React Native, Flutter | Write once, deploy everywhere | Some performance trade-offs |
| **Hybrid** | Web app wrapped in native shell | Ionic, Capacitor | Easiest if you know web | Worst performance |

---

### App Store Considerations

**For iOS (Apple App Store)**:
- Requires Apple Developer account ($99/year)
- Must be built on macOS with Xcode
- Review process takes 1-7 days
- Strict guidelines on content and functionality

**For Android (Google Play Store)**:
- Requires Google Play Developer account ($25 one-time)
- Can build on any operating system
- Review process usually faster
- More flexible guidelines

---

## Security Basics

### Input Validation

**What it is**: Never trust data from users; always check it meets your rules before processing.

**Why it matters**: Malicious users can send unexpected data to try to break your app or steal data.

**Rule**: Validate on both frontend (for user experience) AND backend (for security).

---

### SQL Injection

**What it is**: An attack where malicious input tricks your database into running unintended commands.

**Example attack**: Entering `'; DROP TABLE users; --` as a username

**Prevention**: Always use parameterized queries (prepared statements), never string concatenation.

```javascript
// BAD - vulnerable to injection
const query = `SELECT * FROM users WHERE name = '${userInput}'`;

// GOOD - parameterized query
const query = `SELECT * FROM users WHERE name = $1`;
db.query(query, [userInput]);
```

---

### Cross-Site Scripting (XSS)

**What it is**: An attack where malicious scripts are injected into pages viewed by other users.

**Prevention**: 
- Always escape/sanitize user-generated content before displaying
- Use frameworks that auto-escape (React, Vue)
- Set proper Content Security Policy headers

---

### HTTPS Everywhere

**Rule**: All production apps must use HTTPS. No exceptions.

**Why**: HTTP traffic can be intercepted and read by anyone on the network.

---

## Development Workflow

### Version Control (Git)

**What it is**: A system that tracks all changes to your code over time.

**Why it matters**:
- Undo mistakes by going back to previous versions
- Multiple people can work on the same code
- See who changed what and when
- Standard practice for all professional development

**Key concepts**:
- **Repository (repo)**: The folder containing your project and its history
- **Commit**: A snapshot of your code at a point in time
- **Branch**: A separate line of development
- **Merge**: Combining branches back together

**Analogy**: Like "Track Changes" in Word, but for your entire project.

---

### Local vs. Production Environment

| Environment | Purpose | Data | Performance |
|-------------|---------|------|-------------|
| **Local (Development)** | Building and testing on your computer | Fake/test data | Slower, more logging |
| **Staging** | Final testing before release | Copy of production data (anonymized) | Similar to production |
| **Production** | Live app used by real users | Real user data | Optimized, monitored |

**Rule**: Never test new features directly in production!

---

## Quick Reference: Complexity Guide

When explaining complexity to beginners, use this scale:

| Rating | Meaning | Can a beginner do it? |
|--------|---------|----------------------|
| ⭐ Easy | Minimal setup, clear documentation | Yes, with guidance |
| ⭐⭐ Easy-Moderate | Some setup required, mostly straightforward | Yes, with patience |
| ⭐⭐⭐ Moderate | Requires understanding of concepts | With significant guidance |
| ⭐⭐⭐⭐ Advanced | Multiple moving parts, debugging required | Not recommended for first app |
| ⭐⭐⭐⭐⭐ Expert | Deep expertise required | Hire a developer |
