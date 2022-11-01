# Service Interface
<!-- 
## POST /auth-token

Starts a user session. Since this is a beginner friendly project, the server will just have one session at a time (no concurrency needed).

| **Argument** | **Description** |
| ------------ | --------------- |
| uid          | User id         |

### Return Object

| **Key**    | **Description** |
| ---------- | --------------- |
| auth-token | identifier      |

## PUT /users/{uid}

Updates user info in the db

| **Argument** | **Description**    |
| ------------ | ------------------ |
| name         | User name          |
| major        |                    |
| year         | Year at the school |
| profile      | User description   |

### Return Object

| **Key** | **Description**       |
| ------- | --------------------- |
| courses | top-K matched courses | -->

## GET /recom

| **Argument** | **Description**                                |
| ------------ | ---------------------------------------------- |
| liked        | string, a previous course code that user liked |
| k            | int, number of recommendation                  |
| subjects     | string, list of subject code, csv              |

### Return Object

| **Key** | **Description**                    |
| ------- | ---------------------------------- |
| courses | string, top-k matched courses, csv |

<!-- # User DB

| **field** | **type**   | **constrains** | **description**                                              |
| --------- | ---------- | -------------- | ------------------------------------------------------------ |
| id        | bigint     | Primary key    |                                                              |
| uid       | bigint     | Unique, index  | School id                                                    |
| name      | string     | index          | User name                                                    |
| major     | int/string |                |                                                              |
| year      | int        |                | Year at school                                               |
| keywords  | string     |                | Description of this user, what do they like, etc. **This will be used in matching top K courses for recommendation.** |

Or just use csv for simplicity.

- Since there will be no concurrency, querying one row each time does not worth it
- Up to discussion -->