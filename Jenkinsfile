pipeline {
	agent any
	//agent { docker{ image 'node:latest' } }
	stages {
		stage('Build'){
			steps{
				//sh 'node --version'
				echo "Build"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "JOB_NAME - $env.JOB_NAME"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "BUILD_URL - $env.BUILD_URL"
			}
		}
		stage('Test'){
			steps{
				echo "Test"
			}
		}
		stage('Integration Test'){
			steps{
				echo "Integration Test"
			}
		}
	}
	post{
		always{
			echo "I always run because I am awesome"
		}
		success{
			echo "I run when you are successful"
		}
		failure{
			echo "I run when I you fail"
		}
	}
}
