pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Running build automation'
                sh './gradlew build --no-daemon'
                archiveArtifacts artifacts: 'dist/trainSchedule.zip'
            }
        }
        stage('Build Docker Image') {
            steps {
               sh 'docker build -t npower1109l/nodeapp_test:latest .'
            }
        }

        stage('Push Docker Image') {
            steps {
		sh 'docker login --username=docker_hub_user --password=docker_hub_password && docker push npower1109l/nodeapp_test'
	    }
        }
    }
}
