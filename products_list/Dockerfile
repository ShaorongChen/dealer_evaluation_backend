FROM python:3.13-slim-bookworm AS builder

# Stage 1: Build dependencies
WORKDIR /python-docker
COPY requirements.txt requirements.txt
RUN pip3 install -r requirements.txt

# Stage 2: Copy application code
COPY . .

# Stage 3: Final stage with minimal image
FROM python:3.13-slim-bookworm

WORKDIR /python-docker
COPY --from=builder /usr/local/lib/python3.13/site-packages /usr/local/lib/python3.13/site-packages
COPY . .

CMD [ "python3", "-m" , "flask", "run", "--host=0.0.0.0" ]
