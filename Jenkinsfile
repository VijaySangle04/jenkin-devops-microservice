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
		stage('Checkout') {
			steps {
				echo "Checkout"
				sh 'mvn --version'
				sh 'docker version'
				echo "PATH - $PATH"
				echo "BUILD_URL - $env.BUILD_URL"
			}
		}
		stage('Comple') {
			steps {
				echo "Comple"
				sh 'mvn clean compile'
			}
		}
		stage('Package') {
			steps {
				sh "mvn package -DskipTests"
			}
		}
		// stage('Test') {
		// 	steps {
		// 		echo "Test"
		// 		sh 'mvn test'
		// 	}
		// }
		// stage('Integration Test') {
		// 	steps {
		// 		echo "Integration Test"
		// 		sh 'mvn failsafe:integration-test failsafe:verify'
		// 	}
		// }
		stage('Build Docker Image') {
			steps {
				//"docker build -t sanglevijayuk/currency-exchange-devops:$env.BUILD_TAG"
				script {
					docker.build("sanglevijayuk/currency-exchange-devops:${env.BUILD_TAG}")
				}
			}
		}

		stage('Push Docker Image') {
			steps {
				script {
					docker.withRegistry('', 'dockerhub') {
						dockerImage.push();
						dockerImage.push('latest');
					}
				}
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
