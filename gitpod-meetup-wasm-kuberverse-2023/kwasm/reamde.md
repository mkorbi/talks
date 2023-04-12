# Create cluster
kind create cluster --config cluster.yaml
# Add helm repo
helm repo add kwasm http://kwasm.sh/kwasm-operator/
# Install operator
helm install -n kwasm --create-namespace kwasm-operator kwasm/kwasm-operator
# Annotate single node
kubectl annotate node kind-worker2 kwasm.sh/kwasm-node=true
# Run example
kubectl apply -f runtimeclass.yaml
kubectl apply -f pod.yaml


# Analysis
k get nodes --show-labels

k describe po wasi-demo

k logs wasi-demo

