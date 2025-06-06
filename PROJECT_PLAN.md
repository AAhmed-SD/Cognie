# Project Plan for FocusFlow

## Overview
FocusFlow is an AI-powered scheduling and productivity tool designed to help students and planners manage tasks, goals, and schedules efficiently. The application integrates with Google Calendar, Apple Calendar, and Notion, offering features like AI-synced scheduling, memory-aware task reviews, and dynamic rescheduling.

## Tech Stack

### Backend
- **Language**: Python
- **Framework**: FastAPI
- **AI/LLM Integration**: OpenAI API or local model via LangChain/LLMGuard
- **Memory Store**: Redis (short-term) + PostgreSQL (long-term structured memories)
- **Vector Store**: Weaviate or Qdrant
- **Scheduling/Tasks**: Celery with Redis or FastAPI BackgroundTasks

### Frontend
- **Framework**: Next.js (React)
- **Styling**: Tailwind CSS + shadcn/ui
- **State Management**: Zustand or TanStack Query
- **Realtime Sync**: Socket.IO or Pusher (optional)

### DevOps & Infrastructure
- **Cloud Provider**: Google Cloud Platform (GCP)
- **Storage**: Google Cloud Storage or Backblaze B2
- **Database**: Supabase (PostgreSQL + Auth + Storage)
- **CI/CD**: GitHub Actions or Railway built-ins
- **Monitoring**: Sentry for errors, Posthog for product analytics

### Auth, Payments, and Analytics
- **Auth**: Supabase Auth or Clerk.dev
- **Payments**: Stripe with metered billing or fixed tier plans
- **Analytics**: PostHog, Umami, or Plausible

## GCP Integration Plan
- **Compute Engine**: For running virtual machines and hosting backend services.
- **App Engine**: For building and deploying applications.
- **Cloud Storage**: For storing files and assets.
- **Cloud SQL**: Managed database service for PostgreSQL.
- **Cloud Functions**: For serverless execution of code.
- **AI and Machine Learning**: Use AI Platform for training and deploying models.
- **Cloud Pub/Sub**: For messaging and event-driven architectures.

## Next Steps
1. **Set Up GCP Account**: Ensure GCP account is set up and familiarize with the GCP Console.
2. **Configure Environment**: Integrate development environment with GCP services.
3. **Deploy Application**: Begin deploying backend services to GCP.
4. **Monitor and Optimize**: Use GCP's monitoring tools to track performance and optimize the application.

This plan outlines the comprehensive approach to building and deploying FocusFlow, leveraging modern technologies and GCP's robust infrastructure.

## 📧 Weekly Email Progress Reports

- Implement tracking for user activities such as tasks completed, time spent, and goals achieved.
- Store user data in the database for generating reports.
- Create scripts to aggregate user data weekly.
- Design email templates with HTML/CSS for visual appeal.
- Choose an email service provider (ESP) for email delivery.
- Integrate the application with the chosen ESP for sending emails.
- Automate email generation and sending with a task scheduler.
- Personalize emails with user-specific data.
- Allow users to opt-in or out of receiving emails.
- Ensure data privacy and security, complying with regulations like GDPR.
- Conduct A/B testing and gather feedback for optimization.

## FastAPI Endpoints Plan

### AI Tasks & Memory
- `/generate-flashcards`: Turn raw notes or textbook content into flashcards.
- `/daily-brief`: Generate a daily summary of tasks, priorities, missed tasks, and a reflection.
- `/quiz-me`: Takes a deck ID, returns 3–5 Qs from that deck to quiz the user.
- `/summarize-notes`: Compress long notes into key takeaways.
- `/suggest-reschedule`: Suggest new time + reasoning for missed task.
- `/extract-tasks-from-text`: User brain-dumps a paragraph, AI extracts structured tasks.

### Planning
- `/plan-my-day`: Auto-generate time blocks for a day.
- `/goals`: Create and track high-level goals.
- `/schedule`: Manage scheduled blocks.

### Memory Engine
- `/flashcards`: CRUD operations for flashcards.

### Insights
- `/user-insights`: Return trends, missed patterns, overbooking, etc.
- `/ai-feedback`: GPT reviews your week.

### Utility + UX
- `/notifications`: Basic create/delete for reminders.
- `/settings`: Save user energy preferences, focus hours, etc.

### Integration
- `/notion-sync`: Push/pull tasks and notes from Notion.

### Command UX (stretch)
- `/ai-command`: One endpoint for command-palette prompts. 