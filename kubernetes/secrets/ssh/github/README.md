Create a secret named jenkins-maven-settings in namespace develop using the contents from the settings.xml with key settings.xml. This will result in the example jenkins-maven-settings.yaml but then applied to the Kubernetes cluster.

    kubectl create secret -n develop generic jenkins-ssh-config --from-file=./id_rsa --from-file=./id_rsa.pub
    
To apply the yam manually use the yaml from this directory and use

    kubectl apply -f jenkins-ssh-config.yaml


Update the yaml with:

    kubectl get secret -n develop jenkins-ssh-config -o yaml    