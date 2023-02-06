pipeline{
    agent any
    tools { 
      maven 'MAVEN_HOME' 
      jdk 'JAVA_HOME' 
    }
    stages{
        stage('Git Clone'){
            steps{
                git branch: 'main', url: 'https://github.com/rajeevsinghranjanmanu/HelloWorld-Springboot-App.git'
            }
        }
        stage('Maven Test'){
            steps{
                sh 'mvn test'
            }
        } 
        stage('Maven Build'){
            steps{
                sh 'mvn package'
            }
        }
        stage('Maven Deploy'){
            steps{
                echo "Deployng the WAR file to the server"
            }
        }
        stage('Create Dockerfile'){
            steps{
                sh 'docker build -t dockerfiledemo .'
            }
        }
    }
}
