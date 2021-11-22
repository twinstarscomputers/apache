pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhub-cred-madhan')
		${packageType}
		
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t sm0961/alpha:${packageType} .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push sm0961/alpha:${packageType}'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
