FROM python:3

ARG APP_DIR=/app

WORKDIR ${APP_DIR}

COPY requirements.txt ./

RUN pip install --no-cache-dir -r requirements.txt

COPY . . 

RUN apt update && apt install curl

ENV PORT=3000
ENV INSTANCE_NAME=dovbearpython
ENV INSTANCE_HASH=1290eajsd0912

HEALTHCHECK --interval=30s --timeout=5s --retries=3 \
    CMD curl -s -f http://localhost:${PORT}/healthz || exit 1

CMD ["python", "./main.py", ""]