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
                        -r cli,htmlextra,junit,json \
                        --reporter-htmlextra-export results/booking-report.html \
                        --reporter-junit-export results/booking-report.xml \
                        --reporter-json-export results/booking-report.json
                '''
            }
        }

        stage('Run UserAPI Tests') {
            steps {
                sh '''
                    newman run collections/UserAPI.postman_collection.json \
                        -r cli,htmlextra,junit,json \
                        --reporter-htmlextra-export results/userapi-report.html \
                        --reporter-junit-export results/userapi-report.xml \
                        --reporter-json-export results/userapi-report.json
                '''
            }
        }
    }

    post {
        always {
            junit allowEmptyResults: true, testResults: 'results/*.xml'
            archiveArtifacts artifacts: 'results/*', allowEmptyArchive: true
        }
        success {
            echo 'All tests passed!'
        }
        failure {
            echo 'One or more tests failed.'
        }
    }
}
