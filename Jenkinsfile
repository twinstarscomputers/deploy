pipeline{

	agent any

	environment {
		DOCKERHUB_CREDENTIALS=credentials('dockerhub-cred-madhan')
		key = 'BUILD_VERSION'
		
	}
	stages {
	         
		 stage('Login') {

			steps {
				sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
			}
		 }
		
	

		  stage('Deploy') {

			steps {
				sh 'docker run -d --name apache_deploy -p 8082:80 sm0961/alpha:v1'
			}
		 }
      
	}
	

	post {
		always {
			sh 'docker logout'
		}
	}
}
