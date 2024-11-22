// node {
// 	stage('Build') {
// 		echo "Build"
// 	}
// 	stage('Test') {
// 		echo "Test"
// 	}
// 	stage('Integration Test') {
// 		echo "Integration Test"
// 	}
// }

pipeline {
	// agent any
	agent { docker { image "maven:3.6.3" } }
	stages {
		stage('Build') {
			steps {
				sh 'mvn --version'
				echo "Build"
			}
		}
		stage('Test') {
			steps {
				sh 'mvn --version'
				echo "Test"
			}
		}
		stage('Integration Test') {
			steps {
				sh 'mvn --version'
				echo "Integration Test"
			}
		}
	} 
	post {
		always {
			echo "Runs always"
		}
		success {
			echo "Runs when successful"
		}
		failure {
			echo "Runs on failure"
		}
	}
}
