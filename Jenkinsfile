pipeline {
    agent any 
    stages {
        stage('Build') { 
            steps {
                sh 'docker build –tag  test_image-bash  20_04.dockerfile .'
                sh './gsc build --insecure-args test_image-bash 20.04.manifest'
                sh 'openssl genrsa -3 -out enclave-key.pem 3072'
            }
        }
        stage('Test'){ 
            steps { 
                sh './gsc sign-image test_image-bash enclave-key.pem' 
            }
        }
        stage('Deploy') { 
            steps {
                // 
            }
        }
    }
}
