FROM python:3.12-slim

RUN apt-get -qq update && \
    apt-get -qq install --yes --no-install-recommends libgl1-mesa-glx libglu1-mesa libxrender-dev gettext-base less unzip git > /dev/null && \
    apt-get -qq purge && \
    apt-get -qq clean && \
    rm -rf /var/lib/apt/lists/*

COPY requirements.txt /tmp
RUN pip install --no-cache-dir -r /tmp/requirements.txt

RUN mkdir /home/examples-read-only

VOLUME /home/workdir/
WORKDIR /home/
EXPOSE 8888


ADD examples /home/examples-read-only
ADD run.sh /tmp
RUN chmod +x /tmp/run.sh

ENTRYPOINT ["/tmp/run.sh"]