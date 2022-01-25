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


---
- hosts: localhost
  connection: local
  gather_facts: false
  collections:
    - cisco.ucs

  tasks:
  - name: Configure Service Profile from Template
    ucs_service_profile_from_template:
      hostname: 10.240.4.90
      username: admin
      password: "{{ password }}"
      name: "{{ host_name }}"
      source_template: compute-nodes-m5
      org_dn: org-root/org-SDX
      state:  present
  - name: Query UCS Distinguished Names
    ucs_query:
      hostname: 10.240.4.90
      username: admin
      password: "{{ password }}"
      distinguished_names: sys/chassis-1/blade-1/adaptor-1/host-eth-1
      delegate_to: localhost
    register: result
  - debug:
      msg: "{{ result }}"


-----------------------------------------------------------------------------------

---
- hosts: localhost
  connection: local
  gather_facts: false
  collections:
    - cisco.ucs

  tasks:
  - name: Configure Service Profile from Template
    ucs_service_profile_from_template:
      hostname: 10.240.4.90
      username: admin
      password: "{{ password }}"
      name: "{{ host_name }}"
      source_template: compute-nodes-m5
      org_dn: org-root/org-SDX
      state:  present
  - name: Query UCS Distinguished Names
    ucs_query:
      hostname: 10.240.4.90
      username: admin
      password: "{{ password }}"
      distinguished_names: sys/chassis-1/blade-1/adaptor-1/host-eth-1
      delegate_to: localhost
    register: result
  - debug:
      msg: "{{ result }}"

