pipeline {

    agent {
        docker { image 'public.ecr.aws/docker/libraty/maven:latest'}
    }

    stages{
        stage ('Source'){
            steps {
                sh 'mvn --version'
                sh 'git --version'
                git branch: 'release',
                    url: 'https://github.com/katrix001/docker_jenkins.git'
            }
        }
        stage ('Clean') {
            steps {
                dir("${env.WORKSPACE}/Ch04/04_03-docker-agent"){
                    sh 'mvn clean'
                }
            }
        }
        stage ('Test') {
            steps {
                dir ("${env.WORKSPACE}/Ch04/04_03-docker-agent") {
                    sh "mvn test"
                }
            }
        }
        stage ('Package') {
            steps {
                dir ("${env.WORKSPACE}/Ch04/04_03-docker-agent")
                sh 'mvn package -DskipTests'
            }
        }
    }
}