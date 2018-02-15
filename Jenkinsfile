#!/usr/bin/groovy
@Library('pipeline-library@master')

def canaryVersion = "1.0.${env.BUILD_NUMBER}"
def utils = new io.fabric8.Utils()

def test
node {
    stage('Env') {
        sh 'env | sort'
     }
}

mavenNode {

 // Checkout code from repository
/*
    stage('Checkout source') {
        def scmVars = checkout scm
        echo "$scmVars"

    }
*/


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


