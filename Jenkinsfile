// scripted pipeline (old syntax)
/*node {
	echo "Build"
	echo "Test"
	echo "Integration Test"
} */

// Declarative pipeline (new syntax)
pipeline {
	agent { 
 		docker {
			 image 'node:14.11'
		 }
	}
		
	stages {
		stage('Build') {
			steps {
				sh "node --version"
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