# Pre Setup

1. [KIND](https://kind.sigs.k8s.io/docs/user/quick-start/#installation)
2. [kubectl](https://v1-18.docs.kubernetes.io/docs/tasks/tools/install-kubectl/)
3. [helm](https://helm.sh/docs/intro/install/)
4. [apache-airflow](https://artifacthub.io/packages/helm/apache-airflow/airflow?modal=install)

```console
helm repo add apache-airflow https://airflow.apache.org/
```

```console
helm install my-airflow apache-airflow/airflow --version 1.2.0
```

## Setup

```console
kind create cluster --config kind-cluster.yaml --name cluster-test-${USERNAME}
```

```console
kubectl create namespace airflow
```

```console
helm install apache-airflow apache-airflow/airflow --version 1.2.0 --values values-airflow.yaml --debug -n airflow
```

```console
kubectl get po -n airflow
```

```console
kubectl port-forward svc/apache-airflow-webserver 8080:8080 --namespace airflow
```

## Shutdown

```console
kind delete cluster --name cluster-test-${USERNAME}
```
