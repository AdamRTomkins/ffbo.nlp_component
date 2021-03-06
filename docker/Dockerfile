###########################################
# run using: 
# docker build -t ffbo/nlp_component:develop .
# docker run --name nlp_component -v $(dirname `pwd`):/nlp_component -v $(dirname $(dirname `pwd`))/ffbo.neuroarch_nlp:/neuroarch_nlp -v $(dirname $(dirname `pwd`))/quepy:/quepy -it ffbo/nlp_component:develop sh /nlp_component/nlp_component/run_component_docker.sh
###########################################
FROM python:2

MAINTAINER Adam Tomkins <a.tomkins@sheffield.ac.uk>
RUN apt-get update && apt-get install -y apt-transport-https

ENV HOME /app
ENV DEBIAN_FRONTEND noninteractive

# Install Python and Basic Python Tools
RUN apt-get install -y --force-yes --force-yes python python-dev python-distribute python-pip

# install Autobahn|Python
RUN pip install -U pip && pip install autobahn[twisted]

# Install quepy dependencies
RUN pip install pandas
RUN pip install refo
RUN pip install SPARQLWrapper
RUN pip install docopt
RUN pip install nltk
RUN python -m nltk.downloader maxent_treebank_pos_tagger wordnet averaged_perceptron_tagger
RUN pip install spaCy
RUN python -m spacy.en.download

# Install neuroarch_nlp dependencies
RUN pip install -U fuzzywuzzy
RUN pip install python-Levenshtein
RUN pip install -U datadiff
RUN pip install pyOpenSSL
RUN pip install service_identity