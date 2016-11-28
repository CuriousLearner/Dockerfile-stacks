# Makes conainer for running Jupyter Notebook

FROM ubuntu:14.04

MAINTAINER Sanyam Khurana "Sanyam@SanyamKhurana.com"

RUN apt-get update -y
RUN apt-get -y install python2.7 python-pip python-dev
RUN apt-get -y install ipython ipython-notebook
RUN pip install jupyter

ENTRYPOINT ["jupyter"]
CMD ["notebook", "--ip=0.0.0.0", "--no-browser"]

EXPOSE 8888
