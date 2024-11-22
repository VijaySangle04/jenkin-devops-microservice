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
	agent any
	// agent { docker { image "maven:3.6.3" } }
	environment {
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}

	stages {
		stage('Build') {
			steps {
				sh 'mvn --version'
				sh 'docker version'
				echo "Build"
				echo "PATH - $PATH"
				echo "BUILD_URL - $env.BUILD_URL"
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
