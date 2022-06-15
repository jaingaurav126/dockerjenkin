pipeline{
    agent{label 'linux'}
    options{
        buildDiscarder(logRotator(numToKeepStr:'5'))
    }

    environment{
        DOCKERHUB_CREDENTIALS=credentials('dockerhub')
    }

    stages{
        stage('Build')
        {
            steps{
                sh 'docker build -t jaingaurav126/node-web-app:latest .'
            }
        }
        stage('Login')
        {
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }

        stage('Push')
        {
            steps{
                sh 'docker push jaingaurav126/node-web-app:latest'
                }

        }

    

    post{
        always{
            sh 'docker logout'
        }
    }

    }




node {

    checkout scm

    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {

        def customImage = docker.build("jaingaurav126/node-web-app")

        /* Push the container to the custom Registry */
        customImage.push()
    }
}
