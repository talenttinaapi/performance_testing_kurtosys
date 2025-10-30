Runbook: Distributed JMeter & Cloud Execution

Docker (local):
- Build and run:
  docker compose up --build
- Master will coordinate slaves at jmeter-slave1,jmeter-slave2
- Reports available in ./reports (master produces HTML)

Kubernetes (Helm):
- Build and push your JMeter image to a registry (ECR/GCR/DockerHub)
- Update values.yaml.image.repository and tag
- helm install jmeter ./k8s/helm-chart -n performance-tests --create-namespace
- To view logs: kubectl logs deployment/jmeter-master

AWS ECS (Fargate):
- Build and push images for master and slaves to ECR
- Use aws ecs register-task-definition --cli-input-json file://aws/taskdef.json
- Create service using CloudFormation or AWS Console
- Ensure security groups allow required ports (RMI 1099 and 60000-60010) between tasks

Security & Networking:
- For cloud, prefer using VPN or VPC peering for secure RMI communication.
- Use IAM roles for tasks, and restrict S3/ECR access minimally.
