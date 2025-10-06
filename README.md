# Kubernetes-Learning
This repository is a structured resource for exploring and mastering Kubernetes. It provides practical examples, hands-on manifests, and clear explanations of essential concepts such as Pods, Deployments, Services, ConfigMaps, Secrets, and resource management. Whether you’re just starting your Kubernetes journey or looking to deepen your understanding of advanced topics, this repository is designed to support both learning and experimentation in a real-world context.

"kubectl create"- it creates a new resource based on the provided configuration file.If the resource already exists, kubectl create will return an error, indicating that the resource already exists.
It's typically used for creating resources that don't already exist in the cluster.

"kubectl apply" - is used to create or update resources based on the provided configuration file. If the resource already exists, kubectl apply will update the existing resource with the new configuration. 

kubectl apply is idempotent, i.e., we can apply the same configuration multiple times, and it will ensure that the resource is in the desired state. It's commonly used for both creating new resources and updating existing ones.
