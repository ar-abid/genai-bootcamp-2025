# frontend technical spec 
##pages 

### dashboard
#### purpose 
this page contains the following components 

#### components

- last study session 
    shows last activity used 
    shows when last activity was used
    summarizes wrong from correct from last activity 
    has a link to the group 

- study progress
    shows total words studied eg - 3/124 
     - across all study boards show all studied words possible in database 
    displays a mastery progress bar eg 3%

- quick stats 
    success rate eg 80% 
    total study sessions eg - 4 
    total active groups eg - 3
    study streak eg 4 days 

- start studying button 
    goes to start studying page 

We'll need the following API endpoints 
 - GET /dashboard/last_study_session 
 - GET /dashboard/study_progress
 - GET /dashboard/quick-stats 

### study activites index / - study activities 

#### purpose 
the purpose of this page is to show a collection of study activites with a thumbnail and its name to either launch or view the study activity 

#### components 

- study activtiy card 
 - show a thumbnail of the activity 
 - the name of the study activitiy 
 - a launch button to take us to the launchpage 
 - the view page that shows more information about past study sessions for this study activtiy 

#### needed api endpoints
 - GET/api/study_activities 

### study activity show '/study_activites /:id'

####purpose 
the purpose of this page is to show the details of a study activity and its past sessions 

####component 
- name of study activity 
- thumbnail of study activity 
- description of study activity 
- launch button 
- study activites paginated list 
 - id
 - activity name 
 - start time 
 - end time (inferred by the last word_review_item submitted )
 - number of review items 

####api endpoints 
- GET /api/study_activities/:id
- GET /api/study_activites/:id/study_sessions 

### study activites launch '/study_activites/:id/launch' 

####purpose 
the purpose of this activity is to launch a study activity 

####component 
- name of study activity 
- launch form 
 - select field for group 
 - launch now button 

 ##behaviour 
 after the request is submitted in a new tab opens with the study activity based on its URL provided in the database 
 
 also after the form is submitted the page will redirect to the study session group. 

####api endpoints 
 - POST/api/study_activites/:id/launch 


### Words index '/words'


####purpose 

the purpose of this page is to show all words in our databse 

####component 
- paginated word list 
  - coloumns 
   - english 
   -  japanease 
   - romaji 
   - correct count 
   - wrong count 
- pagination with 100 items per page 
- clicking the japanease word will take us to the word show page  

####api endpoints 
- GET /api/words

### word show page '/words/:id'

####purpose 
the purpose of this page is to show information about a specific word 

####component 
 - japanease 
 - romaji 
 - english 
 - study statistics 
  - correct count 
  - wrong count 
- word groups 
 - show a series of pills eg. tags 
 - when group name is clicked it will take us to the group show page 

####api endpoints 
- GET /api/words/:id 

### word groups index  '/groups/' 


####purpose 
the purpose of this list is to show a list of groups in our database

####component 
- paginated group list 
    - coloumns 
        -group name 
        - word count 
    - clicking the group will take us to the group show page 

####api endpoints 
- GET/ api/ groups 

### Group show '/groups/:id' 

####purpose 
the purpose of this page is to show information about a specific group 

####component 
- group name 
- group statistics 
    - total word count 
- words in group (paginated list of words)
    - should use the same components as the words index page 
- study session (paginated list of study sessions)
    - should use the same component as the study session index page 

####api endpoints 
- GET / api/groups/:id/ (the name and group stats)
- GET / api/groups/:id/words 
- GET / api/groups/id/study_sessions 

## Study session index '/study_session'

####purpose 
the purpose of this page is to sbow a list of study session in our database 

####component 
- paginated study session list t
    - coloumns 
        - Id
        -activity name 
        - group name
        - start time 
        - end time 
        - number of review items 
    - clicking the study session id will take us to the study session show page 

####api endpoints 
- GET /api/study_sessions

### study session show 'study_session/:id'


####purpose 
the purpose of this page is to show specific information about a study session 

####component 
- study session details 
    - activity name 
    - group name 
    - start time 
    - end time
    - number of review items
- words reviewd 
    - should use the same components as the words index page 

####api endpoints 
- GET/api/study_sessions/:id
- GET/api/study_sessions/:id/words

### settings page '/settings'

####purpose 
- the purpose of thiis page is to make configuration to the study portal 

####component 
- theme selection eg. dark or light 
- reset history button 
    - this will delete all study sessions and word review items 
- full reset hsitory button 
    - this will drop all tables and recreate with seed data 

####api endpoints 
- POST/api/reset_history 
- POST/api/full_reset















####purpose 
####component 
####api endpoints 