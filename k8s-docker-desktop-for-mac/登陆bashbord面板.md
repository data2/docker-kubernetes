部署 Kubernetes dashboard
```
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/v2.0.0-rc5/aio/deploy/recommended.yaml
或
kubectl create -f kubernetes-dashboard.yaml
```

检查 kubernetes-dashboard 应用状态
```kubectl get pod -n kubernetes-dashboard```

开启 API Server 访问代理
```kubectl proxy```

通过如下 URL 访问 Kubernetes dashboard
```
http://localhost:8001/api/v1/namespaces/kubernetes-dashboard/services/https:kubernetes-dashboard:/proxy/
```

配置控制台访问令牌
对于Mac环境
```
TOKEN=$(kubectl -n kube-system describe secret default| awk '$1=="token:"{print $2}')
kubectl config set-credentials docker-for-desktop --token="${TOKEN}"
echo $TOKEN
```

对于Windows环境
```$TOKEN=((kubectl -n kube-system describe secret default | Select-String "token:") -split " +")[1]
kubectl config set-credentials docker-for-desktop --token="${TOKEN}"
echo $TOKEN```
