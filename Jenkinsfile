pipeline {
    agent any
    environment {
        DOCKER_IMAGE_NAME = "Mydcoker"
        DOCKER_IMAGE_TAG = "1"
        DOCKER_REGISTRY_URL = "https://index.docker.io/v1/"
        DOCKER_USERNAME = credentials('nayabshaik0587')
        DOCKER_PASSWORD = credentials('nayab@80994980')
    }
    stages {
        stage('Build Docker Image') {
            steps {
                sh "docker build -t ${DOCKER_IMAGE_NAME}:${DOCKER_IMAGE_TAG} ."
            }
        }
        stage('Push Docker Image to Docker Hub') {
            steps {
                sh "docker login -u ${DOCKER_USERNAME} -p ${DOCKER_PASSWORD}"
                sh "docker tag ${DOCKER_IMAGE_NAME}:${DOCKER_IMAGE_TAG} ${DOCKER_REGISTRY_URL}/${DOCKER_IMAGE_NAME}:${DOCKER_IMAGE_TAG}"
                sh "docker push ${DOCKER_REGISTRY_URL}/${DOCKER_IMAGE_NAME}:${DOCKER_IMAGE_TAG}"
            }
        }
    }
}
