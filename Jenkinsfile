pipeline{
    agent any
    stages{
        stage('checkout the code from github'){
            steps{
                 git url: 'https://github.com/Manojgit365/Java-Project'
                 echo 'github url checkout'
            }
        }
        stage('code-compile'){
            steps{
                echo 'starting compiling'
                sh 'mvn compile'
            }
        }
        stage('code-testing'){
            steps{
                sh 'mvn test'
            }
        }
        stage('qa-check'){
            steps{
                sh 'mvn checkstyle:checkstyle'
            }
        }
        stage('package'){
            steps{
                sh 'mvn package'
            }
        }
        stage('run dockerfile'){
          steps{
               sh 'docker build -t myimg .'
           }
         }
        stage('port expose'){
            steps{
                sh 'docker run -dt -p 8091:8091 --name c000 myimg'
            }
        }   
    }
}
