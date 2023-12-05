read -s OPENAI_API_KEY
export OPENAI_API_KEY

(
  set -x; cd "$(mktemp -d)" &&
  OS="$(uname | tr '[:upper:]' '[:lower:]')" &&
  ARCH="$(uname -m | sed -e 's/x86_64/amd64/' -e 's/\(arm\)\(64\)\?.*/\1\2/' -e 's/aarch64$/arm64/')" &&
  KREW="krew-${OS}_${ARCH}" &&
  curl -fsSLO "https://github.com/kubernetes-sigs/krew/releases/latest/download/${KREW}.tar.gz" &&
  tar zxvf "${KREW}.tar.gz" &&
  ./"${KREW}" install krew
)
export PATH="${KREW_ROOT:-$HOME/.krew}/bin:$PATH"
kubectl krew update


kubectl krew index add kubectl-ai https://github.com/sozercan/kubectl-ai
k ai "Create Kubernetes Pod Manifest for app image from gcr.io/translatebot-405321/k8s-k3s/demo:v1.0.0 with labels and containerPort 8000"
This will create a Kubernetes Pod named my-demo-pod running the specified container with the given image. Adjust the configuration as needed based on your specific requirements.

k ai "Create Kubernetes Pod liveness probe for namespace demo"
This will create a Pod in the demo namespace with the specified liveness probe. Adjust the configuration as needed for your application.

k ai "Create Kubernetes Pod readiness probe the demo app"
This will create a Pod in the demo namespace with both Liveness and Readiness Probes. Adjust the configuration as needed based on your application's behavior and requirements.

k ai "Create Kubernetes Pod with Volume"
This will create a Pod with a volume that is mounted from the host machine into the container. Adjust the configuration based on your specific volume requirements and paths.

k ai "Create Kubernetes cronjob"
This will create a CronJob named my-cronjob that runs the specified job on the defined schedule. Customize the manifest based on your specific requirements and job specifications.

k ai "Create Kubernetes rsync job"
This will create a Job named rsync-job that runs the rsync command as specified in the container. Adjust the manifest according to your needs.

k ai "Create Kubernetes multicontainer Pod"
This will create a Pod named multi-container-pod with two containers, one running rsync and the other running an Nginx web server. Adjust the paths and configurations as needed for your use case.

k ai "Create Kubernetes add resources Pod with liveness and readiness probes"
This will create a multi-container Pod named multi-container-pod with resource constraints and probes for each container. Customize the configuration as needed for your specific use case.

k ai "Create Kubernetes Pod with container which is using secrets for username and password"
This will create a Pod named app-secret-container with a single container that echoes the values of the username and password obtained from the mysecret1 Secret. Adjust the secret name and key based on your specific use case.