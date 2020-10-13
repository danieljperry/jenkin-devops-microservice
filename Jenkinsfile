// scripted pipeline (old syntax)
/*node {
	echo "Build"
	echo "Test"
	echo "Integration Test"
} */

// Declarative pipeline (new syntax)
pipeline {
    agent any

	//agent { 
 	//	docker {
	//		 image 'node:current'
			 //image 'maven:3.6.3'
	//	 }
	//}

	environment{
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
		
	stages {
		stage('Checkout') {
			steps {
				sh "mvn --version"
				sh "docker version"
				echo "Build"
				echo "PATH - $PATH"
				echo "BUIlD_NUMBER - $env.BUILD_NUMBER"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "JOB_NAME - $env.JOB_NAME"
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

		stage('Integration Test') {
			steps {
				sh "mvn failsafe:integration-test failsafe:verify"
			}
		}
	}
	post {
		always {
			echo "I always run."
		}
		success {
			echo "I run on successful builds"
		}
		failure{
			echo "I run on failed builds"
		}
		changed{
		    echo "I run when the status of the build changes."
		}
	}
}