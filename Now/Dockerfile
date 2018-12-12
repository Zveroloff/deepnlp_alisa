FROM python:3.6-alpine

RUN echo "http://dl-cdn.alpinelinux.org/alpine/edge/community" >> /etc/apk/repositories
RUN echo "http://dl-cdn.alpinelinux.org/alpine/edge/main" > /etc/apk/repositories
RUN apk --no-cache --update-cache add gcc \
                                      gfortran \
                                      python \
                                      python-dev \
                                      py-pip \
                                      build-base \
                                      wget \
                                      freetype-dev \
                                      libpng-dev \
                                      openblas-dev@community \
                                      openblas@community \
                                      ; \

RUN ln -s /usr/include/locale.h /usr/include/xlocale.h

WORKDIR /app
COPY . /app

EXPOSE 5000

RUN pip install -r requirements.txt
CMD FLASK_APP=api.py flask run --host="::"
