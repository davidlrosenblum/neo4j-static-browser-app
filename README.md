# neo4j-static-browser-app

Docker Image for a web server that serves Neo4j static browser content

To use with Kubernetes

-  Clone repo
-  `docker build . --tag <repositoryName>/neo4jbrowser:4.3.1   `
-  `docker push <repositoryName>/neo4jbrowser:4.3.1   `

  To test outside of Kubernetes
-  `docker run -it --rm -d -p 8080:80  <repositoryName>/neo4jbrowser:4.3.1`
  
As there is no ssl on this image - will not work with a SSL protected Neo4jServer.  We are assuming a private vpc.

  We have sample kubernetes commands in the config directory - neo4j_browser_app.yaml will start a workload, and neo4j_browser_service.yaml which will start
  a load balancer service in your internal vpc.  Please modify neo4j_browser_app.yaml to point to your docker repository
  
  ### To start the app in kubernetes
  -  `kubectl apply -f neo4j_browser_app.yaml`
  -  `kubectl apply -f neo4j-browser-service.yaml`
  -  You can stop the app by scaling to 0
  -  `kubectl scale deployment neo4jbrowser --replicas=0`
  -  To delete the app
  -  `kubectl delete deployment neo4jbrowser`
