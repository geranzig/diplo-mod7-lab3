#!groovy

pipeline {
  agent any
  stages {
    stage('Compilación') {
        steps {
            sh './mvnw clean compile -e'
        }
    }

    stage('Docker Build') {
    	agent any
      steps {
      	sh 'docker build -t geranzig/grupo5mod7taller3:v1  .'
      }
    }

 stage('Docker Push') {
    	agent any
      steps {
      	withCredentials([usernamePassword(credentialsId: 'dockerHub', passwordVariable: 'dockerHubPassword', usernameVariable: 'dockerHubUser')]) {
        	sh "docker login -u ${env.dockerHubUser} -p ${env.dockerHubPassword}"
          sh 'docker push geranzig/grupo5mod7taller3:v1 '
        }
      }

  }
}