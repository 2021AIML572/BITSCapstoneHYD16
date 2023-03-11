FROM python:3.7.13 

# Setup python and java and base system
# ENV DEBIAN_FRONTEND noninteractive
# ENV LANG=en_US.UTF-8

RUN apt-get update 
RUN apt-get upgrade -y 
#RUN apt-get install -q -y  python3-pip libsnappy-dev language-pack-en supervisor

RUN apt-get install -y locales locales-all
ENV LC_ALL en_US.UTF-8
ENV LANG en_US.UTF-8
ENV LANGUAGE en_US.UTF-8
  
RUN pip3 install --upgrade pip requests


WORKDIR /code

COPY requirements.txt /code/requirements.txt
RUN pip install --no-cache-dir --upgrade -r /code/requirements.txt

COPY ./service/app/ /code/app/

CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000"]
