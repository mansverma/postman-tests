pipeline {
    agent any

    stages {
        stage('Install Newman') {
            steps {
                sh 'npm install -g newman newman-reporter-htmlextra'
            }
        }

        stage('Run Booking Tests') {
            steps {
                sh '''
                    newman run collections/Booking.postman_collection.json \
                        -r cli,htmlextra \
                        --reporter-htmlextra-export results/booking-report.html
                '''
            }
        }

        stage('Run UserAPI Tests') {
            steps {
                sh '''
                    newman run collections/UserAPI.postman_collection.json \
                        -r cli,htmlextra \
                        --reporter-htmlextra-export results/userapi-report.html
                '''
            }
        }
    }

    post {
        always {
            archiveArtifacts artifacts: 'results/*.html', allowEmptyArchive: true
        }
        success {
            echo 'All tests passed!'
        }
        failure {
            echo 'One or more tests failed.'
        }
    }
}
