Create namespace:
	kubectl create namespace prom-grafana
Add repo:
	helm install promi stable/prometheus-operator
	
Check all:

	kubectl  get pods -l "release=promi" -n prom-grafana
	kubectl get all
	kubectl get pod/alertmanager-promi-prometheus-operator-alertmanager-0 --n prom-grafana -o wide
	kubectl get endpoints/promi-grafana  -o wide
	kubectl get service/promi-grafana -n prom-grafana -o wide
	kubectl get servicemonitor -o wide
	kubectl get deployment/promi-grafana --namespace prom-grafana -o wide

To check:
	kubectl log deployments/promi-grafana -n prom-grafana  //find port 
	kubectl port-forward deployments/promi-grafana 3000 -n prom-grafana
	kubectl port-forward pods/prometheus-promi-prometheus-operator-prometheus-0 9090 -n prom-grafana
	