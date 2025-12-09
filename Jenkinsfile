pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/dhruv26-ops/practice.git'
            }
        }

        stage('Build') {
            steps {
                sh 'echo "No build needed for static HTML"'
            }
        }

        stage('Test') {
            steps {
                sh 'echo "Testing HTML file exists..."'
                sh 'test -f index.html'
            }
        }

        stage('Deploy') {
    steps {
        sh '''
        docker run -d -p 9090:80 \
          -v $WORKSPACE:/usr/share/nginx/html:ro \
          nginx:alpine
        '''
    }
}

    post {
        success {
            echo "Pipeline finished successfully!"
        }
        failure {
            echo "Pipeline failed!"
        }
    }
}
