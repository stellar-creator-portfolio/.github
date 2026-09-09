<p align="center">
  <img src="stellar-creator.jpg" alt="Stellar Creator Portfolio" width="100%" />
</p>

# Stellar Creator Portfolio

**Creator Portfolio, Bounty Marketplace & Freelancing Hub on Stellar**

A professional platform connecting exceptional non-technical talent with opportunities, clients, and collaborators.

Showcase your work, discover bounties, find verified professionals, and coordinate freelance work with programmable payments powered by Stellar and Soroban.

---

## What we build

Stellar is an ecosystem designed specifically for **non-technical talent in the technology industry**.

Designers, writers, marketers, product managers, community professionals, sales specialists, and other creative or strategic professionals can use the platform to showcase their work, discover opportunities, connect with clients, and grow their careers.

> **The core question:** *How do we connect exceptional talent with meaningful opportunities while making the engagement and payment process transparent?*

Stellar combines creator portfolios, freelancer discovery, bounty-based work, and blockchain-powered escrow infrastructure into a single platform.

---

## Platform Features

### Creator Portfolios

Create beautiful, customizable professional profiles that showcase:

- Projects and previous work
- Professional biography and tagline
- Skills and areas of expertise
- Client and project statistics
- Testimonials and reputation
- LinkedIn and X/Twitter profiles
- Portfolio links

### Bounty Marketplace

Create and discover short-term, high-impact opportunities with transparent:

- Budgets
- Deadlines
- Difficulty levels
- Required skills
- Deliverables
- Application counts
- Bounty status

### Freelancer Directory

Discover professionals across **15+ non-technical technology disciplines**.

Search and filter talent by:

- Discipline
- Skills
- Experience
- Availability
- Expertise

Freelancers can expose service packages, rates, ratings, response times, and hiring information.

### Direct Networking

Connect directly with professionals through integrated social profiles, including LinkedIn and X/Twitter.

### Dark & Light Mode

Responsive interface with automatic theme detection and support for system, light, and dark themes.

---

## Supported Disciplines

Stellar supports talent across 15+ non-technical technology fields:

| Category | Disciplines |
| :--- | :--- |
| **Creative & Design** | UI/UX Design, Brand Strategy |
| **Content** | Writing, Content Creation |
| **Growth & Marketing** | Marketing, Community Management, Brand Strategy |
| **Product & Operations** | Product Management, Project Management, Business Development |
| **Data & Analytics** | Data Analysis |
| **Revenue & Sales** | Sales, Customer Success |
| **People & Legal** | HR & Recruiting, Legal & Compliance |

---

## Integrate With Stellar

### Creator Profiles

Build and manage professional creator profiles with structured portfolio data, projects, skills, experience, and social connections.

### Bounty Infrastructure

Create, discover, filter, and apply for bounties while tracking budgets, deadlines, required skills, deliverables, and application status.

### Escrow & Payments

Use Soroban smart contracts to coordinate project payments through escrow, milestone releases, refunds, timelocks, and multi-condition release mechanisms.

### API

A Rust-based REST API provides the integration layer between the frontend, platform services, and blockchain infrastructure.

---

## Stellar Infrastructure

Stellar is built on the **Stellar Network and Soroban**.

| Layer | Technology |
| :--- | :--- |
| **Frontend** | Next.js 16, TypeScript |
| **Framework** | Next.js App Router |
| **Styling** | Tailwind CSS v4 |
| **UI** | shadcn/ui |
| **Icons** | Lucide React |
| **Themes** | next-themes |
| **Blockchain** | Stellar Network |
| **Smart Contracts** | Rust + Soroban SDK |
| **API** | Rust + Actix-web |
| **Database** | PostgreSQL |
| **Cache** | Redis |
| **Indexer** | Custom Rust blockchain indexer |

The frontend uses Next.js 16 with Tailwind CSS, shadcn/ui, Lucide React, and TypeScript. The backend combines Soroban smart contracts with Rust-based services, PostgreSQL, Redis, and a custom blockchain event indexer.

---

## Smart Contracts

Stellar includes four core Soroban contracts:

### Bounty Contract

Manages the lifecycle of platform bounties:

- Create bounties with budgets and timelines
- Accept freelancer applications
- Track bounty status
- Select freelancers
- Manage completed, disputed, and cancelled work

### Escrow Contract

Provides secure payment coordination:

- Hold project funds in escrow
- Release funds based on milestones
- Support timelock-based releases
- Handle refunds
- Support multi-condition release mechanisms

### Freelancer Registry

Maintains talent and reputation information:

- Freelancer profiles
- Ratings and reviews
- Verification status
- Earnings history
- Project history

### Governance Contract

Provides platform-level governance:

- Configure platform fees
- Set bounty budget limits
- Vote on proposals
- Manage the platform treasury

---

## Project Structure

