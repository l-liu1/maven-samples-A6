pipeline {
    agent any
    tools { 
        maven 'maven'
        jdk 'JDK 21'
    }
    stages {
        stage('Checkout') {
            steps {
                git(url: 'https://github.com/l-liu1/maven-samples-A6.git', branch: 'master')
            }
        }

        stage('Git Bisect') {
            steps {
                script {
                    // Start Git Bisect
                    sh 'git bisect start 198644632661c67b6c32f59e9047c11a70685e15 98ac319c0cff47b4d39a1a7b61b4e195cfa231e5'

                    // Run Git Bisect with defined command
                    sh 'git bisect run mvn clean test'
                }
            }
        }
    }
    post {
        success {
            echo 'Git Bisect completed successfully!'
        }
        failure {
            echo 'Git Bisect failed!'
        }
    }
}
