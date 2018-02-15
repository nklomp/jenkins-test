#!/usr/bin/groovy
@Library('pipeline-library@master')

def canaryVersion = "1.0.${env.BUILD_NUMBER}"
def utils = new io.fabric8.Utils()

def test

mavenNode {

 // Checkout code from repository

    stage('Checkout source') {
        checkout(scm).each { k,v -> env.setProperty(k, v) }
        sh 'env | sort'

    }



    def branch = utils.getBranch();
    def branchType = utils.getBranchType(branch)
    def ns = utils.getKubernetesNamespaceFromBranchType(branchType)
    def pr = utils.isPR()

    def source = utils.getSourceBranch()
    def target = utils.getTargetBranch()

    echo "======> Building branch ${branch} of type ${branchType} for namespace ${ns}, is PR: ${pr}"
    echo "Source: ${source}, Target: ${target}"




        buildLibrary{}


}


