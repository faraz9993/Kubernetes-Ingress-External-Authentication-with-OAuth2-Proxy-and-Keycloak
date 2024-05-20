1. I have 5 files in /home/einfochips/keycloak.
2. Went to https://www.keycloak.org/getting-started/getting-started-kube
3. Followed the steps given in above link to create kubectl create -f keycloak.yaml
4.  After the ingress service is deployed I needed to create application web page using command kubectl create -f app.yaml
5. After deploying these two, 10.101.95.46 was opening my desired webpage.
6. Then created kubectl create -f redis.yaml after creating appropriate namespaces.
7. Then, I created an OAuth App on GitHub. I have created the OAuth App with below details:
	Application name: Einfochips
	Homepage URL: http://foo.bar.com
	Authoriztion callback URL: http://10.101.95.46/
8. Then created OAuth2 Proxy Deployment file using kubectl create -f Oauth2_prox_deploy.yaml
9. Created configuration file with OAuth2 Proxy Configuration file with Oauth2_proxy_config.yaml
10. I had to enter the client id, client secret and cookie secret in the configuration file as per my OAuth application.
11. Gave the below entry in /etc /hosts:
192.168.49.2    foo.bar.com
192.168.49.2 is an IP address where ingress service is running.
12. After the successful deployment of all the services, when I search “foo.bar.com/index.html”, it takes me to the to the GitHub page for the authentication.
13. After the successful authenticatin from login id and password I was redirected to my desired web-page.

Important commands:
kubectl get pod -A
kubectl logs <pod_name> -n <namespace_name> --follow