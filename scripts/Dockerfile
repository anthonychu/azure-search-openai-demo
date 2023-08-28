# Use an official Python runtime as a parent image
FROM python:3.10-slim-buster

WORKDIR /scripts

COPY . /scripts

# Install any needed packages specified in requirements.txt
# (copying a test PDF file in there for now)
RUN pip install --trusted-host pypi.python.org -r requirements.txt && \
    mkdir -p /data && \
    mv /scripts/data/* /data

CMD ["bash", "-c", "python ./prepdocs.py /data/* --storageaccount $AZURE_STORAGE_ACCOUNT --container $AZURE_STORAGE_CONTAINER --searchservice $AZURE_SEARCH_SERVICE --openaiservice $AZURE_OPENAI_SERVICE --openaideployment $AZURE_OPENAI_EMB_DEPLOYMENT --index $AZURE_SEARCH_INDEX --formrecognizerservice $AZURE_FORMRECOGNIZER_SERVICE -v"]