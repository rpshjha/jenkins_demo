pipeline {

    agent {
        node {
            label 'devops'
        }
    }

    tools {
        maven 'maven3'
    }

    stages {

        stage('Checkout') {
            steps {
                git(
                    url: 'https://github.com/rpshjha/jenkins_demo.git',
                    credentialsId: 'xpc',
                    branch: "${main}"
                )
                

                checkout([$class: 'GitSCM', branches: [[name: '*/branchname']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'jenkins-user-github', url: 'https://github.com/aakashsehgal/FMU.git']]])
                sh "ls -lart ./*"
            }
        }

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

        stage('Publish') {
            steps {
                sh './mvnw package'
            }
            post {
                success {
                    archiveArtifacts 'target/*.jar'
                }
            }
        }

    }
}