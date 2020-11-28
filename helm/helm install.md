Install helm:
	$ curl -fsSL -o get_helm.sh https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3
	$ chmod 700 get_helm.sh
	$ ./get_helm.sh

ubontu:

	curl https://baltocdn.com/helm/signing.asc | sudo apt-key add -
	sudo apt-get install apt-transport-https --yes
	echo "deb https://baltocdn.com/helm/stable/debian/ all main" | sudo tee /etc/apt/sources.list.d/helm-stable-debian.list
	sudo apt-get update
	sudo apt-get install helm

Add repo:
Initialize a Helm Chart Repository

	helm repo add stable https://charts.helm.sh/stable

	helm search repo stable

	helm repo update 

	helm install stable/mysql --generate-name
	
	
https://helm.sh/docs/intro/quickstart/