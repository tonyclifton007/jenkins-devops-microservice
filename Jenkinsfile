//declarative pipeline
pipeline {
		agent any
		//agent { docker { image 'maven:3.6.3'}}
		environment {
			dockerHome = tool 'myDocker'
			mavenHome = tool 'myMaven'
			PATH = "$dockerHome/bin:$mavenHome/bin:$PATH"
		}
		stages {
			stage ('Checkout')	{
				steps {
					sh 'mvn --version'
					sh 'docker version'
					echo "Build"
					echo "$PATH"
					echo "BUILD NUMBER - $env.BUILD_NUMBER"
					echo "BUILD ID - $env.BUILD_ID"
					echo "JOB NAME - $env.JOB_NAME"
					echo "BUILD TAG - $env.BUILD_TAG"
					echo "BUILD URL - $env.BUILD_URL"
				}
			}
			stage ('Compile') {
				steps {
					sh "mvn clean compile"

				}
			}
			stage ('Test')	{
				steps {
					sh "mvn test"
				}
			}
			stage ('Integration Test')	{
				steps {
					echo "mvn failsafe:integration-test failsafe:verify"
				}
			}
		}	
	}