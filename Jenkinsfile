pipeline{
    agent any
    
    stages{
        stage('Code'){
            steps{
                git url: 'https://github.com/akhilvijay15/-react_django_demo_app.git', branch: 'master' 
            }
        }
        stage('Build'){
            steps{
                sh 'docker build . -t akhilvijay15/django_app:latest'
            }
            
        }
        stage('Push'){
            steps{
                 withCredentials([usernamePassword(credentialsId: 'dockerHub', usernameVariable: 'dockerHubUser', passwordVariable: 'dockerHubPassword')]) {
          
          sh "docker login -u ${env.dockerHUbuser} -p ${env.dockerHubpassword}"
          sh 'docker push akhilvijay15/django_app:latest'
          }
            }
            
        }
        stage('Deploy'){
            steps{
                sh "docker-compose down && docker-compose up -d"
            }
            
        }
    }
}





