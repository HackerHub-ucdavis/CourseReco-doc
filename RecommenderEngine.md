# Recommender Engine

- Recommender Engine only provides one function: get top-K courses

- Hybrid Recommendation?

## Collaborative Filtering

| \     | course1 | course2 | course3 | …    |
| ----- | ------- | ------- | ------- | ---- |
| user1 |         |         |         |      |
| user2 |         |         |         |      |
| user3 |         |         |         |      |

## Content-based (NLP)

* Fold a user’s past courses’ description into one list of keywords

* Cosine similarity of user profile vector with latent embedding vector of each course description

* Take top K course based on similarity (choosing factor)

* Filter with prerequisite
  * Choosing factor++ if can choose it at pass 1
  * Factor++ if core requirement of user’s major

* Response with the final top K course (after re-ranking)

[NLP Movie Recommendation](https://towardsdatascience.com/using-cosine-similarity-to-build-a-movie-recommendation-system-ae7f20842599)

In our case, in addition to the combined features of the courses, we will add a row of user’s feature string (combined by user keywords, major(s), and year). The row will also be given an `ID`, which will be used as the “user liked” course later. This consideration is due to we don’t know which course the user actually likes

Therefore, let $m$ denote the number of courses available in next quarter, instead of an $m \times m$ cosine similarity matrix, we will have a $m+1 \times m+1$ matrix, and the further filtering will use `ID` to start the top-K query.

## Model Consideration

In normal cases, a hybrid approach (collaborative filtering on user-embedding v.s. item-embedding) would be better. However, this would require us to have enough user data. That is, let $n$ denote number number of user data we have, we need
$$
0 << n
$$
for CF to work appropriately.

From a complexity perspective, if $n << m$, the content based approach will result in a much larger matrix for us to compute. Therefore, a further discussion is needed if we decide to use the program online.

For our project demonstration, since there is literally no user data, we will consider the second approach.