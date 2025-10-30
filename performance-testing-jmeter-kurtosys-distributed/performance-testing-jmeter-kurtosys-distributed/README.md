# Distributed & Cloud-ready JMeter Performance Testing (Kurtosys)

This repository provides a JMeter-based performance testing module for https://www.kurtosys.com with:
- Distributed (master-slave) mode
- Dockerized runner + docker-compose
- GitHub Actions CI integration
- Kubernetes Helm Chart for scalable execution
- AWS ECS Fargate task definition example for cloud execution

Folders:
- `jmeter/` - test plan and properties
- `docker/` - Dockerfiles and docker-compose for master/slave
- `.github/workflows/` - CI workflow
- `k8s/helm-chart/` - Helm chart for Kubernetes deployment
- `aws/ecs/` - ECS Task Definition and CloudFormation service example
- `docs/` - runbooks and setup notes

Run locally (docker):
1. docker compose up --build
2. Results will be in ./reports (master generates HTML report)

Run in Kubernetes (Helm):
1. helm install jmeter ./k8s/helm-chart -n performance-tests --create-namespace
2. Scale slaves via values.yaml or hpa

AWS ECS (Fargate):
- Use the provided taskdef.json and service example as a starting point. You'll need an ECR image for the master and slaves and proper IAM roles.

