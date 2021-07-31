pipeline {
	agent any
	//agent { docker{ image 'node:latest' } }
	
	environment{
		dockerHome = tool 'myDocker'
		mavenHome = tool 'myMaven'
		PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
	}
	
	stages {
		stage('Checkout'){
			steps{
				sh 'mvn --version'
				sh 'docker version'
				echo "Build"
				echo "BUILD_ID - $env.BUILD_ID"
				echo "BUILD_NUMBER - $env.BUILD_NUMBER"
				echo "JOB_NAME - $env.JOB_NAME"
				echo "BUILD_TAG - $env.BUILD_TAG"
				echo "BUILD_URL - $env.BUILD_URL"
			}
		}
		stage('Compile'){
			steps{
				sh "mvn clean compile"
			}
		}
		stage('Test'){
			steps{
				//echo "Test"
				sh "mvn test"
			}
		}
		stage('Integration Test'){
			steps{
				//echo "Integration Test"
				sh "mvn failsafe:integration-test failsafe:verify"
			}
		}
		stage('Package'){
			steps{
				sh "mvn package -DskipTests"
			}
		}
		stage('Build Docker Image'){
			steps{
				script{
					//docker build -t lakshay/mangu/currency-exchange-devops:$env.BUILD_TAG
					dockerImage=docker.build("lakshaymangu/currency-exchange-devops:${env.BUILD_TAG}")
				}
			}
		}
		stage('Push Docker Image'){
			steps{
				script{
					dockerImage.push()
				dockerImage.push('latest')
				}
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
