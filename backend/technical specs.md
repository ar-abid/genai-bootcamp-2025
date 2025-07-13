### Business Goal

-A language learning school wants to build a prototype of learning portal which will act as three things:
-Inventory of possible vocabulary that can be learned
-Act as a  Learning record store (LRS), providing correct and wrong score on practice vocabulary
-A unified launchpad to launch different learning apps

### technical requirements

-the backend will be made using go
-the database will be SQLlite 3
–the api will be built using GIN
-the api will return using JSON
-there will be no authentication or authorisaion 
-assume there is only a single user

### database schema 

-words - stored vocabulary of words 
 - kanji - string 
 - romanji - string 
 - engish - string
 - parts - json 
-word_groups - joins words and groups table in many to many relation
-study_activites - a specific study actvity, linking a study session to a group 
 - id - integer
 - group_id - integer 
 - user_id - integer 

-study_sessions  - records of study sessions grouping word_review_items 
 - id - integer 
 - group_id - integer 
 - created at date time 

-word_review_items - a record of word practice, determining if the word was correct or not.
 - id - integer 
 - word_id - integer 
 - correct - boolean 
 - study_session - integer 

 ### API endpoints

- GET/words 
 - pagination with 100 items per page 

- GET/api/words/:id
- GET/api/groups/
    - paginated with 100 items per page 
- GET/api/groups/:id 
- GET/api/groups/:id/words 
- GET/api/groups/id/study_sessions 
- GET/api/dashboard/last_study_session 
- GET/api/dashboard/study_progress
- GET/api/dashboard/quick-stats 
- GET/api/study_activities 
- GET/api/study_activities/:id
- GET/api/study_activites/:id/study_sessions 
- POST/api/study_activites/:id/launch 
 -required params: group_id, study_activity_id 

- GET /api/study_sessions
    - pagination with 100 items per page 

- GET/api/study_sessions/:id
- GET/api/study_sessions/:id/words
- POST/api/reset_history 
- POST/api/full_reset
- POST/api/study_sessions/:id/words/:word_id/review
    - required params:correct 



