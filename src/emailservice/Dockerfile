FROM python:3.11-alpine as builder
WORKDIR /usr/src/app
RUN apk add --no-cache gcc g++ musl-dev linux-headers
COPY requirements.txt ./
RUN pip install --no-cache-dir -r requirements.txt

FROM python:3.11-alpine
WORKDIR /usr/src/app
COPY . .
COPY --from=builder /usr/local/lib/python3.11/site-packages /usr/local/lib/python3.11/site-packages
ARG PORT=8080
ENV PORT=$PORT
EXPOSE $PORT
CMD [ "python", "email_server.py" ]