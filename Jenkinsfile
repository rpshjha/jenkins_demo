pipeline {

    agent {
        node {
            label 'devops'
        }
    }

    tools {
        maven 'maven3'
    }

    options {
        buildDiscarder logRotator(
                    daysToKeepStr: '15',
                    numToKeepStr: '10'
            )
    }

    environment {
        APP_NAME = "DCUBE_APP",
        APP_ENV  = "DEV"
    }

    stages {

        stage('build') {
            steps {
                 echo 'building the application'
                 sh 'mvn install -Dmaven.test.skip=true'
            }
        }

        stage('test') {
             steps {
                   echo 'test the application'

             }
        }

        stage('deploy') {
              steps {
                    echo 'deploy the application'
              
              }
        }

        stage('Priting All Global Variables') {
            steps {
                sh """
                env
                """
            }
        }

    }
}