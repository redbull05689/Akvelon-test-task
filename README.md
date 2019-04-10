# Akvelon-test-task

How to run from scratch:

sudo snap install microk8s --classic
sudo microk8s.start
snap alias microk8s.kubectl kubectl
microk8s.enable ingress

openssl req -x509 -newkey rsa:4096 -sha256 -nodes -keyout tls.key -out tls.crt -subj "/CN=example.com" -days 999
kubectl create secret tls example-com-tls --cert=tls.crt --key=tls.key

git clone https://github.com/redbull05689/Akvelon-test-task
cd Akvelon-test-task
openssl req -x509 -newkey rsa:4096 -sha256 -nodes -keyout tls.key -out tls.crt -subj "/CN=example.com" -days 999
kubectl create secret tls example-com-tls --cert=tls.crt --key=tls.key
kubectl apply -f vote-app.yaml

