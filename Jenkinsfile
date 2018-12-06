node {
    def app
    stage('Clone repository'){
        checkout scm
    }

    stage('Build image'){
        app = docker.build("deorenik/node-todo-app")

    }

    stage('Push Image Dockerhub'){
        docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }
    }

    stage('Push Image AWS ECR'){
        docker.withRegistry('https://135612535889.dkr.ecr.us-east-1.amazonaws.com/deorenik/node-todo-app', 'ecr:us-east-1:docker-ecr-credentials') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
        }
    }




}
