# FROM python:3-alpine

# # Create app directory
# WORKDIR /app

# # Install app dependencies
# COPY requirements.txt ./

# # RUN sudo apt install -y apparmor apturl

# RUN pip install  -r requirements.txt

# # Bundle app source
# COPY . .
# # RUN apk add py3-virtualenv
# # RUN cd flask
# RUN source ./flask/bin/activate
# RUN apk add flask

# EXPOSE 5002
# CMD [ "python", "app.py"]

FROM python:3.8.2-alpine
WORKDIR /project
ADD . /project
# RUN apk add --update --no-cache python3 && ln -sf python3 /usr/bin/python
RUN pip3 install --upgrade pip
RUN apk update && apk add mysql mysql-client
RUN apk update \ 
    && apk add --virtual build-deps gcc libc-dev linux-headers python3-dev musl-dev postgresql-dev \
    && apk add --no-cache mariadb-dev
RUN pip3 install -r requirements.txt
RUN pip3 install flask_mysqldb
EXPOSE 5002
CMD ["python","app.py"]