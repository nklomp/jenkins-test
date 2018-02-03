#!/usr/bin/groovy
@Library('pipeline-library@master')

def canaryVersion = "1.0.${env.BUILD_NUMBER}"
def utils = new io.fabric8.Utils()

def test
mavenNode {

 // Checkout code from repository
    stage('Checkout source') {
        checkout scm

    }



    def branch = utils.getBranch();
    def branchType = utils.getBranchType(branch)
    def environment = utils.getDeploymentEnvironmentFromBranchType(branchType)
    def pr = utils.isPR()

    echo "======> Building branch ${branch} of type ${branchType} for env ${environment}, is PR: ${pr}"

    if (utils.isCI()){
        echo'###########################################'
        echo'############ Build snapshot lib '+ canaryVersion
        echo'###########################################'

        buildLibrary{}

    } else if (utils.isCD()){
        echo 'NOTE: running pipelines for the first time will take longer as build and base docker images are pulled onto the node'
        container(name: 'maven') {

            stage('Build Release'){
                mavenCanaryRelease {
                    version = canaryVersion
                }
            }
        }
    } else {
        echo "###############NOPE##################"
    }
}


