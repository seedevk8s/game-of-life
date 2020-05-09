pipeline{
    tools{
        jdk 'mymaven'
        maven 'mymaven'
    }
    agent none
    stages{
        stage('Checkout'){
            agent any
            steps{
                git 'https://github.com/seedevk8s/game-of-life.git'
            }
        }
        stage('Compile'){
            agent any
            steps{
                sh 'mvn compile'
            }
        }
        stage('Test'){
            agent any
            steps{
                sh 'mvn test'
            }
            post{
                always{
                    junit 'gameoflife-web/target/surefire-reports/*.xml'
                }                
            }
        }
        stage('Package'){
            agent {label 'Linux_Slave'}
            steps{
                git 'https://github.com/seedevk8s/game-of-life.git'
                sh 'mvn package'
            }
        }
    }
}