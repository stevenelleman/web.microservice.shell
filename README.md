# Web Microservice Shell

## Code-Amendment Best Practices 
- Don't commit directly to master, make PRs. 
- PRs should be reviewed and be required to have a +1 from non-contributor to the PR.
- PRs should have corresponding tests. 
- PRs should include documentation. Documentation should be kept with its relevant code to minimize drift.
- Autogenerated code should not be committed.
- Correct known trip-wires (little annoyances, mistakes, gotchas) immediately - quick fixes pay off dividends.
- Prefix branch name with creator's initials.
- As new items come up, add to [TODO](./TODO.md). 
- Maximize code reuse, minimize service directory size and complexity

## Development Setup
1. Install [Docker for Mac](https://docs.docker.com/docker-for-mac/install/) (v3.4.0) 
2. Kubectl 
3. Install [Tilt](https://docs.tilt.dev/install.html) (v0.20.8)
4. Install Helm, `brew install helm`. 
5. Install [golang](https://golang.org/doc/install) (go1.16.4)
6. Install [yarn]()

5. Comment out `external-dns` service and `dev.yaml` in `Tiltfile`, there steps require AWS Route 53 credentials. 
4. [Apply](https://kubernetes.github.io/ingress-nginx/deploy/#aws) nginx ingress controller so that the ingress rules work. s
5. [Apply](https://cert-manager.io/docs/installation/kubernetes/) cert manager.
6. Run `make vendor-all`.
7. Run `tilt up` and navigate to `staging.grouphouse.io`.

## AWS Deployment
[Deployment Docs](./deployment/README.md)

1. Navigate to `./deployment`
2. Run `terraform init` to download providers.
3. `terraform plan`
4. `terraform apply`
5. Update kubectl config: `aws eks --region=us-west-1 update-kubeconfig --name=${cluster name}`

## Charts:
- [External DNS README](charts/external-dns/README.md)
- [Web Frontend Service](charts/web-frontend/Chart.yaml)
- [Public API Service](charts/public-api/Chart.yaml)
- [Example GRPC Service](charts/grpc/Chart.yaml)
- [Postgres API Store](charts/api-store/Chart.yaml)

## Dockerized Services:
- [Web Frontend Service](./services/web-frontend/src/components/README.md)
- [Public API Service](./services/public-api/README.md)
- [Example GRPC Service](./services/grpc)

## Docs
- [TODO](./TODO.md)
- [CHEATSHEET](./CHEATSHEET.md)
- [Libraries](libraries/golang/README.md)
- [Service Deployment](deployment/website/README.md)