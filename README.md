## get container list 


kubectl get pods --all-namespaces -o=custom-columns=NameSpace:.metadata.namespace,NAME:.metadata.name,CONTAINERS:.spec.containers[*].name

##example

kubectl get pods awx-operator-controller-manager-647f4c5c7d-hphht -o=custom-columns=NameSpace:.metadata.namespace,NAME:.metadata.name,CONTAINERS:.spec.containers[*].name -n awx



kubectl get pods awx-75bd7d77d5-v78wc  -o=custom-columns=NameSpace:.metadata.namespace,NAME:.metadata.name,CONTAINERS:.spec.containers[*].name -n awx


---------------------------------------------------------------------------------------
## Enter container 

kubectl exec mypod -c ruby-container -i -t -- bash -il

kubectl exec awx-operator-controller-manager-647f4c5c7d-hphht --namespace awx -c awx-manager -i -t -- bash -il
kubectl exec awx-operator-controller-manager-647f4c5c7d-hphht --namespace awx -c  kube-rbac-proxy -i -t -- bash -il

##### AWX Path ########

kubectl exec awx-75bd7d77d5-v78wc --namespace awx -c awx-web -i -t -- bash -il


----------------------------------------------------------------------


