# Backend Technical Specs

## Business Goal: 

A language learning school wants to build a prototype of learning portal which will act as three things:
- Inventory of possible vocabulary that can be learned
- Act as a  Learning record store (LRS), providing correct and wrong score on practice vocabulary
- A unified launchpad to launch different learning apps

## Technical Requirements

- The backend will be written in Python
- The database will be using SQLite3
- The API will be written in Flask
- The API will always return JSON
- There will be no authentication or authorization
- Everything will be treated as a single user

## Database Schema

We have the following tables:
- words - stored vocabulary words
    - id integer
    - urdu string
    - roman urdu string
    - english string
    - parts json
- words_groups - join table between words and groups
many to many
    - id integer
    - word_id integer
    - group_id integer
- groups - thematic groups of words
    - id integer
    - word_id integer
- study_activities - a specific study activity for each group
    - id integer
    - study_session_id integer
    - group_id integer
    - created_at datetime
- study_sessions - record of study sessions grouping word_review_items
    - id integer
    - group_id integer
    - created_at datetime
    - study_activity_id integer
- word_review_items - a record of word practice, determining if the word is correct or not
    - word_id integer
    - study_session_id integer
    - correct boolean
    - created_at datetime

### API Endpoints

- GET /api/words
- GET /api/words/:id
- GET /api/groups
- GET /api/groups/:id
- GET /api/groups/:id/words

- GET /api/dashboard/last-study-session
- GET /api/dashboard/study-progress
- GET /api/dashboard/quick-stats

- GET /api/study_activities

- GET /api/study_activities/:id
- GET /api/study_activities/:id/study_sessions

- POST /api/study_activities/
    - required_params: group_id, study_activity_id