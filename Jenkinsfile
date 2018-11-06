pipeline {
         agent any
         stages {
                 stage('first') {
                 steps {
                     echo 'Hi, this is Jay testing pipeline using Jenkinsfile on branch2'
                 }
                 }
                 stage('Second') {
                 steps {
                    input('Do you want to proceed?')
                 }
                 }
                 stage('Third') {
                 when {
                       not {
                            branch "branch2"
                       }
                 }
                 steps {
                       echo "Hello"
                 }
                 }
                 stage('Fourth') {
                 parallel { 
                            stage('Tests') {
                           steps {
                                echo "Running the unit test on branch2..."
                           }
                           }
                            stage('docker slave 1') {
                              agent { label 'testslave' }
                              steps {
                                echo "Running the integration test on branch2..."
                              }
                           }
                          stage('docker slave 2') {
                              agent { label 'testslave1' }
                                   steps {
                                   echo "Running the unit tests on testslave1"
                                   }
                                   }
                          stage('docker slave 3') {
                                   agent{ label 'testslave2'}
                                   steps{ 
                                   echo "Running the functional test on testslave2 node"
                                   }
                          }
                          stage('docker slave 4') {
                              agent { label 'testslave1' }
                                   steps {
                                   echo "Running the unit tests on testslave1"
                                   }
                                   }
                          stage('docker slave 5') {
                                   agent{ label 'testslave2'}
                                   steps{ 
                                   echo "Running the functional test on testslave2 node"
                                   }
                          }
                           }
                           }
              }
}
