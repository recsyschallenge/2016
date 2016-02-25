Baselines
==========

The curent baseline that appears in the [leaderboard](https://recsys.xing.com/leaders) and achieves 
`26857.38` points is purely content-based. For a given user `u`, recommendations are 
determined as follows: 

1. Only consider those items for which `active_during_test = 1`
2. `jobrole-title-based` = get top 100 items for which `users.jobroles` and `items.title` overlap and rank by the following score: _number of overlapping IDs * 3_
3. `jobrole-tags-based` = get top 100 items for which `users.jobroles` and `items.tags` overlap and rank by the number of overlapping IDs: _number of overlapping IDs * 2_
4. `discipline-and-region-based` = get 100 random items for which `users.discipline_id == items.discipline_id AND users.region == items.region`. Score of each item = 2 
5. `industry-and-region-based` = get 100 random items for which `users.industry_id == items.industry_id AND users.region == items.region`. Score of each item = 1 
6. Aggregate scores of `jobrole-title-based`, `jobrole-tags-based`, `discipline-and-region-based` and `industry-and-region-based` and ensure that `users.career_level == items.career_level` (and if `users.career_level` is `NULL` or `0` then simply assume that the carer level is 3). 
