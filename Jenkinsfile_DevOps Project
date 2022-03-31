pipeline {
    agent any
    tools {
        maven 'mvn385'
    }
    stages{
        stage ('Get the source code') {
            steps {
                git branch: 'main', url: 'https://github.com/szeshiang/DevOps.git'
            }
        }
        stage ('Compile App') {
            steps {
                sh 'mvn compile'
            }
        }
        stage ('Code Scan') {
            steps {
                sh 'mvn -P metrics pmd:pmd'
            }
        }
        stage ('Unit  Test') {
            steps {
                sh 'mvn test'
            }
        }
        stage ('Package') {
            steps {
                sh 'mvn package'
            }
        }
        stage ('Archive Artifacts') {
            steps {
                archiveArtifacts artifacts: 'target/*.war', followSymlinks: false
            }
        }
    }
}
