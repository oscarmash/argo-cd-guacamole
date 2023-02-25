# argo-cd-guacamole

# Instalación de Argo CD

$ helm upgrade --install argo-cd argo/argo-cd \
--create-namespace \
--namespace argo-cd \
--version=5.22.1

$ k ns argo-cd
$ k get pods
$ k patch svc argo-cd-argocd-server -n argo-cd -p '{"spec": {"type": "LoadBalancer"}}'
$ k get svc
$ k -n argo-cd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo

# Primeros pasos:

Antes de hacer nada, hacer login:

$ argocd --insecure login 172.26.20.251:443
Username: admin
Password: 4Nam6r6VbukA4VpN

La password se ha sacado de:

$ kubectl -n argo-cd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d; echo


Añadimos nuestro repositorio:

$ argocd repo add git@github.com:oscarmash/argo-cd-guacamole.git --ssh-private-key-path $HOME/.ssh/id_rsa

Lo podremos ver en la GUI:
	Setting -> Repositories


