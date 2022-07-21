pipeline {
  agent { label 'tomcat-slave5' }
	 
	 stages {
	      stage ('git checkout') {
		       steps {
			       git branch: 'main', url: 'https://github.com/pavanabangera/spark.git' 
				}
			}	
			stage ('build stage') {
			    steps {
				     sh 'mvn clean install'
				}
			}
			stage('SonarQube analysis') {
			steps{
			withSonarQubeEnv('sonarqube-8.9.2') {
			sh "mvn sonar:sonar"
			}
			}
			}
			
			
			stage ('push to artifactory') {
			    steps {
				     sleep 15
				}
			}
			stage ('deploy') {
			    steps {
				     sh 'sudo cp /home/ec2-user/JENKINS1/workspace/jenkinfile/target/*.war /home/ec2-user/apache-tomcat-8.5.81/webapps'
				}
			}
			}
		}
