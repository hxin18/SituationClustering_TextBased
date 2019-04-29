# Text Based Situation Clustering in Real-time
Unlike other offline clustering algorithms, models here are used to cluster tweets, messages, or texts during disasters in real-time. Tweets in different situations would be divided into their coressponding clusters based on the content of messages. At the end, one can do quiry on some tweets and to see related tweets in the same situation.

## Getting Started

Models are implemented under python 2.7.*. There are some denpendency and packages needed before running it.

### Prerequisites

One pre-trained Word2Vec word embedding is used in models here. Essentially, this word embedding was trained on tweets of 19 natural and man-made disasters datasets, which is a relatively general word wmbedding for processing tweets during diasters.

Just simply refer to this link to download and put it under the SituationClustering_TextBased folder(this folder).

*   [CrisisWordEmbedding](http://crisisnlp.qcri.org/data/lrec2016/crisisNLP_word2vec_model_v1.2.zip) - crisisNLP_word_vector

To get this use

```
wget http://crisisnlp.qcri.org/data/lrec2016/crisisNLP_word2vec_model_v1.2.zip
```
### Installing

gensim tool should be installed if it is not in your python packages. To do in terminal:

```
- pip install gensim
```

## Usage
The model takes .txt file, in which all data represents as json lines in time sequence, as the input. Meanwhile, one should specify the output file as one runs the model.

There is another optional parameter, -stop_point, which is used to specify the number of tweets to be processed in the model. All tweets would be computed by default, if one do not want to set up stop point.

Last parameter is to specify the model name you'd use: One is "DynamicClustering", the other is "EvolutionaryClustering".

### Example
If all tweets need to be processed, command in terminal should be like this:

	python SituationClustering.py -input sample.jl -output output.jl -model_name DynamicClustering [or EvolutionaryClustering]

If one wants to set stop point to run the code, command in terminal should be like this:

	python SituationClustering.py -input sample.jl -output output.jl  -stop_point 1000 -model_name DynamicClustering [or EvolutionaryClustering]


## Sample Format

sample.jl is a json_line file. with each line a json format of tweet.
For each tweets, originalText, id, creatAt are three mandatory fields, other fields are optional for this version.

ex:

{"LOC": ["Everest"], "originalText": "8 dead as #japanquake-triggered avalanche sweeps Everest: KATHMANDU, Nepal (AP) \u2014 An avalanche swept the\u2026 http://t.co/43v3yjs6Hc #tel4rent", "language": "en", "geoLocations": [{"lat": 27.98791, "geohash": "tuvz4p116hd4", "lon": 86.92529}], "GPE": ["KATHMANDU", "Nepal"], "topics": ["search"], "sentimentString": "Negative, Activation", "ORG": ["AP"], "id": 591934196102221825, "createdAt": "2015-04-25T11:58:04Z"}

## Sample output:

Output is a json-line file, with each line represents a clusters

ex:

{"cluster15": [593705687043022849, 593705778290171905, 593705687051476992]}

{"cluster16": [593617518654160896, 593661509584048128, 593641872121290753, 593629791548350464]}

{"cluster17": [594059340752949248]}

explaination:
clusters contains three tweets whose id are 593705687043022849, 593705778290171905, 593705687051476992

## Versioning

Version 1.0

## Authors

* **Jianheng Hou** - *Information Science Institute* - [Jianheng Hou](https://www.linkedin.com/in/jianheng-hou-70130a154/)

## Additional Contact:

Xin Huang(huan233@usc.edu)

* See also the other detalis or background of this project - [THOR](http://usc-isi-i2.github.io/thor/)

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details

## Acknowledgments

* Word Embedding trained on tweets of 19 natural and man-made disasters datasets from:

    Muhammad Imran, Prasenjit Mitra, Carlos Castillo: [Twitter as a Lifeline: Human-annotated Twitter Corpora for NLP of Crisis-related Messages](https://mimran.me/papers/imran_prasenjit_carlos_lrec2016.pdf). In Proceedings of the 10th Language Resources and Evaluation Conference (LREC), pp. 1638-1643. May 2016, Portorož, Slovenia.
