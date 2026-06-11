# Behavioral Finance Analytics

> **An AI-powered behavioral finance platform that transforms financial activity into actionable behavioral insights and personalized coaching.**

**Ebraz** is a behavioral finance analytics platform that bridges the gap between transactional data, emotional context, and financial decision-making. Traditional finance applications focus on recording expenses and categorizing transactions. Ebraz goes further by analyzing *why* people spend the way they do, identifying behavioral patterns, emotional triggers, and spending tendencies to help users build healthier financial habits.

By combining financial activity with emotional signals and large language models, Ebraz generates personalized coaching and behavioral insights tailored to each user's financial context.

## 🌟 The Problem Ebraz Solves

Most personal finance applications assume that financial decisions are rational and purely transactional. In reality, spending behavior is often influenced by stress, satisfaction, urgency, habits, cultural context, and impulse.

Ebraz addresses this gap by providing:

* **Behavioral Finance Analytics:** Analyze how emotions, intentions, and habits shape financial decisions.
* **AI-Generated Coaching:** Deliver personalized monthly guidance powered by OpenAI models.
* **Pattern Recognition:** Identify recurring emotional triggers and spending behaviors over time.
* **Context-Aware Analysis:** Incorporate regional financial realities such as inflation and currency fluctuations.
* **Decision Intelligence:** Transform raw transaction records into meaningful behavioral insights.

## 🚀 Key Capabilities

* Multi-currency financial tracking with real-time exchange rates
* Emotional tagging for financial activities
* AI-generated financial coaching reports
* Behavioral and intent-based spending analysis
* Comprehensive analytics across categories and emotional dimensions
* GraphQL API with JWT authentication
* Background processing for AI workloads using BullMQ

## 📊 Analytics & Intelligence

* Net balance and cash flow analysis
* Emotional spending distribution and trend detection
* Planned versus impulsive spending analysis
* Category-level financial behavior analytics
* Monthly AI-generated coaching reports
* Longitudinal behavioral pattern recognition

## 🛠️ Tech Stack

- **Backend**: NestJS + TypeScript + GraphQL + Apollo Server
- **Database**: MySQL + Prisma ORM
- **Caching**: Redis for performance optimization
- **Queue**: BullMQ for background AI processing
- **AI**: OpenAI API for intelligent insights generation

## 🔧 Development & Deployment

### Getting Started
```bash
# Install dependencies
pnpm install

# Set up environment variables
cp .env.example .env

# Run database migrations
pnpm dlx prisma migrate dev

# Start development server
pnpm run start:dev
```

### Available Scripts
- `pnpm run build` - Production build
- `pnpm run start:dev` - Development server with hot reload
- `pnpm run test` - Run test suite

### Docker Compose

Run the full stack (app + MySQL + Redis) with Docker Compose.

**1. Create secret files**

The compose setup uses Docker secrets for sensitive values. Create a `secrets/` directory and add one value per file:

```bash
mkdir -p secrets
echo 'your-db-password'       > secrets/db-password.secret.txt
echo 'your-db-root-password'  > secrets/db-root-password.secret.txt
echo 'your-jwt-secret-min-32' > secrets/jwt-secret.secret.txt
echo 'sk-proj-your-key'       > secrets/openai-api-key.secret.txt
```

> These files are git-ignored. Never commit them.

**2. Build the image**

```bash
docker build -t ebraz:0.0.0 .
```

**3. Start the stack**

```bash
docker compose up
```

This starts three containers:
- **ebraz-app** — the NestJS application on port `3000`
- **ebraz-mysql** — MySQL 8.0 with persistent data volume
- **ebraz-redis** — Redis with AOF persistence

Prisma migrations run automatically on each app start. Non-secret environment variables (port, Redis URL, cache TTL, etc.) are configured directly in `docker-compose.yaml`.


## 🔮 Future Roadmap

- **Data Visualization**: Interactive emotion-spending charts and graphs
- **Export & Backup**: Comprehensive data portability features
- **Social Features**: Optional community support and shared insights
- **Integration APIs**: Connect with local banks and financial institutions
- **Improvements**: Add logging mechanism, better caching and testing, etc.
