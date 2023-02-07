pipeline{
    agent any
    tools {
        maven 'MAVEN_HOME'
        jdk 'JAVA_HOME'
    }
    environment{
        DOCKERHUB_CREDENTIALS=credentials('dockerjob')
    }
    stages{
        stage('checkout'){
            steps{
                git branch: 'main', url: 'https://github.com/rajeevsinghranjanmanu/HelloWorld-Springboot-App.git'
            }
        }
        stage('build package'){
            steps{
                sh 'mvn package'
            }
        }
        stage('build image'){
            steps{
                sh 'docker build -t rajeevtcsranjan/demopush .'
            }
        }
        stage('login'){
            steps{
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }
        stage('push'){
            steps{
                sh 'docker push rajeevtcsranjan/demopush:latest'
            }
        }
    }
}
