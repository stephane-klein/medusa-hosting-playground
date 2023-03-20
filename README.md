# Medusa hosting playground

This repository contains a environment that allows to test [Medusa](https://github.com/medusajs) deployment.

This installation is based in part on https://docs.medusajs.com/deployments/server/deploying-on-digital-ocean

```sh
$ docker compose up -d --wait medusa-backend
```

Wait…

```sh
$ docker compose logs -f medusa-backend
...
medusa-hosting-playground-medusa-backend-1  | ✔ Indexing event emitted – 10ms
medusa-hosting-playground-medusa-backend-1  | - Creating server
medusa-hosting-playground-medusa-backend-1  | ✔ Server is ready on port: 9000 – 11ms
```

Inject database seed:

```sh
$ docker compose exec medusa-backend medusa seed -f data/seed.json
```


```sh
$ curl -X GET http://localhost:9000/store/products | jq
```

Start [*Medusa admin*](https://github.com/medusajs/admin): 

```sh
$ docker compose up -d --wait medusa-admin
```

Go to http://localhost:7000

Login: `admin@medusa-test.com`  
Password: `supersecret`
