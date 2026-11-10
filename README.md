CareerBreak AI
CareerBreak AI is a career-restart support platform designed to help
women returning to the workforce after a career break. It brings
career-planning resources into one place, including resume management,
skill tracking, career roadmaps, interview practice and job discovery.
Project status: This repository contains a working application
prototype. Some guidance and analysis experiences currently use
predefined or demo content; they should not be described as live
AI-powered analysis unless an actual AI service is integrated.

Table of Contents
- Overview
- Features
- Technology Stack
- Application Architecture
- Getting Started
- Environment Variables
- Database and Authentication
- Available Scripts
- Testing
- Security Notes
- Future Improvements
- Contributing
Overview
Returning to work after a career break can involve several challenges:
identifying relevant skills, updating a resume, planning a learning path
and preparing for interviews. CareerBreak AI aims to make this process
easier through a single web application where users can organise their
career-re-entry activities.
Features
The application includes the following modules:
- User authentication: Sign-up, sign-in and sign-out using
  Supabase Auth.
- Dashboard: A central view of career progress and application
  activity.
- Resume management: Resume upload and an analysis-results
  interface. The current analysis experience uses demo/predefined
  results.
- Career roadmaps: Structured career-planning templates, including
  short- and longer-term plans.
- Skills tracker: Select and track skills relevant to a target
  career path.
- Interview preparation: Practice using a question bank and record
  practice activity.
- Job discovery: Browse, search and filter job opportunities.
- Career-break guidance: View guidance and sample explanations for
  discussing a career break.
- Profile management: Maintain user-specific career information.
Feature availability and data behaviour may depend on the configured
Supabase project.
Technology Stack
  Area                   Technologies
  Frontend               React 18, TypeScript
Build tooling          Vite
Styling                Tailwind CSS
UI components          shadcn/ui, Radix UI
Routing                React Router
Backend services       Supabase
Database               Supabase PostgreSQL
Authentication         Supabase Auth
Data fetching/state    TanStack React Query
Forms and validation   React Hook Form, Zod
Charts                 Recharts
Testing tools          Vitest, Testing Library
Code quality           ESLint
Package manager        npm or Bun
Application Architecture
CareerBreak AI is a client-side React application built with TypeScript
and Vite. It uses Supabase as its hosted backend service for
authentication and database access.

At a high level:
1. The React frontend presents the dashboard and career-support
   modules.
2. Supabase Auth manages user authentication and sessions.
3. The frontend communicates with the Supabase project for supported
   data operations.
4. PostgreSQL stores application data such as profiles, resumes,
   skills, roadmap tasks, interview sessions, achievements and job
   records.
5. Row Level Security (RLS) policies in the database migration are
   intended to restrict access to user-specific records.
This repository does not currently include a separate Express/Node.js
API server.
Getting Started
Prerequisites
Install the following:
- Node.js (LTS recommended)
- npm (included with Node.js) or Bun
- A Supabase project
1. Clone the repository
git clone https://github.com/Saranya2006-py/CarrerBreak-AI.git
cd CarrerBreak-AI
2. Install dependencies
Using npm:
npm install
Or using Bun:
bun install
3. Configure environment variables
Create a .env file in the project root and add the Supabase values for
your own project:
VITE_SUPABASE_URL=your_supabase_project_url
VITE_SUPABASE_PUBLISHABLE_KEY=your_supabase_publishable_key
VITE_SUPABASE_PROJECT_ID=your_supabase_project_id
Use the values from your Supabase project settings. Do not commit your
.env file or any secret keys to GitHub.
4. Set up the database
Apply the SQL migration in:
supabase/migrations/
You can run the migration using the Supabase CLI or the SQL Editor in
your Supabase dashboard. Review the migration and configure the required
Supabase services and policies for your project before using the
application.
5. Start the development server
npm run dev
Open the local URL printed by Vite in your terminal (usually
http://localhost:5173).
Environment Variables
  Variable                            Description
  VITE_SUPABASE_URL                 URL of your Supabase project

  VITE_SUPABASE_PUBLISHABLE_KEY     Supabase publishable/anonymous
client key
VITE_SUPABASE_PROJECT_ID          Supabase project identifier
Vite exposes variables prefixed with VITE_ to browser-side code.
Therefore, never put service-role keys, database passwords, private
API keys or other secrets in these variables. Any privileged operation
should be performed by a secure server-side component.
Database and Authentication
The repository includes a Supabase SQL migration under
supabase/migrations/. The database types and client configuration are
located under:
src/integrations/supabase/
The schema includes user-related data such as profiles, resumes, roadmap
tasks, skills, user skills, interview sessions, achievements and jobs.
Supabase Auth is used for account and session management. Review the
migration's Row Level Security policies before deploying and verify that
each table and storage resource enforces the intended access rules.
Available Scripts
  Command                Description
  npm run dev          Start the Vite development server
npm run build        Create a production build
npm run build:dev    Create a development-mode build
npm run preview      Preview the production build locally
npm run lint         Run ESLint
npm test             Run the Vitest test suite once
npm run test:watch   Run tests in watch mode
Testing
Run the current test suite with:
npm test
Run lint checks with:
npm run lint
The project includes Vitest and Testing Library dependencies. Add and
maintain tests for important user journeys, especially authentication,
form validation, profile updates and database-backed workflows.
Security Notes
- Keep .env out of version control.
- Never expose Supabase service-role keys or other privileged
  credentials in frontend code.
- If a credential has ever been committed or shared publicly, rotate
  it.
- Review Row Level Security policies for every user-specific table.
- Validate uploaded files and restrict file types and sizes.
- Do not treat demo analysis or predefined recommendations as verified
  AI output.
- Do not store sensitive personal information unless it is necessary
  and appropriately protected.
Future Improvements
Potential areas for further development include:
- Integrate a real, securely hosted AI service for resume feedback and
  personalised career guidance.
- Replace demo content with validated, database-backed workflows.
- Add stronger automated tests for critical user journeys.
- Improve accessibility, responsive behaviour and error handling.
- Add deployment instructions and a live demo.
- Add screenshots and an architecture diagram to this README.
Contributing
Contributions and suggestions are welcome. For changes, create a feature
branch, make the update, run the test and lint commands, and submit a
pull request with a clear description of the change.
