# Fronted Technical Specs

## Pages

### Dashboard `/api/dashboard`

#### Purpose

The purpose of this page is to provide a summary of learning and acts as the default page when user visits the website.

#### Components

This page contains the following:
- Last Study Session
    - shows last activity used
    - shows when last activity used
    - summarizes wrong vs correct from last activity
    - has a link to the group 
- Study Progress
    - total words studied
        - across all study sessions, show the total words studied out of all the possible words in the 
    - display a mastery progress eg. 0% - 100%
- Quick Stats
    - success rate eg. 80%
    - total study sessions eg. 4
    - total active groups eg. 3
    - study streak eg. 3 days
- Start Studying Button
    - goes to study activities page

#### Needed API Endpoints

We'll need the following API endpoints to power this page:
- GET /api/dashboard/last-study-session
- GET /api/dashboard/study-progress
- GET /api/dashboard/quick-stats

### Study Activities Index / `/api/study_activities`

#### Purpose

The purpose of this page is to show a collection of study activities, with a thumbnail and name, to either launch the activity or to learn more about the activity.

#### Components

- Study Acitivity Card
    - thumbnail of the study activity
    - name of the study activity
    - launch button
    - view page to view more info about past study sessions


#### Needed API Endpoints

- GET /api/study_activities


### Study Activity Show / `/api/study_activities/:id`

#### Purpose

The purpose of this page is to show the details of a study activity and its past study sessions.

#### Components
- Name of study activity
- Thumbnail of study activity
- Description of study activity
- Launch button
- Study Activities Paginated List
    - id
    - activity name
    - group name
    - start time
    - end time (inferred by the last word_review_items submitted)
    - number of review items

#### Needed API Endpoints

- GET /api/study_activities/:id
- GET /api/study_activities/:id/study_sessions

## Study Activities Launch `/api/study_activities/:id/launch`

#### Purpose

The purpose of this page is to launch a study activity.

#### Components
- Name of study activity
- Launch form
    - select field for group
    - launch now button

#### Behaviour
After the form is submitted, a new tab opens with the study activity based on its URL specified in the database.

After the form is submitted, the page will redirect to the study session show page.

#### Needed API Endpoints
- POST /api/study_activities/

### Words Index `/api/words `

#### Purpose

The purpose of this page is to show all words in our database.

#### Components
- Paginated Word List
    - Columns
        - Urdu
        - Roman Urdu
        - English
        - Correct Count
        - Wrong Count
    - Pagination with 100 items per page
    - Clicking the Urud word will take us to the word show page

#### Needed API Endpoints
- GET /api/words


### Word Show `/api/words/:id`

#### Purpose

The purpose of this page is to show the details of a specific word.

#### Components
- Urdu
- Roman Urdu
- English
- Study Statistics
    - Correct Count
    - Wrong Count
- Word Groups
    - show as a series of pills eg. tags
    - when group is clicked, go to group show page

#### Needed API Endpoints
- GET /api/words/:id


### Word Groups Index `/api/groups`

#### Purpose

The purpose of this page is to show all word groups in our database.

#### Components
- Paginated Word Group List
    - Columns
        - Name
        - Words Count
    - Clicking the name will take us to the group show page

#### Needed API Endpoints

### Group Show `/api/groups/:id`

#### Purpose

The purpose of this page is to show the details of a specific group.

#### Components
- Group Name
- Group Statistics
    - Total Word Count
- Words in Group (Paginated List of Words)
    - should use the same component as the word index page
- Study Sessions (Paginated List of Study Sessions)
    -  Should use the same component as the study sessions index page

#### Needed API Endpoints
- GET /api/groups/:id (the name and group stats)
- GET /api/groups/:id/words
- GET /api/groups/:id/study_sessions


### Study Sessions Index `/api/study_sessions`


#### Purpose

The purpose of this page is to show all study sessions in our database.

#### Components
- Paginated Study Session List
    - Columns
        - Id
        - Activity Name
        - Start Time
        - End Time
        - Number of review items
    - Clicking the study session id will take you to the study session show page.

#### Needed API Endpoints
- GET /api/study_sessions


### Study Session Show Page `/api/study_sessions/:id`

#### Purpose

The purpose of this page is to show the details of a specific study session.

#### Components
- Study Session Details
    - Activity Name
    - Start Time
    - End Time
    - Number of review items
    - Group Name
- Word Reviewed Items (Paginated List of Word Reviewed Items)
    - Should use the same component as the word index page

#### Needed API Endpoints
- GET /api/study_sessions/:id 
- GET /api/study_sessions/:id/words

### Settings `/api/settings`

#### Purpose

The purpose of this page is to make configurations to the study portal.

#### Components
- Theme Selection eg. Ligt, Dark, System Default
- Reset history button
    - this will delete all study sessions
- Full Reset button
    - this will drop all tables and recreate with seed data

#### Needed API Endpoints
- POST /api/settings/reset-history
- POST /api/settings/full_reset

------

#### Purpose
#### Components
#### Needed API Endpoints