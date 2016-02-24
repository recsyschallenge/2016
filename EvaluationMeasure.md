Evaluation Measure
==================

The evaluation measure reflects typical use cases at XING: typically, the top k recommendations are 
shown to the user and clicks on recommended items count as a success. Primarily, XING is 
optimizing against _precision@k_. 

The task of the challenge is to compute 30 recommendations (or less) for each of the target users. Essentially this 
is equivalent to predicting those items that a user will interact with in the test period (ca. 2 weeks). The algorithms 
can therefore exploit all the training data that was generate during ca. 2 months before the test period. 
We use the function `score(S, G)` to measure the quality of the recommendations and thus to compute the score 
for the leaderboard. 

**Input:** 

- *Ground truth:* `G` = The ground truth consists of 150,000 `(user, relevantItems)` tuples. For a given user (contained in the _target users_), `relevantItems` is the set of items that are considered as relevant:
  + Relevant items are those items on which the user performed a "positive interaction" in the test period. 
  + We count clicks, bookmarks and clicks on the reply button as positive interaction. 
- *Solution:* `S` = The task is to compile a list of interactions close to the ground truth list. Teams should predict up to 30 interactions for each of the 150k target users. The 30 interactions should be represented as an ordered list of items that should be recommended to the user.
  + `S(u) = recommendedItems` = ordered list of items that are recommended to user `u` (may be empty if no items are recommended to the user)

```javascript
//main scoring function: 
function score(S, G) = {
  score = 0.0
  foreach (u, g) in G: 
    r = S(u) 
    score +=   20 * (precisionAtK(r, g, 2) + precisionAtK(r, g, 4) + recall(r, g) + userSuccess(r, g)) 
             + 10 * (precisionAtK(r, g, 6) + precisionAtK(r, g, 20))
  
  return score
}

//precision within the first top k items: 
function precisionAtK(recommendedItems, relevantItem, k) = {
  topK = recommendedItems.take(k) //takes first k items from the list of reccommendedItems
  return intersect(topK, relevantItems).size / k
}

//recall = fraction of relevant, retrieved items (30 items 
//are allowed to be submitted at maximum per user): 
function recall(recommendedItems, relevantItem) = {
  if (relevantItems.size > 0)
    return intersect(recommendedItems.take(30), relevantItems).size / relevantItems.size
  else 
    return 0.0
}

//user success = was at least one relevant item recommended for a given user?
function userSuccess(recommendedItems, relevantItem) = {
  if (intersect(recommendedItems, relevantItems) > 0)
    1.0
  else 
    0.0
}
```

Additional remarks: 

- `intersect(r, g)` returns the intersection between the (top k) list of recommended items `r` and the set of relevant items `g`
- `intersect(r, g).size` returns the size of the intersection
- For each user, one can thus - at maximum - earn 100 points (given that there exist 20 relevant items for the user). 
