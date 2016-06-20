# nginx-s3-proxy

## Motivation

This image was created to securely proxy requests to S3. It uses
[confd](http://github.com/kelseyhightower/confd) to update the nginx
configuration and then starts nginx. You'll need to run your container with the
following environment variables:

```
CACHE_TIME
SERVER_NAME
S3_BUCKET
REGION
AWS_ACCESS_KEY_ID
AWS_SECRET_ACCESS_KEY
```


## Usage

You can run it using a docker-compose like this:

```yaml
version: '2'
services:
  s3proxy:
    cpu_shares: 512
    mem_limit: 128m
    build: ./
    environment:
      CACHE_TIME: "10m"
      SERVER_NAME: "s3proxy.example.com"
      S3_BUCKET: "your-conf-data"
      REGION: "us-west-2"
      AWS_ACCESS_KEY_ID: "<some-access-key>"
      AWS_SECRET_ACCESS_KEY: "<some-secret-key>"
    ports:
      - "8080:80"
```

## License

MIT
