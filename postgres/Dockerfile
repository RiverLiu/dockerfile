FROM postgres:10.7 AS cube-builder
MAINTAINER River Liu <ljathit@gmail.com>

ENV PG_VERSION 10.7

RUN set -xe \
    &&  apt-get update && apt-get install -y build-essential curl postgresql-server-dev-10 \
    && curl https://ftp.postgresql.org/pub/source/v$PG_VERSION/postgresql-$PG_VERSION.tar.bz2 -o /postgresql-$PG_VERSION.tar.bz2 \
    && cd / && tar xvf postgresql-$PG_VERSION.tar.bz2 \
    && cd /postgresql-10.7/contrib/cube && sed -i 's/#define CUBE_MAX_DIM (100)/#define CUBE_MAX_DIM (256)/' cubedata.h \
    && USE_PGXS=true make \
    && USE_PGXS=true make install 

FROM postgres:10.7
COPY --from=cube-builder /usr/lib/postgresql/10/lib/cube.so /usr/lib/postgresql/10/lib/

