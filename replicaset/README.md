# *MongoDB 레플리카셋 쿠버네티스 설치 방법*
### 1. ConfigMap 설치
```bash
kctl apply -f mongodb-configmap.yaml
```
### 2. Service 설치
```bash
kctl apply -f mongodb-service.yaml
```
### 3. Statefulset 설치
```bash
kctl apply -f mongodb-statefulset.yaml
```
# *MongoDB 레플리카셋 쿠버네티스 접속 방법*
### 1. mongos가 설치된 pod 터미널 접속
```bash
kubectl run mongodb-client --rm -it --image=mongo --command -- /bin/bash
```
### 2. mongo 접속
```bash
mongosh mongodb://mongodb-0.mongodb.mongodb.svc.cluster.local:27017
```
### 3. 레플리카셋 초기화
```bash
rs.initiate()
```
