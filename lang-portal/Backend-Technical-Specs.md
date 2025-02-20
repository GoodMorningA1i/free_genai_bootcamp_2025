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

## API Endpoints

### GET /api/dashboard/last-study-session

#### JSON Response
```json
{
    "id": integer,
    "group_id": integer,
    "created_at": datetime,
    "study_activity_id": integer
    "last_used": datetime
}
```

### GET /api/dashboard/study-progress

#### JSON Response
```json
{
    "total_words_studied": integer,
    "total_available_words": integer
}
```

### GET /api/dashboard/quick-stats

#### JSON Response
```json
{
    "total_words_studied": integer,
    "total_correct": integer,
    "total_mastered": integer,
    "total_sessions": integer,
    "total_active_groups": integer,
    "study_streak": integer
}
```


### GET /api/study-activities

#### JSON Response
```json
{
    "id": integer,
    "group_id": integer,
    "study_activity_id": integer,
    "created_at": datetime
}
```

### GET /api/study-activities/:id

#### JSON Response
```json
{
    "id": integer,
    "name": string,
    "thumbnail_url": string,
    "description": string
}
```

### GET /api/study-activities/:id/study_sessions

#### JSON Response
```json
{
    "items": [
        {
            "id": integer,
            "activity_name": string,
            "created_at": datetime,
            "end_time": datetime,
            "number_of_review_items": integer
        }
    ],
    "pagination": {
        "current_page": integer,
        "total_pages": integer,
        "total_items": integer,
        "items_per_page": integer
    }
}
```

### POST /api/study-activities/

#### Request Parameters
- group_id integer
- study_activity_id integer

#### JSON Response
```json
{
    "id": integer,
    "group_id": integer
}
```

- GET /api/words
    - pagination with 100 items per page

- GET /api/words/:id

- GET /api/groups
    - pagination with 100 items per page 

- GET /api/groups/:id
- GET /api/groups/:id/words
- GET /api/groups/:id/study_sessions

GET /api/study_sessions

- GET /api/study_sessions/:id 
- GET /api/study_sessions/:id/words

- POST /api/settings/reset-history
- POST /api/settings/full_reset

- POST /api/study_sessions/:id/word_id/review