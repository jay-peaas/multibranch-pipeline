pipeline {
         agent any
         stages {
                 stage('One') {
                 steps {
                     echo 'Hi, this is Jay testing pipeline using Jenkinsfile on branch master and branch1'
                 }
                 }
                 stage('Two') {
                 steps {
                    input('Do you want to proceed?')
                 }
                 }
                 stage('Three') {
                 when {
                       not {
                            branch "branch1" && "master"
                       }
                 }
                 steps {
                       echo "Hello"
                 }
                 }
                 stage('Four') {
                 parallel { 
                            stage('Unit Test') {
                           steps {
                                echo "Running the unit test on master and branch1..."
                           }
                           }
                            stage('Integration test') {
                              agent { label 'testslave2' }
                              steps {
                                echo "Running the integration test on master and branch1..."
                              }
                           }
                           }
                           }
              }
}
