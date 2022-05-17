# 
FROM python:3.9.11-slim

# set proxies
ENV http_proxy http://kpaamirij:aa3572@proxy.ihu.ac.ir:8080
ENV https_proxy http://kpaamirij:aa3572@proxy.ihu.ac.ir:8080
#
RUN apt-get update && apt-get install

#
RUN apt-get install -y \
  dos2unix \
  libpq-dev \
  libmariadb-dev-compat \
  libmariadb-dev \
  gcc \
  && apt-get clean

# 
WORKDIR /code

# 
COPY ./requirements.txt /code/requirements.txt

# set env variables
ENV PYTHONDONTWRITEBYTECODE 1
ENV PYTHONUNBUFFERED 1

# 
RUN pip install --no-cache-dir --upgrade -r /code/requirements.txt

# 
COPY . /code

# 
CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8080"]
