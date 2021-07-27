pipeline {
	//agent any
	agent { docker{ image 'node:latest' } }
	stages {
		stage('Build'){
			steps{
				//sh 'node --version'
				echo "Build"
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
