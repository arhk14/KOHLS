pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from your GitHub repository
                git url: 'https://github.com/arhk14/KOHLS.git', credentialsId: 'Git_Authentication'
            }
        }
        
        stage('Run JMeter') {
            steps {
                // Execute your JMeter script
                sh 'jmeter -n -t jmeter_api_sample.jmx -l results.jtl'
            }
        }
    }

    post {
        always {
            // Archive the JTL result file for later reference
            archiveArtifacts artifacts: 'results.jtl', onlyIfSuccessful: false
        }
    }
}
