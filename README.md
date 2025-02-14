# ncaa-twitter

This repository integrates [Deephaven](http://deephaven.io/) with [Twitter](https://twitter.com/) and [Python's Natural Language Toolkit (NLTK)](https://www.nltk.org/) to pull recent tweets and evaluate sentiment in real-time. We start by pulling the data and running a `SentimentIntensityAnalyzer` on each tweet. We then aggregate the posts to see the overall positivity or negativity of that term on Twitter with time.
 Running `./ncaa-twitter.sh` will create open deephaven on [http://localhost:10000/ide](http://localhost:10000/ide).

## How it works


### Components

* `Dockerfile` - The Dockerfile for the application. This extends the default Deephaven images to add dependencies. See our guide, [How to install Python packages](https://deephaven.io/core/docs/how-to-guides/install-python-packages/#add-packages-to-a-custom-docker-image), for more information.
* `docker-compose.yml` - The Docker Compose file for the application. This is mostly the same as the [Deephaven docker-compose file](https://raw.githubusercontent.com/deephaven/deephaven-core/main/containers/python-examples/docker-compose.yml) with modifications to run (NLTK)](https://www.nltk.org/) with [Twitter V2 API](https://twitter.com/) and custom dependencies.
* `ncaa-twitter.sh` - A simple helper script to launch the application.
* `data/notebooks/ncaa.py` - A Deephaven sample query to pull Tweets.


### High level overview

Twitter is a firehose of data from which - if used properly - we can learn a lot about social sentiment. There are cases such as with GameStop where attitudes expressed on social media led to huge market changes. If this behavior can be predicted, you have the potential to make a lot of money. Most of the time, you can scroll Twitter for a long time and not glean much insight. With Deephaven and a little bit of natural language processing, we can quickly determine the overall sentiment of a topic to provide a rough idea of the future outlook.

We'll show you how to pull in Twitter data and process that in Deephaven. This data can then be combined with other data - for this post, we chose to look at cryptocurrency, but the possibilities are endless.

## Dependencies

* The [Deephaven-core dependencies](https://github.com/deephaven/deephaven-core#required-dependencies) are required to build and run this project.

## Launch

To launch the latest release, you can clone the repository via:

```shell
git clone https://github.com/deephaven-examples/ncaa-twitter.git
cd ncaa-twitter
```

A start script will install the needed python modules. It will also start the Deephaven IDE.

To run it, execute:

```shell
sh ncaa-twitter.sh
```

Running this script will start several Docker containers that work together to launch Deephaven with the needed dependancies. To view the data navigate to [http://localhost:10000/ide](http://localhost:10000/ide).  To view the data you need to edit the `keys.py` file with your infomration.


## Prereqs

[Twitter](https://developer.twitter.com/en/docs/twitter-api) provides an API to make it easy to pull public tweets. In order to use this code as-is, you need to also have a Twitter Developer account and copy your Bearer Token.


### Run the program

This program is intended to be fine-tuned to fit your data needs. As is this will pull in the live tweets for the NCAA teams.  It will perform sentiment on the tweets and aggregate the tweets to assess if that team is positive/negative to guide wins.

## Your turn

This code provides a basic starter. You can use it to make your own searches, tie to other programs, or just see how social media is doing.

We hope this program inspires you. If you make something of your own or have an idea to share, we'd love to hear about it on [Gitter](https://gitter.im/deephaven/deephaven)!



## Related documentation

- [Simple Kafka import](https://deephaven.io/core/docs/how-to-guides/kafka-simple/)
- [Kafka introduction](https://deephaven.io/core/docs/conceptual/kafka-in-deephaven/)
- [How to connect to a Kafka stream](https://deephaven.io/core/docs/how-to-guides/kafka-stream/)
- [Kafka basic terminology](https://deephaven.io/core/docs/conceptual/kafka-basic-terms/)
- [consumeToTable](https://deephaven.io/core/docs/reference/data-import-export/Kafka/consumeToTable/)
