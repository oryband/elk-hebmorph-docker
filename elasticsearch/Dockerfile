FROM elasticsearch:1.7
MAINTAINER Ory Band <oryband@gmail.com>

# install hspell data files,
# hebmorph requirement
ENV HEBMORPH_VERSION 2.3.0
ENV HEBMORPH_FILE hebmorph-lucene-$HEBMORPH_VERSION

RUN wget -P /tmp/ https://github.com/synhershko/HebMorph/archive/$HEBMORPH_FILE.tar.gz && \
    tar -C /opt/ --strip-components 1 -xvf /tmp/$HEBMORPH_FILE.tar.gz HebMorph-$HEBMORPH_FILE/hspell-data-files && \
    chown -R elasticsearch:elasticsearch /opt/hspell-data-files && \
    rm -rf /tmp/$HEBMORPH_FILE.tar.gz

# install hebmorph plugin
RUN plugin --install analysis-hebrew --url https://bintray.com/artifact/download/synhershko/elasticsearch-analysis-hebrew/elasticsearch-analysis-hebrew-1.7.zip
