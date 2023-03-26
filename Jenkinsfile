// DECLARATIVE
pipeline {
	agent { docker { image 'maven:3.9.0' } }
	stages {
		stage('Build') {
			steps {
				sh 'mvn --version'
				echo "Build"
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