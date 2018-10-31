pipeline {
         agent any
         stages {
                 stage('One') {
                 steps {
                     echo 'Hi, this is Jay testing pipeline using Jenkinsfile on branch2'
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
                            branch "branch2"
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
                                echo "Running the unit test on branch2..."
                           }
                           }
                            stage('Integration test') {
                              agent { label 'testslave' }
                              steps {
                                echo "Running the integration test on branch2..."
                              }
                           }
                          stage('Unit tests') {
                              agent { label 'testslave1' }
                                   steps {
                                   echo "Running the unit tests on testslave1"
                                   }
                                   }
                           }
                           }
              }
}
