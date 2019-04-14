# Akvelon-test-task

How to run from scratch:

#Устанавливаем microk8s на дистрибутив Ubuntu. По умолчанию  Ingrees  включен в microk8s , достаточно просто просто активировать
sudo snap install microk8s --classic
sudo microk8s.start
snap alias microk8s.kubectl kubectl
microk8s.enable ingress

#Сохдадим сертификат и добавим его в secrets
openssl req -x509 -newkey rsa:4096 -sha256 -nodes -keyout tls.key -out tls.crt -subj "/CN=example.com" -days 999
kubectl create secret tls example-com-tls --cert=tls.crt --key=tls.key

#Скачаем yml файл проекта и запустим его
git clone https://github.com/redbull05689/Akvelon-test-task
cd Akvelon-test-task
kubectl apply -f vote-app.yaml

Для примера был взят образ приложения для голосования из репозитория Макрософт. Приложение состоит из бэкенд и фронтенд частей, которые были описаны типом Deployment.  Также для них были описанны сервисы для доступа. Финально был добавлен Ingress с использованием ранее сгенеренного сертификата
