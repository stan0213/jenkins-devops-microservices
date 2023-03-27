// DECLARATIVE
pipeline {
	// agent { docker { image 'maven:3.9.0' } }
	agent any
	stages {
		stage('Build') {
			steps {
				//sh 'mvn --version'
				echo "Build"
				echo "Build number - $env.BUILD_NUMBER"
				echo "Job name - $env.JOB_NAME"
				echo "Build ID - $env.BUILD_ID"
				echo "Build TAG - $env.BUILD_TAG"
				echo "Build URL - $env.BUILD_URL"
			}
		}
		stage('Test') {
			steps {
				echo "Test"
			}
		}
		stage('Integration Test') {
			steps {
				echo "Integration Test"
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