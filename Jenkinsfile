pipeline{
	agent {
	label 'Jenkins_Master'
	}
	stages{
		stage('SCM Checkout'){
			steps{
				script{
				
				}
			}
		}
		stage('Maven Build'){
			steps{
				script{
					sh 'mvn clean package'
				}
			}
		}
		stage('Docker build image'){
			steps{
				script{
					sh 'docker build -t khaja359/my-app-1.0:1.0 .'
				}
			}
		}
		stage('Docker login'){
			steps{
				script{
					
				}
			}
		}
		stage('Docker push'){
			steps{
				script{
					sh 'docker push khaja359/my-app-1.0:1.0'
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