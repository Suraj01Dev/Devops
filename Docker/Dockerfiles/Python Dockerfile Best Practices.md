	

## Using multi stage docker builds.

```
# temp stage
FROM python:3.9-slim as builder

WORKDIR /app

ENV PYTHONDONTWRITEBYTECODE 1

RUN apt-get update && \
    apt-get install -y --no-install-recommends gcc

COPY requirements.txt .
RUN pip wheel --no-cache-dir --no-deps --wheel-dir /app/wheels -r requirements.txt


# final stage
FROM python:3.9-slim

WORKDIR /app

COPY --from=builder /app/wheels /wheels
COPY --from=builder /app/requirements.txt .

RUN pip install --no-cache /wheels/*
```

- **ENV PYTHONDONTWRITEBYTECODE 1**
  Setting this will prevent python from writing pyc files.

- **apt-get install -y --no-install-recommends gcc**
  This will install the `gcc` compiler for building python wheels

- **RUN pip wheel --no-cache-dir --no-deps --wheel-dir /app/wheels -r requirements.txt**
  This command will build the wheel for the python packages, wheels are nothing but binary files that pip uses to build the modules, building the wheel needs gcc compiler

- After building these wheels, this can be transferred into the final stage and it can be installed using pip.
