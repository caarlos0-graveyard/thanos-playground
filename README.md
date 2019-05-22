# thanos-tests

This is project is purely educational and is not a pattern for production
deployments or anything like that.

## Usage

Run `./fire` and wait.

It will start:

- 2 prometheus instances (`prometheus1` and `prometheus2`)
- 2 thanos sidecars (1 for each prometheus instance) (`sidecar1` and `sidecar2`)
- 1 minio instance
- 1 traefik instance
- 3 thanos query instances
- 1 domain_exporter instance to have some sample metrics
- 1 thanos compact instance (which is short lived, will run and `exit 0`)
- 1 thanos storer

In our example it will not be used though.

## Accessing things

- http://localhost : querier
- http://localhost:9000 : minio (`minio`/`miniostorage`)
- http://localhost:8080 : traefik dashboard

## More info

- [Thanos docs](https://thanos.io/getting-started.md/) - much here is based on these docs

## TODO

- [ ] alerting
- [ ] grafana
- [ ] run a ruler just to see it work?
