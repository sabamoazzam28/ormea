---
- hosts: localhost
  become: true
  vars:
     namespace: dev
  tasks:
    - name: Check if kubectl is installed
      command: kubectl version --short
      become_user: ubuntu
      register: kube_version
    - name: Install kubectl
      shell: curl -LO "https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl"
      when: kube_version.rc==1
    - name: Granting exec permission 
      file:
        path: ./kubectl
        mode: '775'
      when: kube_version.rc==1
    - name: Moving executable to bin folder
      command: mv kubectl /usr/local/bin/
      when: kube_version.rc==1
    - name: Build  Application Dockerfile
      shell: docker build -t firdous24/nginx:v2
    - name: Build  SideCar Dockerfile
      shell: docker build firdous24/fluentbit:v2
    - name: Create namespace
      command: kubectl create ns dev
      become_user: ubuntu
      ignore_errors: yes
      become_user: ubuntu
    - name: Install helm
      shell: helm install nginx . -n {{ namespace }}
      ignore_errors: yes
    - name: Deploy Rancher through LoadBalancer
      shell: kubectl apply -f https://myrancher.devops.mhealth.tech/v3/import/hdpwnvbdpeybvmqpebzmdvpsdbldrogablosirufdnbmwedklei.yaml -n {{ namespace }}
      ignore_errors: yes
