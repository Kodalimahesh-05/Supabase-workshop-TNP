# Flask + Supabase Task Manager

A simple beginner-friendly CRUD application built with:

- Python
- Flask
- Supabase PostgreSQL
- supabase-py
- HTML/CSS

The application lets you create, complete/uncomplete, list, and delete tasks.

## 1. Prerequisites

Install:

- Python 3.9+
- A Supabase account

## 2. Create the Supabase project

1. Open https://supabase.com/
2. Create an account/sign in.
3. Create a new project.
4. Select the Free plan if you want to keep this demo at $0.
5. Wait until the project is ready.

## 3. Create the database table

1. Open your Supabase project.
2. Go to SQL Editor.
3. Create a new query.
4. Copy everything from `schema.sql`.
5. Paste it into the SQL Editor.
6. Click Run.

You should now have a `tasks` table.

## 4. Get your Supabase API details

In your Supabase project, open the Connect panel/API settings and copy:

- Project URL
- Publishable key

The current Supabase Python quickstart uses `SUPABASE_URL` and
`SUPABASE_PUBLISHABLE_KEY` environment variables.

## 5. Create a Python virtual environment

Open a terminal in this project folder.

### Windows

    python -m venv .venv
    .venv\Scripts\activate

### macOS/Linux

    python3 -m venv .venv
    source .venv/bin/activate

## 6. Install dependencies

    pip install -r requirements.txt

## 7. Create your .env file

Copy `.env.example` to `.env`.

Windows:

    copy .env.example .env

macOS/Linux:

    cp .env.example .env

Then edit `.env`:

    SUPABASE_URL=https://your-project-ref.supabase.co
    SUPABASE_PUBLISHABLE_KEY=your-publishable-key
    FLASK_SECRET_KEY=some-random-secret

Do NOT commit `.env` to Git.

## 8. Start Flask

    python app.py

Open:

    http://127.0.0.1:5000

You should see the Task Manager.

## 9. Test CRUD

Try these operations:

1. Add a task.
2. Mark it complete.
3. Mark it open again.
4. Delete it.
5. Refresh the browser.

The data is stored in Supabase PostgreSQL, so restarting Flask does not remove it.

## 10. Understand the architecture

Browser
   |
   v
Flask
   |
   v
supabase-py
   |
   v
Supabase Data API
   |
   v
PostgreSQL

Flask renders the HTML templates and sends database operations through
the Supabase Python client.

## 11. Important security note

This demo intentionally uses simple anonymous RLS policies so that you can
learn the Flask/Supabase connection without first implementing authentication.

Those policies allow anyone using the application's Supabase key to read,
insert, update, and delete all tasks.

Do NOT use this exact policy setup for a real multi-user production app.

For a real application, the next step is:

1. Add Supabase Auth.
2. Associate every task with `auth.uid()`.
3. Change RLS policies so users can only access their own rows.
4. Keep secrets in environment variables.
5. Disable debug mode in production.

## 12. Free-tier note

Supabase currently has a Free plan. Its documented limits include two active
free projects, 500 MB database size per project, 5 GB egress, 1 GB storage,
and other quotas. Free projects may be paused after inactivity.

Check Supabase's current pricing/billing documentation before deploying a
real application because limits can change.

## 13. Common errors

### Missing SUPABASE_URL

Make sure `.env` exists in the same directory as `app.py`.

### relation "tasks" does not exist

Run `schema.sql` in Supabase SQL Editor.

### permission denied for table tasks

Check that the table is exposed through the Data API and that the grants/RLS
policies from `schema.sql` were successfully created.

### The page loads but there are no tasks

Run the INSERT statements in `schema.sql`, or create a task from the UI.

## Project structure

    flask_supabase_crud/
    ├── app.py
    ├── schema.sql
    ├── requirements.txt
    ├── .env.example
    ├── .gitignore
    ├── README.md
    ├── templates/
    │   └── index.html
    └── static/
        └── style.css
# Supabase-workshop-TNP
