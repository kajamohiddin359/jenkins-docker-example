pipeline{
	agent {
	label 'Jenkins_Master'
	}
	 tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "Maven_Home"
    }
	stages{
		stage('Maven Build'){
			steps{
				script{
				checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/kajamohiddin359/jenkins-docker-example.git']]])
					sh "mvn -Dmaven.test.failure.ignore=true clean package"
				}
			}
		}
		stage('Docker build image'){
			steps{
				script{
					sh 'docker build -t khaja359/my-app-1.0:2.0 .'
				}
			}
		}
		stage('Docker login'){
			steps{
				script{
					withCredentials([string(credentialsId: 'khaja359', variable: 'dockerHubId')]) {
						sh 'docker login -u khaja359 -p ${dockerHubId}'
					}
				}
			}
		}
		stage('Docker push'){
			steps{
				script{
					sh 'docker push khaja359/my-app-1.0:2.0'
				}
			}
		}
	}
	post{
		always{
			sh 'docker logout'
		}
	}
}