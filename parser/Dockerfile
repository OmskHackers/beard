FROM debian:10

RUN apt-get update && \
    apt-get install -y \
    chromium \
    python3-pip \
    libxml2 \
    libxslt1-dev libxslt1.1 python-libxslt1 python-libxslt1-dbg xsltproc zlib* \    
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

ENV DEBIAN_FRONTEND noninteractive
ENV TZ Europe/Moscow

WORKDIR /app

COPY requirements.txt .

RUN pip3 install -r requirements.txt
RUN pip3 install webdriver-manager==3.5.2
RUN mkdir /app/ws

ADD board_parser.py board_parser.py
ADD game.py game.py
ADD parser.py parser.py
ADD ws/ws.py ws/ws.py

CMD [ "python3", "parser.py"]

