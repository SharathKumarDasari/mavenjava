#this code is for scripted pipeline
pipeline {
agent any  // Agent: Defines the machine (or slave) that runs the tasks 
   tools{
        maven 'MAVEN-HOME'
    }
    stages {         //The script is divided into stages, each representing a specific step, like building,
        stage('git repo & clean') {
            steps {
                //bat "rmdir  /s /q mavenjava"
                bat "git clone provide your github link"
                bat "mvn clean -f mavenjava"
            }
        }
        stage('install') {
            steps {
                bat "mvn install -f mavenjava" #project name#
            }
        }
        stage('test') {
            steps {
                bat "mvn test -f mavenjava"
            }
        }
        stage('package') {
            steps {
                bat "mvn package -f mavenjava"
            }
        }
    }
}
