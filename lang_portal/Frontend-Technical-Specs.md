# Fronted Technical Specs

## Pages

### Dashboard

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

We'll need the following API endpoints to power this page:
- GET /dashboard/last-study-session
- GET /dashboard/study-progress
- GET /dashboard/quick-stats