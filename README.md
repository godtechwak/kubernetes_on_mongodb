# *단일 노드 MongoDB 쿠버네티스 설치 방법*
### 1. mongo-client 설치
```bash
kctl apply -f mongodb-client.yaml
```
### 2. PV 생성
```bash
kctl apply -f mongodb-pv.yaml
```
### 3. PVC 생성
```bash
kctl apply -f mongodb-pvc.yaml
```
### 4. Secret 생성
```bash
kctl apply -f mongodb-secrets.yaml
```
### 5. Deployment 생성
```bash
kctl apply -f mongodb-deployment.yaml
```
### 6. Service 생성
```bash
kctl apply -f mongodb-nodeport-svc.yaml
```

# *MongoDB 쿠버네티스 접속 방법*
### 1. minikube ip 확인
```bash
$ minikube ip
192.168.49.2
```
### 2. mongo-nodeport-svc 서비스 URL 오픈
```bash
minikube service --url mongo-nodeport-svc -n mongodb
```
### 3. MongoDB 접속
```bash
mongo --host 192.168.49.2 --port 32000 -u adminuser -p
```
