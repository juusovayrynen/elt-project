#base image
FROM python:3.8-slim

#install postgresql comman line tools
RUN apt-get update && apt-get install -y postgresql-client

#copy files and directories (elt script)
COPY elt_script.py .

#default command to run elt script
CMD [ "python", "elt_script.py" ]