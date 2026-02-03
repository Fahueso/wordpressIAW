# WordPress sobre Kubernetes (Minikube) en EC2 — Paso a paso**

---

# 🟦 1. **Crear la EC2**

**Requisitos recomendados:**

- Ubuntu 22.04 / 24.04
- t3.large 
- **Disco: 20 GB (mínimo recomendado)**
- Security Group: permitir **22** (SSH), puerto 8080, puerto 80

---

# 🟦 2. **Instalar Docker, kubectl y Minikube**

### ➤ Actualizar sistema

sudo apt update -y && sudo apt upgrade -y

### ➤ Instalar dependencias

sudo apt install -y curl wget apt-transport-https ca-certificates gnupg lsb-release software-properties-common

### ➤ Instalar Docker

sudo apt install -y docker.io

sudo usermod -aG docker $USER

newgrp docker

sudo systemctl enable --now docker

### ➤ Instalar kubectl

curl -LO "https://dl.k8s.io/release/$(curl -fsSL https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"

sudo install -m 0755 kubectl /usr/local/bin/kubectl

### ➤ Instalar Minikube

curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64

sudo install minikube-linux-amd64 /usr/local/bin/minikube

---

# 🟦 3. **Iniciar Minikube**

minikube start --driver=docker --cpus=2 --memory=4096

Verificar:

minikube status

kubectl get nodes

---

# 🟦 4. **Instalar Helm**

curl -fsSL https://raw.githubusercontent.com/helm/helm/master/scripts/get-helm-3 | bash

helm version

---

# 🟦 5. **Instalar WordPress con Helm**

helm repo add bitnami https://charts.bitnami.com/bitnami

helm repo update

helm install miwp bitnami/wordpress

Ver los pods:

kubectl get pods -w

Esperar hasta que WordPress y MariaDB estén **Running**.

---

# 🟦 6. **Obtener la contraseña de WordPress**

kubectl get secret miwp-wordpress -o jsonpath="{.data.wordpress-password}" | base64 -d ; echo

Usuario: **user**

---

# 🟦 7. **Exponer WordPress en el PUERTO 80** (Método fiable en Minikube + EC2)

La forma **estable, sin Ingress y sin NodePort** es usar port-forward.

### ➤ 7.1 Permitir a kubectl usar puertos bajos

sudo apt install -y libcap2-bin

sudo setcap 'cap_net_bind_service=+ep' $(which kubectl)

### ➤ 7.2 Hacer port-forward del servicio al puerto 80

kubectl port-forward svc/miwp-wordpress 80:80 --address=0.0.0.0

### ➤ 7.3 Abrir puerto 80 en AWS

En Security Groups → Inbound Rules:

- **Type:** HTTP
- **Port:** 80
- **Source:** 0.0.0.0/0

### ➤ 7.4 Acceder desde navegador:

```
http://IP_PUBLICA_DE_TU_EC2
```

---

# 🟦 8. **Escalado (más pods)**

## 8.1 Escalado manual (no es util)

kubectl scale deploy miwp-wordpress --replicas=3

kubectl get pods


---

# 🟦 9. **Notas importantes para clase**

1. En Minikube **no hay balanceo real** entre pods expuestos al exterior.
2. El escalado es útil **como concepto**, pero no como producción.
3. El port-forward es la única forma fiable de exponer WordPress en EC2.


---

# 🟦 10. **Comandos útiles**

Reiniciar Minikube:

minikube delete

minikube start --driver=docker --cpus=2 --memory=4096

Ver logs de WordPress:

kubectl logs deploy/miwp-wordpress

Eliminar WordPress:

helm uninstall miwp


Instala otros:

helm repo add grafana https://grafana.github.io/helm-charts
helm repo update
helm install mi-grafana grafana/grafana

kubectl port-forward svc/mi-grafana 8081:80 --address=0.0.0.0


[nextcloud 8.9.0 · nextcloud/nextcloud](https://artifacthub.io/packages/helm/nextcloud/nextcloud)


