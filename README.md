## get container list 


kubectl get pods --all-namespaces -o=custom-columns=NameSpace:.metadata.namespace,NAME:.metadata.name,CONTAINERS:.spec.containers[*].name

##example

kubectl get pods awx-operator-controller-manager-647f4c5c7d-hphht -o=custom-columns=NameSpace:.metadata.namespace,NAME:.metadata.name,CONTAINERS:.spec.containers[*].name -n awx

---------------------------------------------------------------------------------------

