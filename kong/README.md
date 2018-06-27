
## Create migrate binrary
clone github.com/golang-migrate/migrate

change Makefile
- add CGO_ENABLED=0 support linux alpine 
```sh
build-cli: clean
	-mkdir ./cli/build
  ...
	cd ./cli && CGO_ENABLED=0 GOOS=darwin GOARCH=amd64 go build -a -o build/migrate.darwin-amd64 -ldflags='-X main.Version=$(VERSION)' -tags '$(DATABASE) $(SOURCE)' .
	...
	cat ./cli/build/sha256sum.txt

```
Build 
```sh
# Gary @ MacBook in ~/.gvm/pkgsets/go1.10/global/src/github.com/golang-migrate/migrate on git:master x [17:32:30] C:2
$ make build-cli
```

file at  
```
cli/build/migrate.linux-amd64
```

## container migrations path 

Default path

```sh
/migrations 
```

You can set custom path use docker environment variables flag (-e)

```sh
-e CUSTOM_MIGRATION_DIR=/tmp/
```

## docker-compose sample

```yaml
version: '3'

services:
    db:
      image: garychen/postgres:10
      restart: always
      volumes:
        - ./data/db/data:/var/lib/postgresql/data
      ports:
        - "9970:5432"
      environment:
        - POSTGRES_MULTIPLE_DATABASES=transcoder,console,kong
        - POSTGRES_USER=gary
        - POSTGRES_PASSWORD=xxxx
      healthcheck:
        test: ["CMD", "pg_isready", "-U", "qeek"]
        interval: 10s
        timeout: 5s
        retries: 5
      networks:
        - backend
				- frontend
				
    kong:
      image: garychen/kong:0.13.1-alpine
      restart: always
      depends_on:
        - db
      volumes:
        - ./data/kong/etc/kong.conf:/etc/kong.conf
        - ./data/db/migrations/kong:/migrations
        - ./tmp/logs/kong:/usr/local/kong/logs
      environment:
        - KONG_DATABASE=postgres
        - KONG_PG_HOST=db
        - KONG_PG_USER=gary
        - KONG_PG_PASSWORD=xxxx
        - KONG_PG_DATABASE=kong
        - KONG_CASSANDRA_CONTACT_POINTS=db
        - KONG_ADMIN_LISTEN=0.0.0.0:8001
        - KONG_MIGRATION_AUTO=true
        - CUSTOM_MIGRATION=true
      ports:
        - "8000:8000"
        - "8443:8443"
        - "8001:8001"
        - "8444:8444"
      command: >
            sh -c "kong migrations up --vv && custom-migration && kong start --vv"
      networks:
        - backend
        - frontend

networks:
  frontend:
    external:
      name: dj2-live-x-frontend
  backend:
    external:
      name: dj2-live-x-backend


```