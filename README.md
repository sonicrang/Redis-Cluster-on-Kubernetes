config:
edit namespace in all yaml files
edit dns address in job.yaml like "redis-cluster-0.redis-service.redis(namespace).svc.cluster.local"
edit configmap
edit nfs address in redis-pv-helm-values.yaml


install:
helm install --values redis-pv-helm-values.yaml --name redis-pv --namespace redis stable/nfs-client-provisioner
kubectl apply -f configmap.yaml
kubectl apply -f service.yaml
kubectl apply -f statefulset.yaml
kubectl apply -f job.yaml

uninstall:
helm delete --purge redis-pv
kubectl delete -f configmap.yaml
kubectl delete -f service.yaml
kubectl delete -f statefulset.yaml
kubectl delete -f job.yaml


