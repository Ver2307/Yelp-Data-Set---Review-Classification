# Review Classification using the Yelp Data Set
##### Will other users perceive a yelp review as useful or not?
- Main.py uses yelp review and user data to train a model that classifies each review as useful or not useful to other users
- The label useful (1) is assigned if more than 60 % of the all votes (cool, funny, and useful) are the "useful"
- To run the code on your machine use the docker commands below.
- The feature generation involves text processing, which is computationally expensive.
- Due to limited computing power only a very small sample (20 000 reviews) from the original data set is being used.


### List of features

- stars
- average_stars
- compliment_more
- compliment_hot
- compliment_photos
- compliment_writer
- compliment_plain
- fans
- review_count
- days_yelping
- word_count (without stopwords)
- unique_words_perc
- no_adjectives
- perc_unique_verbs
- perc_unique_adjectives
- norm_of_wordvecs
- adj_wordvecs
- verb_wordvecs
- adj_maj_sent__negative
- adj_maj_sent__objective
- adj_maj_sent__positive
- adj_maj_sent__no_sentiment_assigned
- verb_maj_sent_negative
- verb_maj_sent_objective
- verb_maj_sent_positive
- verb_maj_sent_no_sentiment_assigned
- useful_review_compliments_received_for_other_reviews
                       

### Docker instructions

Download Main_pickled_sample.py from this Github repo and merged_small.pkl from Google Drive (https://drive.google.com/file/d/1v1AKrZGwKtehgQwoTUF80gDnq2b7U9Xo/view?usp=sharing) and save them in a folder. Run the following commands:

```sh
docker pull viavia/firstrepo:yelp_rev_class
docker run -it -v [YOUR_PATH_TO_FOLDER]:/app -w /app  yelp_rev_class bash
```
Now you can run bash commands inside the docker container. Simply run the python file in commandline fashion.

```sh
python Main_pickled_sample.py
```

**NOTE**: On Mac you have to allocate more memory to the Docker container to make run the script. The default setting only allocates 2GB of RAM to Docker containers. I configured it to use 16 GB of RAM and 12 CPUs via Docker advanced settings.

### Use bigger sample or even entire data set

- In case you want to run the script on the entire data set or use a bigger sample you can download Main.py. Main.py takes the   share of the data set that you want to use as an additional argument, e.g. python Main.py 0.05 uses 5 % of the original data
  set. 
- It loads the files user.json and review.json as provided by Yelp.
- The full data set consists of *6 685 900* reviews.
- You also need to specify the hyperparameters for the random forest (number of trees, max_depth and max_features).

```sh
python Main.py [FLOAT - SHARE OF DATA TO USE] [INT - NO_TREES_RF] [INT - MAX_DEPTH_RF] [INT - MAX_FEATURES_RF]
```
