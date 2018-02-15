Create persistent volume claim in namespace develop

    kubectl -n develop -f jenkins-maven-local-repo-claim.yaml apply
     
persistentvolumeclaim "jenkins-maven-local-repo" created


    kubectl -n develop get pvc jenkins-maven-local-repo -o yaml
    apiVersion: v1
    kind: PersistentVolumeClaim
    metadata:
      annotations:
        kubectl.kubernetes.io/last-applied-configuration: |
          {"apiVersion":"v1","kind":"PersistentVolumeClaim","metadata":{"annotations":{},"name":"jenkins-maven-local-repo","namespace":"develop"},"spec":{"accessModes":["ReadWriteMany"],"resources":{"requests":{"storage":"5Gi"}},"storageClassName":"mvndevstorageclass"}}
        pv.kubernetes.io/bind-completed: "yes"
        pv.kubernetes.io/bound-by-controller: "yes"
        volume.beta.kubernetes.io/storage-provisioner: kubernetes.io/azure-file
      creationTimestamp: 2018-02-02T00:09:57Z
      name: jenkins-maven-local-repo
      namespace: develop
      resourceVersion: "4024422"
      selfLink: /api/v1/namespaces/develop/persistentvolumeclaims/jenkins-maven-local-repo
      uid: 66d8bb85-07ad-11e8-ab00-0a58ac1f1a0a
    spec:
      accessModes:
      - ReadWriteMany
      resources:
        requests:
          storage: 5Gi
      storageClassName: mvndevstorageclass
      volumeName: pvc-66d8bb85-07ad-11e8-ab00-0a58ac1f1a0a
    status:
      accessModes:
      - ReadWriteMany
      capacity:
        storage: 5Gi
      phase: Bound