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
        stage('Login Docker Registry') {
            steps {
		sh 'echo 123456aA@ | docker login -u npower1109l --password-stdin'
	    }
        }
        stage('Push Docker Image') {
            steps {
		sh 'docker push npower1109l/nodeapp_test:latest'
	    }
        }
    }
}
