Deploy Tomcat App on Kubernetes
```bash
apiVersion: v1                                    
kind: Namespace                                   
metadata:                                         
  name: tomcat-namespace-datacenter               
  labels:                                         
    name: tomcat-balu                             
                                                  
---                                               
apiVersion: apps/v1                               
kind: Deployment                                  
metadata:                                         
  name: tomcat-deployment-datacenter              
  namespace: tomcat-namespace-datacenter          
spec:                                             
  replicas: 1                                     
  selector:                                       
    matchLabels:                                  
      app: tomcat-balu                            
  template:                                       
    metadata:                                     
      labels:                                     
        app: tomcat-balu                          
    spec:                                         
      containers:                                 
      - name: tomcat-container-datacenter         
        image: gcr.io/kodekloud/centos-ssh-enabled:tomcat 
        ports:                                    
        - containerPort: 8080       
                         
       
     
---    
apiVersion: v1                                            
kind: Service                                             
metadata:                                                 
  name: tomcat-service-datacenter                       
spec:  
  type: NodePort 
  selector: 
	app: tomcat-balu 
  ports:                                                  
	- port: 80                                            
	  protocol: TCP                                       
	  targetPort: 8080                                    
	  nodePort: 32227                                     
	
