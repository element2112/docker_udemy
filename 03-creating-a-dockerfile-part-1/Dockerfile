FROM python:2.7-alpine

# create folder for application
# RUN allows you to use basic shell scripting commands
# alpine is linux so using bash
RUN mkdir /app

# set the working directory. All pathing will be relative to this dir
WORKDIR /app

# takes in src and destination respectively
# cannot use cd .. to move back a directory
# below is similar to COPY requirements.txt /app/requirements.txt
#   but setting the working directory makes this unnecessary
COPY requirements.txt requirements.txt

# install dependencies (ex: npm install)
# node: npm install -r package.json
RUN pip install -r requirements.txt

# copying all contents of this directory into app directory
# . <- works as a destination again due to setting the workdir

# due to layering, it's best to copy the application last because docker will rebuild
# everything below that line that has any changes
# each instruction is a different layer. Want to have the least amount of layers possible for efficiency
# dockerfiles can be shared across containers if using the same base image
COPY . .

# docker image metadata that can be retrieved with a command
# this is optional (key="value")
# use \ to chain stuff for one instruction to prevent multiple layers
LABEL maintainer="Brittanie" \
      version="1.0"

# different than RUN
# CMD gets executed when the docker image is ran
# RUN gets executed when docker image is built
CMD flask run --host=0.0.0.0 --port=5000
