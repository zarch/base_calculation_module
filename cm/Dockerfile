#
# hotmaps/cm image Dockerfile
#
#


FROM geographica/gdal2:latest


MAINTAINER lesly Houndole <lesly.houndole@crem.ch>


# setup volume
RUN mkdir -p /data
VOLUME /data


# Build commands
RUN apt-get update && apt-get dist-upgrade -y && apt-get autoremove -y

# Install required software

RUN apt-get update \
    && apt-get upgrade -y \
    && apt-get install -y \
    build-essential \
    software-properties-common \
    wget \
    gdal-bin \
    ca-certificates \
    gcc \
    git \
    libpq-dev \
    libgeos-dev \
    libgdal-dev \
    python-gdal \
    make \
    python-pip \
    ssh \
    && apt-get autoremove \
    && apt-get clean









# Setup app server
RUN mkdir -p /data
COPY . /cm
WORKDIR /cm

RUN ls

RUN apt-get update \
    && apt-get upgrade -y \
    && apt-get install -y \
    build-essential \
    software-properties-common \
    wget

RUN wget https://bootstrap.pypa.io/get-pip.py
RUN python get-pip.py


RUN pip install -r requirements.txt
RUN pip install gunicorn



# Install required python modules


# Copy app source code



EXPOSE 5001

# Start server

RUN apt-get update && apt-get install -y supervisor
RUN mkdir -p /var/log/supervisor
COPY supervisord.conf /etc/supervisor/conf.d/supervisord.conf

# CMD ["gunicorn", "--config", "gunicorn-config.py", "--log-config", "app/logging.conf", "run:application"]

# Start processes
CMD ["/usr/bin/supervisord"]


