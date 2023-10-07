# Prometheus and Grafana Deployment on Kubernetes

This repository contains Kubernetes manifests and configuration files for deploying Prometheus and Grafana on a Kubernetes cluster. Prometheus is an open-source monitoring and alerting toolkit, and Grafana is a popular open-source platform for visualizing and monitoring data.

## Prerequisites

Before you begin, ensure you have the following prerequisites:

- A running Kubernetes cluster. You can use Minikube, Kind, or a managed Kubernetes service like GKE, EKS, or AKS.
- `kubectl` command-line tool configured to use your Kubernetes cluster.

1. Clone this repository to your local machine:

   ```bash
   git clone https://github.com/Kartikdudeja/prometheus-grafana-k8s.git
   ```

2. Change into the project directory:

   ```bash
   cd prometheus-grafana-k8s
   ```
3. Deploy Prometheus and Grafana using provided Manifest files  

   ``` bash
   kubectl create -k .
   ```

4. Access Prometheus and Grafana:

   - To access Prometheus, you can use a port-forward command:

     ```bash
     kubectl port-forward <prometheus-pod-name> 9090
     ```

     Then open your web browser and navigate to http://localhost:9090.

   - To access Grafana, you can use a port-forward command:

     ```bash
     kubectl port-forward <grafana-pod-name> 3000
     ```

     Then open your web browser and navigate to http://localhost:3000.

     Default Grafana credentials:
     - Username: `admin`
     - Password: `admin`

5. Configure Grafana:

   - Add Prometheus as a data source in Grafana using the URL `http://prometheus:9090`
   - Import or create your dashboards in Grafana for monitoring your applications and infrastructure.
  
## Cleanup

To remove Prometheus and Grafana from your Kubernetes cluster, run the following commands:

```bash
kubectl delete -k .
```

## Customization

You can customize Prometheus and Grafana configurations by editing the YAML files. Refer to the official Prometheus and Grafana documentation for advanced configuration options.

## Monitoring Targets

To monitor your applications and services, you need to configure Prometheus to scrape the appropriate targets. Update the Prometheus configuration in the `prometheus-configmap.yaml` file to add or modify scraping targets.
