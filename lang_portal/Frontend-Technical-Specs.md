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

### Study Activities / `/api/study_activities`

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

------

#### Purpose
#### Components
#### Needed API Endpoints