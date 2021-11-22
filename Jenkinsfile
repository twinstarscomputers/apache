pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhub-cred-madhan')
		key = 'value'
		
	}

	stages {

		stage('Build') {

			steps {
				sh 'docker build -t sm0961/alpha:$value .'
			}
		}

		stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		}

		stage('Push') {

			steps {
				sh 'docker push sm0961/alpha:$value'
			}
		}
	}

	post {
		always {
			sh 'docker logout'
		}
	}

}
