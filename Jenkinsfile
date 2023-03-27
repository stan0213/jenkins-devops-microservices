// DECLARATIVE
pipeline {
	// agent { docker { image 'maven:3.9.0' } }
	agent any
	environment {
		mavenHome = tool 'myMaven'
		dockerHome = tool 'myDocker'
		PATH = "$mavenHome/bin:$dockerHome/bin:$PATH"
	}
	
	stages {
		stage('Checkout') {
			steps {
				sh 'mvn --version'
				sh 'docker version'
				echo "Build"
				echo "Build number - $env.BUILD_NUMBER"
				echo "Job name - $env.JOB_NAME"
				echo "Build ID - $env.BUILD_ID"
				echo "Build TAG - $env.BUILD_TAG"
				echo "Build URL - $env.BUILD_URL"
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
		
		stage('Integration Test') {
			steps {
				sh "mvn failsafe:integration-test failsafe:verify"
			}
		}

		stage('Package') {
			steps {
				sh "mvn package -DskipTests"
			}
		}

		stage('Build Docker Image') {
			steps {
				script {
					dockerImage = docker.build("standockertest/currency-exchange-devops:${env.BUILD_TAG}")
				}
			}
		}

		stage('Push Docker Image') {
			steps {
				script {
					docker.withRegistry('', 'dockerHub')
					dockerImage.push();
					dockerImage.push('latest');
				}
			}
		}
	}
	
	post {
		always {
			echo "this action execute always"
		}
		success {
			echo "this action execute when OK"
		}
		failure {
			echo "this action execute when goes wrong :("
		}
	}
}