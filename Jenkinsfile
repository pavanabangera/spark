pipeline {
agent {
  label 'tomcat-slave5'
}

stages {
       stage('checkout stage') {
       steps {
	   git branch: 'main', url: 'https://github.com/pavanabangera/spark.git'
         }
         }
		stage('build stage') {
       steps {
          sh 'mvn clean install'
         }
         }
		 stage('push stage') {
       steps {
        sh 'sleep 15'
         }
         }
		stage('deploy stage') {
       steps {
    sh 'sudo cp /home/ec2-user/JENKINS1/workspace/demojob/target/*.war /home/ec2-user/apache-tomcat-8.5.81/webapps'
         }
         } 
		 }
		 }
