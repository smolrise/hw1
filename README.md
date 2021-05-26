# hw1
1. Для сборки образа необходимо запустить внутри дирректории my-ws:
docker build -t my-ws:v1 .

2. Gосле этого в родительской дирректории:
kubectl apply -f deployment.yaml -f service.yaml -f ingress.yaml
или
skaffold run

3. Если необходимо получать ответ от сервиса по имени хоста, тогда в конец /etc/hosts надо добавить запись
<ip_kubernates> arch.homework
где <ip_kubernates> - это ip Kubernates. В моем случае, его можно получить командой minikube ip

Сервис доступен по URI:
curl -H'host: arch.homework' http://<ip_kubernates>/health
либо, если прописан /etc/hosts, то
curl -H'host: arch.homework' http://arch.homework/health

также доступна ручка /version