```text
stellar-platform/
├── app/                              # Next.js 16 Frontend
│   ├── page.tsx                      # Landing page
│   ├── layout.tsx                    # Root layout & theme provider
│   ├── globals.css                   # Global styles & design tokens
│   ├── creators/
│   │   ├── page.tsx                  # Creator directory
│   │   └── [id]/
│   │       ├── layout.tsx            # Creator profile layout
│   │       └── page.tsx              # Individual creator profile
│   ├── freelancers/
│   │   └── page.tsx                  # Freelancer directory
│   ├── bounties/
│   │   └── page.tsx                  # Bounty marketplace
│   └── about/
│       └── page.tsx                  # About & mission
│
├── components/
│   ├── header.tsx                    # Navigation & theme toggle
│   ├── footer.tsx                    # Footer & social links
│   ├── creator-card.tsx              # Creator profile card
│   ├── project-card.tsx              # Project showcase card
│   └── ui/                           # shadcn/ui components
│
├── lib/
│   └── creators-data.ts              # Sample data & utilities
│
├── public/
│   ├── avatars/                      # Creator avatars
│   ├── covers/                       # Creator cover images
│   └── projects/                     # Project images
│
└── backend/
    ├── contracts/
    │   ├── bounty/                   # Bounty management
    │   ├── escrow/                   # Payment escrow
    │   ├── freelancer/               # Freelancer registry
    │   └── governance/               # Platform governance
    │
    ├── services/
    │   ├── api/                      # REST API
    │   ├── auth/                     # Authentication
    │   ├── notifications/            # Notifications
    │   └── indexer/                  # Blockchain indexer
    │
    ├── Cargo.toml                    # Rust workspace
    ├── docker-compose.yml            # Backend orchestration
    └── README.md                     # Backend documentation
```

---

## Core Data Models

### Creator

```typescript
interface Creator {
  id: string;
  name: string;
  title: string;
  discipline: string;
  bio: string;
  avatar: string;
  coverImage: string;
  tagline: string;
  linkedIn: string;
  twitter: string;
  portfolio?: string;
  projects: Project[];
  skills: string[];
  stats: {
    projects: number;
    clients: number;
    experience: number;
  };
  services?: Service[];
  hourlyRate?: number;
  responseTime?: string;
  availability?: 'available' | 'limited' | 'unavailable';
  rating?: number;
  reviewCount?: number;
}
```

### Bounty

```typescript
interface Bounty {
  id: string;
  title: string;
  description: string;
  budget: number;
  currency: string;
  deadline: Date;
  difficulty: 'beginner' | 'intermediate' | 'advanced' | 'expert';
  category: string;
  tags: string[];
  applicants: number;
  status: 'open' | 'in-progress' | 'completed' | 'cancelled';
  requiredSkills: string[];
  deliverables: string;
}
```

### Service

```typescript
interface Service {
  id: string;
  name: string;
  description: string;
  category: string;
  basePrice: number;
  deliveryTime: number;
  rating: number;
  reviewCount: number;
}
```

---

## Pages & Routes

| Route | Description |
| :--- | :--- |
| `/` | Landing page with hero, featured creators, and platform benefits |
| `/creators` | Creator directory with discipline filtering |
| `/creators/[id]` | Individual creator portfolio and collaboration CTA |
| `/freelancers` | Freelancer discovery and hiring interface |
| `/bounties` | Bounty marketplace with filters |
| `/about` | Platform mission, values, and information |

---

## Creator Experience

A creator can:

1. Build a professional profile
2. Showcase projects and skills
3. Connect social profiles
4. Discover relevant opportunities
5. Apply for bounties
6. Offer services
7. Build reputation through ratings and reviews
8. Track projects and earnings

---

## Client Experience

Clients and organizations can:

1. Discover qualified professionals
2. Search by discipline and skills
3. Review portfolios and experience
4. Post bounties
5. Receive freelancer applications
6. Select professionals
7. Coordinate project milestones
8. Release payments through escrow

---

## Bounty Lifecycle

```text
Create Bounty
      ↓
Publish Opportunity
      ↓
Freelancers Apply
      ↓
Select Freelancer
      ↓
Project Begins
      ↓
Milestones / Deliverables
      ↓
Approval
      ↓
Escrow Release
      ↓
Project Completed
```

The platform's Soroban contracts provide the underlying mechanisms for bounty status management, escrow, milestone releases, refunds, and dispute-related flows.

---

## Design System

### Light Mode

- **Primary:** Deep Indigo-Blue — `oklch(0.35 0.15 250)`
- **Accent:** Vibrant Teal — `oklch(0.6 0.15 200)`
- **Secondary:** Soft Slate — `oklch(0.5 0.05 240)`
- **Muted:** Light Gray — `oklch(0.92 0 0)`

### Dark Mode

