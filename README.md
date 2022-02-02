## get container list 


kubectl get pods --all-namespaces -o=custom-columns=NameSpace:.metadata.namespace,NAME:.metadata.name,CONTAINERS:.spec.containers[*].name

##example

kubectl get pods awx-operator-controller-manager-647f4c5c7d-hphht -o=custom-columns=NameSpace:.metadata.namespace,NAME:.metadata.name,CONTAINERS:.spec.containers[*].name -n awx



kubectl get pods awx-75bd7d77d5-v78wc  -o=custom-columns=NameSpace:.metadata.namespace,NAME:.metadata.name,CONTAINERS:.spec.containers[*].name -n awx
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

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

https://computingforgeeks.com/how-to-install-ansible-awx-on-ubuntu-linux/
---------------------------------------------------------------

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
---------------------------------------------------------------------------------

1) Create Service profile from template 
2) Attach  Service profile  to a  server
3) Record IQN ,  WWN details
4) Login in to Pure , create a lun using those IQN details
5) Login KVM of UCS
6) Activate virtual drivers, insert esxi ISO  , install on the boot lun created above.
7) Add management IP , DNS,NTP and add it to  the vcenter.


