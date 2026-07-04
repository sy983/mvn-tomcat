pipeline {
    agent any
 //       triggers {
  //      pollSCM('*/2 * * * *')
  //  }
   
    stages {
        stage('git clone') {
            steps {
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/vagile-devsecops/vagile-webapp.git']])
            }
        }
        stage('maven build') {
            steps {
                bat 'mvn clean package'
            }
        }
        stage('deploy to tomcat') {
            steps {
                deploy adapters: [tomcat9(credentialsId: '492f4d40-e6b0-4d1d-ad9f-463532963288', path: '', url: 'http://localhost:8090/')], contextPath: null, war: '**/*.war'
            }
        }
       
    }
}
