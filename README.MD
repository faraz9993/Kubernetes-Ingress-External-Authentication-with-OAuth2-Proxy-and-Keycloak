1. I have 5 files in my home directory.
2. Go to this webpage https://www.keycloak.org/getting-started/getting-started-kube to install and run Keycloak. 
3. In the above step use the Keycloak file in my repo named keycloak.yaml .
4. After the sucessful deployment of ingress service you need to deployed my web-app in the file app.yaml.
5. After deploying these two services, you must be able to open the webpage on the IP 10.101.95.46
6. Then deploy the redis service using redis.yaml after creating appropriate namespaces as per given in the file.
7. Then, you will have to creat an OAuth App on GitHub. 
8. I have created the OAuth App with below details:
	Application name: <As_you_want>
	Homepage URL: http://foo.bar.com
	Authoriztion callback URL: http://10.101.95.46/
9. Then deploy the OAuth2 Proxy service using Oauth2_prox_deploy.yaml
10. Then you need to deploy the OAuth2 proxy configuration using OAuth2_proxy_config.yaml file.
11. You need to make the appropriate changes in the OAuth2_proxy_config.yaml as per the OAuth app you created earlier on GitHub. I had to enter the client id, client secret and cookie secret in the OAuth2_proxy_config.yaml file as per my OAuth application.
12. Give the below entry in /etc/hosts file of your local host:
192.168.49.2    foo.bar.com
192.168.49.2 is an IP address where your ingress service will be running.
12. After the successful deployment of all the services, when you will search “foo.bar.com/index.html”, it should take you to the GitHub page for the authentication.
13. After the successful authenticatin from login id and password you would be redirected to your desired web-page.

Important commands:
kubectl get pod -A
kubectl logs <pod_name> -n <namespace_name> --follow