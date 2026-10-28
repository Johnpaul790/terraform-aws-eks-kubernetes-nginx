
# AWS EKS Kubernetes NGINX Deployment

This project demonstrates deploying a containerized NGINX
application on Amazon EKS using Terraform and Kubernetes.

## Technologies
- AWS (EKS, VPC, EC2, Load Balancer)
- Terraform
- Kubernetes
- Docker / NGINX
- YAML

## Architecture

Internet → AWS Load Balancer → Kubernetes Service
→ NGINX Pod

## Project Structure
- `eks-cluster.tf` - EKS cluster configuration
- `vpc.tf` - AWS networking infrastructure
- `providers.tf` - Terraform provider configuration
- `nginx-config.yaml` - Kubernetes Deployment and Service

## Deployment

Initialize and deploy the Terraform infrastructure:

```bash
terraform init
terraform plan
terraform apply
```

After configuring kubectl access to the EKS cluster,
deploy NGINX:

```bash
kubectl apply -f nginx-config.yaml
kubectl get pods
kubectl get svc nginx
```

Use the external load balancer DNS name to access NGINX.

## Cleanup

Delete the Kubernetes resources first:

```bash
kubectl delete -f nginx-config.yaml
```

After verifying that the load balancer is deleted:

```bash
terraform destroy
```
