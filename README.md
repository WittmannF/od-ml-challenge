# On Deck ML Challenge

- Build the first iteration of a recommender system that could suggest top-recommended movies to users.
- Provide a GitHub repo (private is fine) with the working model and some description of how to reproduce training/testing steps.
- Provide written answers to these questions:
  - A brief justification of the chosen model and the scoring metric. What alternatives would be worth exploring?
  - What would be your next steps to improve the recommendation quality?

[Dataset link](https://www.dropbox.com/s/vi7lktdxx0r97o4/od-challenge.tar.gz?dl=1).

## Notes

- You define the technical details of the solution: the model, feature set, test/train split, normalization, loss, scoring metric.
- You're not expected to use as much features as possible. Explore the data and take what works best for your approach.
- You're not expected to produce a model with perfect scores. It's enough to pick a sensible model, make a few tweak iterations, produce some results, and outline a path to improve it.

## Technical constraints

- Python 3.8+, Torch/TensorFlow/Keras.
- The model, the traing and testing code should be in Jupyter notebooks. Everything else may be in notebooks or python files.
- If trainng takes more than an hour on a laptop, provide the trained model and the code to load it.

## Dataset details

`movies.pickle` (4107 rows) — basic info about movies:

| Column     | Type       | Example                             | Notes                     |
| :--------- | :--------- | :---------------------------------- | :------------------------ |
| `movie_id` | `int`      | `109830`                            |
| `title`    | `str`      | `"Forrest Gump"`                    |
| `genres`   | `set[str]` | `{"Romance", "Comedy"}`             |
| `year`     | `int`      | `1994`                              |
| `synopsis` | `str`      | `"The film begins with feather..."` | Detailed plot description |

`aggs.pickle` (28557 rows) — aggregated ratings, total and by demographic:

| Column           | Type    | Example       | Notes                                     |
| :--------------- | :------ | :------------ | :---------------------------------------- |
| `movie_id`       | `int`   | `109830`      |
| `rating_average` | `float` | `8.8`         |
| `rating_count`   | `int`   | `304`         | Number of ratings collected for the group |
| `demographic`    | `str`   | `"age_18_29"` | Group name: total, by age, by gender      |

`teams.pickle` (190547 rows) — cast & crew:

| Column        | Type  | Example             | Notes                       |
| :------------ | :---- | :------------------ | :-------------------------- |
| `movie_id`    | `int` | `109830`            |
| `person_role` | `str` | `"actor"`           | Enum: actor/director/writer |
| `person_id`   | `int` | `37097`             |
| `person_name` | `str` | `"Giovanni Arpino"` |

`labels.pickle` (42237 rows) — user ratings to use as labels:

| Column     | Type    | Example  | Notes      |
| :--------- | :------ | :------- | :--------- |
| `movie_id` | `int`   | `109830` |
| `user_id`  | `int`   | `184`    |
| `rating`   | `float` | `8.8`    | 1-10 scale |
