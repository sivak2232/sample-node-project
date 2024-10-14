pipeline {
    agent any

    stages {
        stage('Preparation') {
            steps {
                echo 'Cloning the code from GitHub'
				sh'''
				
				git clone https://github.com/sairammagham/sample-node-project.git
				'''
            }
        }
		
		stage('Docker Build') {
            steps {
                echo 'Building the Docker Image'
				sh'''
				
				cd sample-node-project
				sudo docker build -t rams3/nodejs:latest .
				sudo docker images
				
				'''
            }
        }
		
		stage('Docker Deployment') {
            steps {
                echo 'docker run '
                sh '''
                sudo docker push rams3/nodejs:latest
                sudo docker run -d -p 8083:3005 --name samplenode rams3/nodejs:latest
                sudo docker ps
                '''
            }
        }
    }
}