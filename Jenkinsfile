pipeline {
    agent any
    
   // tools {
   //     maven 'M2_HOME'
   // }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            //checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/devopscbabu/DevOpsAddressBook.git']]])
            }
        }
        stage('Compile') {
            steps {
            sh 'mvn clean compile'
            }
        }  
        stage('Test') {
            steps {
            sh 'mvn test'
            }
        }
        stage('Package') {
            steps {
            sh 'mvn clean package'
            }
        }   
        stage('Deployment') {
	       steps {
           sh 'sshpass -p tomcat scp target/addressbook.war tomcat@172.31.95.241:/opt/tomcat/webapps'
	}
    }
    }
}
