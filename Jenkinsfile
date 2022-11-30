pipeline {

//     agent any
    agent {
        label 'devops'
    }
    tools {
        maven 'Maven'
    }

    stages {

        stage('Checkout') {
            steps {
                git(
                    url: 'https://github.com/rpshjha/jenkins_demo.git',
//                  credentialsId: 'credentialsId',
                    branch: "main"
                )

                sh "ls -lart ./*"
            }
        }

        stage('build') {
            steps {
                 echo 'building the application'
                 sh 'mvn -f hellocucumber/pom.xml clean install'
            }
            post {
               success {
                    echo 'Build success'
               }
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

        stage('Publish') {
            steps {
                sh 'mvn -f hellocucumber package'
            }
            post {
                success {
                    archiveArtifacts 'hellocucumber/target/*.jar'
                }
            }
        }

    }
}