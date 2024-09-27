//DECLARATIVE
pipeline {
	//agent any
	// agent { docker { image 'maven:3.6.3'}}
	// agent { docker { image 'node:13.8'}}
	agent {
        docker { image 'openjdk:8-jdk' }
    }

	environment {
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}

	stages {
		stage('Checkout') {
			steps {
				sh 'mvn --version'
				sh 'docker --version'
				echo "Build"
				echo "PATH - $PATH"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "$env.JOB_NAME"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "BUILD_URL - $env.BUILD_URL"
			}
		}
		stage('Compile'){
			steps {
				sh "mvn clean compile"
			}
		}
		stage('Test') {
			steps {
				sh "mvn test"
			}
		}
		stage('IntegrationTest') {
			steps {
				sh "mvn failsafe:integration-test"
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
