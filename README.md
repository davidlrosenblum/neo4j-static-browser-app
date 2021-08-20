# neo4j-static-http-app
Docker Image for a web server that serves Neo4j static browser content
To use with Kubernetes
Clone repo
docker build . --tag <repositoryName>/neo4jbrowser:4.3.1   
docker push <repositoryName>/neo4jbrowser:4.3.1   
To test outside of Kubernetes
docker run -it --rm -d -p 8080:80  <repositoryName>/neo4jbrowser:4.3.1
As there is no ssl on this image - will not work with a SSL protected Neo4jServer
We have sample kubernetes command in the config directory
  To start the app
  kubectl apply -f neo4j_browser_app.yaml
  You can stop the app by scaling to 0
  kubectl scale deployment neo4jbrowser --replicas=0
  Then delete the app
  kubectl delete deployment neo4jbrowser
