# thanos-tests
just testing thanos with docker-compose to understand how it works :)

## Usage

Run `./fire` and wait.

It will start:

- 2 prometheus instances (`prometheus1` and `prometheus2`)
- 2 thanos sidecars (1 for each instance) (`sidecar1` and `sidecar2`)
- 1 minio instance
- 1 traefik instance
- 1 thanos query instance
- 1 domain_exporter instance to have some sample metrics
- 1 thanos compact instance (which is short lived, will run and `exit 0`)
- 1 thanos storer

Components that you can scale up:

- Querier

It is stateless, traefik will discovery additional instances and load balance.

To scale run:

```sh
docker-compose scale querier=3
```

- Storer

It talks with the bucket (in our case, minio). It can also be scale freely.

You can do so with:

```sh
docker-compose scale storer=2
```

In our example it will not be used though.

## Accessing things

- http://localhost : querier
- http://localhost:9000 : minio (`minio`/`miniostorage`)
- http://localhost:8080 : traefik dashboard
