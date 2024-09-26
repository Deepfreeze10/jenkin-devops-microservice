//DECLARATIVE
pipeline {
	agent any
	stages {
		stage('Build') {
			steps {
				echo "Build"
			}
		}
		stage('Test') {
			steps {
				echo "Test"
			}
		}
		stage('IntegrationTest') {
			steps {
				echo "IntegrationTest"
			}
		}
	} 
	post {
		always {
			echo "Im awesome. I run always"
		}
		success {
			echo "I run when you are sucessful"
		}
		failure {
			echo "I run when you fail"
		}
	}
	
}
