# NovaNews Architecture Note

## 1. Project Overview
NovaNews is a full-stack multi-user news dashboard where users can browse the latest headlines, search/filter news by category or keyword, generate AI summaries for articles, save articles to a personal library, and revisit saved articles later.

## 2. MVP Scope
The MVP includes:
- Home page with latest headlines
- Search/filter by category or keyword
- AI summary button on each news card
- Link to the original full article
- Signup/login with email and password
- Save article functionality for authenticated users
- My Library page with saved articles and associated summaries

Out of scope for MVP:
- Deployment
- Docker
- OAuth
- Advanced system design
- Microservices

## 3. Pages
- Home
- Auth
- My Library

## 4. Core Features
- Browse latest headlines
- Search/filter news
- Generate AI summary for an article
- Open original article link
- Sign up / log in
- Save article
- View saved articles and summaries

## 5. Backend Route Groups
- `auth`
- `news`
- `summaries`
- `saved`

### Example Endpoints
- `POST /auth/signup`
- `POST /auth/login`
- `GET /news/top-headlines`
- `GET /news/search`
- `POST /summaries`
- `POST /saved`
- `GET /saved`

## 6. Database Tables
### `users`
Stores user account data.
Suggested fields:
- `id`
- `email`
- `password_hash`
- `created_at`

### `saved_articles`
Stores articles saved by authenticated users.
Suggested fields:
- `id`
- `user_id`
- `title`
- `url`
- `source`
- `image_url`
- `summary`
- `published_at`
- `saved_at`

## 7. Data Flow
User actions start in the frontend. The frontend sends requests to the backend. The backend handles authentication, database access, and external API calls. News data is fetched from the News API, summaries are generated using the LLM API, and saved article data is stored in PostgreSQL. The backend returns responses to the frontend for display.

## 8. Stack
- Frontend: React
- Backend: FastAPI
- Database: PostgreSQL
- News API: NewsAPI or similar headlines/search provider
- LLM API: Gemini

## 9. Repo Structure
```text
novanews/
  frontend/
  backend/
  README.md
  ARCHITECTURE.md
