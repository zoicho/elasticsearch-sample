FROM docker.elastic.co/elasticsearch/elasticsearch:7.14.1

ENV DEBIAN_FRONTEND noninteractive

WORKDIR /usr/share/elasticsearch

ADD ./readonlyrest-1.34.0_es7.14.1.zip /tmp/readonlyrest-1.34.0_es7.14.1.zip

RUN bin/elasticsearch-plugin install analysis-icu
RUN bin/elasticsearch-plugin install -b ingest-attachment
RUN bin/elasticsearch-plugin install https://github.com/vhyza/elasticsearch-analysis-lemmagen/releases/download/v7.14.1/elasticsearch-analysis-lemmagen-7.14.1-plugin.zip
RUN bin/elasticsearch-plugin install -b file:///tmp/readonlyrest-1.34.0_es7.14.1.zip
RUN mkdir config/lemmagen

ADD ./lemmagen/cs.lem /usr/share/elasticsearch/config/lemmagen
ADD ./lemmagen/sk.lem /usr/share/elasticsearch/config/lemmagen
ADD ./lemmagen/pl.lem /usr/share/elasticsearch/config/lemmagen
ADD ./lemmagen/hu.lem /usr/share/elasticsearch/config/lemmagen
ADD ./lemmagen/en.lem /usr/share/elasticsearch/config/lemmagen

ADD ./hunspell config/hunspell
ADD ./readonlyrest.yml config/readonlyrest.yml