- **Primary:** Bright Indigo — `oklch(0.65 0.18 255)`
- **Accent:** Bright Cyan-Teal — `oklch(0.7 0.18 190)`
- **Secondary:** Soft Grayish-Blue — `oklch(0.35 0.08 240)`
- **Muted:** Dark Gray — `oklch(0.28 0.02 240)`

### Typography

**Geist** is used for both headings and body text.

The interface follows a 4px base spacing system, responsive breakpoints, Flexbox-first layouts, and a maximum container width of `7xl / 80rem`.

---

## Getting Started

### Prerequisites

- Node.js 18+ (20+ recommended)
- npm, pnpm, yarn, or bun

### Installation

```bash
git clone https://github.com/yourusername/stellar-platform.git
cd stellar-platform
```

### Install Dependencies

```bash
pnpm install

# or
npm install

# or
yarn install

# or
bun install
```

### Run Development Server

```bash
pnpm dev
```

Open `http://localhost:3000` in your browser.

### Production Build

```bash
pnpm build
pnpm start
```

---

## Backend

The backend consists of Soroban smart contracts and Rust services providing the infrastructure required for blockchain interaction and frontend integration.

### Run API

```bash
cd backend
cargo run --bin stellar-api
```

The API runs on:

```text
http://localhost:3001
```

### Key API Endpoints

```text
POST /api/bounties
GET  /api/bounties
POST /api/bounties/:id/apply

POST /api/freelancers/register
GET  /api/freelancers

POST /api/escrow/:id/release
```

### Run Full Backend Stack

```bash
cd backend
docker-compose up
```

Services:

```text
API:        http://localhost:3001
pgAdmin:    http://localhost:5050
PostgreSQL: localhost:5432
Redis:      localhost:6379
```

---

## Smart Contract Development

Build all contracts:

```bash
cd backend
cargo build --release
```

Run tests:

```bash
cargo test
```

Deploy the bounty contract to Stellar Testnet:

```bash
cd contracts/bounty
stellar contract deploy --network testnet --source account-name
```

---

## Deployment

### Vercel

1. Push the repository to GitHub
2. Import the repository into Vercel
3. Deploy automatically on every push

Or deploy using:

```bash
vercel --prod
```

### Other Platforms

The application can also be deployed to Node.js-compatible platforms including:

- Netlify
- AWS Amplify
- Railway
- Render
- DigitalOcean

Build:

```bash
pnpm build
```

Start:

```bash
NODE_ENV=production pnpm start
```

---

## Environment Variables

The base installation does not currently require environment variables.

Future integrations may use:

```env
DB_ENGINE=postgresql
DATABASE_URL=
NEXT_PUBLIC_API_URL=
AUTH_SECRET=
STRIPE_API_KEY=
```

Production deployments should provision PostgreSQL and configure `DATABASE_URL`. SQLite remains available for local development and testing.

---

## Roadmap

### Phase 1 — Platform Foundation

- Creator portfolio experience
- Creator and freelancer directories
- Bounty marketplace
- Soroban bounty, escrow, freelancer, and governance contracts
- Stellar wallet authentication
- Frontend/API integration

### Phase 2 — Payments & Reputation

- Payment processing
- Escrow integration
- Ratings and reviews
- Freelancer verification
- Blockchain event indexing

### Phase 3 — Collaboration

- Mobile application
- Real-time blockchain notifications
- Milestone-based payments
- Dispute resolution

### Phase 4 — Creator Economy

- Portfolio analytics
- Creator verification and reputation NFTs
- Third-party API integrations
- Decentralized governance

The source roadmap describes these capabilities across the Q1–Q4 phases, including wallet authentication, escrow, ratings, indexing, milestone payments, dispute resolution, reputation NFTs, APIs, and governance.

---

## Future Infrastructure

Planned extensions include:

- User accounts and authentication
- Creator dashboards
- Bounty applications and messaging
- Payment integrations
- Reviews and ratings
- Saved search filters
- Creator verification badges
- Portfolio analytics
- Email notifications
- Social sharing
- Public API
- Administrative dashboard
- Real-time messaging
- Live bounty updates
- Live bidding

---

## Contributing

Contributions are welcome.

```bash
git checkout -b feature/amazing-feature
git commit -m "Add amazing feature"
git push origin feature/amazing-feature
```

Then open a Pull Request.

---

## License

This project is licensed under the **MIT License**.

---

## Support

For issues, questions, or suggestions:

- Open an issue on GitHub
- Contact via LinkedIn
- Email: support@stellar.dev

---

## Acknowledgments

Built with:

- Next.js
- Tailwind CSS
- shadcn/ui
- Lucide React
- Stellar Network
- Soroban
- Rust
- Actix-web
- PostgreSQL
- Redis

---

**Start your journey on Stellar today — where exceptional talent meets extraordinary opportunities.**
