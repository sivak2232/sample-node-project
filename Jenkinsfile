pipeline {
    agent any

    stages {
        stage('Preparation') {
            steps {
                echo 'Cloning the code from GitHub'
				sh'''
				
				git clone https://github.com/sivak2232/sample-node-project.git
				'''
            }
        }
		
		stage('Docker Build') {
            steps {
                echo 'Building the Docker Image'
				sh'''
				
				cd sample-node-project
				sudo docker build -t siva2232/nodeproject:latest .
				sudo docker images
				
				'''
            }
        }
		
		stage('Docker Deployment') {
            steps {
                echo 'docker run '
                sh '''
                sudo docker push siva2232/nodeproject:latest
                sudo docker run -d -p 8083:3005 --name sivanode siva2232/nodeproject:latest
                sudo docker ps
                '''
            }
        }
    }
}